---
title:       "Newsletter 96"
author:      "Z98"
date:        2013-05-16
aliases:     [ "newsletter-96", "node/643" ]
---

<h2>Testing and Debugging</h2>
<p>The hardest thing about writing software is finding the source of bugs. Good testers are as such extremely valuable, and those able to use debuggers well even more so. Two issues were recently dealt with thanks to one such tester, Olaf Siejka.</p>
<p>The first issue involved Microsoft Excel Viewer, an application that as its name suggests allows for viewing of spreadsheets but not editing. Word Viewer actually worked in ReactOS, and Excel Viewer&#39;s failure drew Olaf&#39;s attention. Using Ollydbg, which Olaf considers the most user friendly debugger he has ever used, he determined roughly where the error was and then compared the parameters, register values, and return values of the problematic functions. From here and with a little help from Giannis Adamopoulos and Thomas Faber, it was determined that a NULL handle was being passed in the process of drawing a bitmap. Excel Viewer detected this issue and failed appropriately, which in and of itself is a nice exception from simply plowing ahead and crashing. Olaf passed on his results to Thomas, who determined that ReactOS was not properly reporting support for several operations. Timo Kreuzer proceeded to fix the issue, querying the graphics device and properly reporting what &nbsp;operations were supported, thus allowing Excel Viewer to work.</p>
<p>The second issue was considerably more complex and actually revealed two problems, one fixed and the other still under investigation. The failures manifested in the OpenOffice installer failing, an issue that has been around for over two years. Olaf found the revision that introduced the regression, which was sufficiently old that he needed to do some juggling with different build environments. The guilty revision involved some work Pierre Schweitzer had done with the filesystem runtime library, but after reviewing the code, Pierre was unable to find anything obviously wrong. In addition, the existing tests did not show any regressions being introduced with Pierre&#39;s code. With some help from Giannis, Olaf eventually found that the installer was failing when trying to unpack files with the names f0_001 to f0_088. The installer itself was actually looking for these files using a wildcard pattern. Giannis managed to trace the call chain of functions from what the OpenOfficer installer was calling to down in FsRtl on Windows, helping provide a point of reference. This little effort actually required compiling and using an ext2 IFS so that he had debug symbols to peek into the bowels of the filesystem stack.</p>
<p>At the same time, Victor Martinez joined the effort and started creating test cases for FsRtl. Using these tests, Olaf tried various combinations of filename patterns and discovered that ReactOS consistently failed to find files that it should have when taking wildcard expansion into consideration. Olaf then started methodically comparing path strings being passed up and down the filesystem stack on Windows, first starting in user mode. For this, he used ApiMonitor, an application that is able to show parameters being passed into functions and return values in user mode.</p>
<p>The problem was eventually traced to the way wildcards were dealt with in both FsRtl and kernel32. Whereas FsRtl was having some issues with non-unicode paths, kernel32 was not properly expanding wildcards into non-unicode wildcards. The corrected versions now allowed the OpenOffice installer to find the files it needed to unpack, but another problem appeared. Since the first bug appeared, Aleksey Bragin had done a rewrite of the loader code, introducing another regression preventing the installer from completing. This issue is still under investigation, but fixing the FsRtl issue has resulted in a whole class of issues being squashed.</p>
<p>The effort described above involved fairly close cooperation between ReactOS&#39; testers and developers, with developers providing background knowledge and testers doing the digging to gather the raw data. It demonstrates quite nicely that ReactOS is not just a product of the developers, but also of the testers that invest the time and effort to find the source of bugs.</p>
<h2>Kernel Debugger</h2>
<p>To support development, the ReactOS project developed a kernel debugger for use in GCC builds of ReactOS for situations where something goes wrong in kernel mode. Microsoft has a similar system for Windows and they have built up a fairly extensive ecosystem of tools to make debugging easier. The debugging interfaces used in each are however incompatible. To take advantage of this ecosystem, Alex Ionescu had originally done some work to add support for using Microsoft&#39;s debuggers if ReactOS was built with MSVC. This was before the cmake transition so the work was only possible to utilize easily fairly recently. Hermès Bélusca-Maïto has picked up and continued this work to see if ReactOS&#39; original debugging interface could be rearchitectured to match that of Windows&#39;. While the functionality of both kernel debugging interfaces are broadly similar, they have some crucial incompatibilities. For example, ReactOS&#39; debugging interface only understands GCC debug symbols, not ones generated by Microsoft&#39;s compilers. ReactOS&#39; built in debugger also provides the ability to debug on the same machine as the OS is running on, which can be useful in certain situations. The ultimate goal is to not have different kernel debugging interfaces built based on whether one is using GCC and MSVC. Hermès does not yet know how much could be shared, but modifying ReactOS&#39; debugger interface to more closely match that of Windows&#39; is the first step.</p>
<h2>Theme Control</h2>
<p>Rudimentary theme support has been present for some time now, but its usability was hampered by the lack of tools to do easy configuration. One of those tools was the desktop control panel applet, whose appearance tab was fairly incomplete. One of the problems involved how desk.cpl read values from theme files, or rather, when it read them. Previously, desk.cpl could not read theme metrics from a theme that was not loaded, which meant to change things like color and size a user needed to first apply a theme before trying to change those values for their desired theme. Giannis has fixed desk.cpl to be able to read theme files to retrieve those values before the theme is activated, allowing users to tweak before hitting apply. This work involved a bit of investigation that discovered a few undocumented functions in the uxtheme library that helps facilitate this reading. Testing was done on Windows XP as more work will be needed in other modules before ReactOS can take advantage of Giannis&#39; improvements.</p>
<h2>Mono</h2>
<p>There is a very large body of applications on Windows written using the .NET framework, especially in the corporate world. Ultimately, support for that framework is going to be important from a strategic perspective.</p> <p>Sylvain Petreolle recently looked at installing Mono using the MSI package provided by Wine. The installer failed initially, leading him to incorrect behavior in ReactOS&#39; rundll32 application. The incorrectness of this behavior was slightly unexpected however, as what it boiled down to was Windows&#39; rundll32 will always return 0. Keeping in mind that rundll32 is used to execute functions inside of DLLs, it is liable to end up calling functions with a wide variety of return types. Returning 0 instead of trying to pass back the return value of the called function simplifies things considerably, especially since rundll32&#39;s exit code could then be used to indicate a major failure with rundll32 itself. Granted what exactly will trigger a nonzero return value is not immediately obvious, as tests on Windows 2003 revealed that even attempts to call functions in nonexistent DLLs would yield a 0 for the exit code. Sylvain has fixed the issue in ReactOS&#39; implementation and then proceeded to successfully test a Hello World .NET application using the installed Mono.</p>