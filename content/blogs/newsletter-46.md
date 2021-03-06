---
title:       "Newsletter 46"
author:      "Z98"
date:        2008-08-20
aliases:     [ "newsletter-46", "node/186" ]
---

<h2>Shellfolder Extensions</h2>
<p>
All of the special folders such as control panel, printer folder, and administrative tools are actually shellfolder extensions that the Explorer shell implements using IShellFolder.  Johannes Anderwald has been implementing those still missing in ReactOS as well as extending and fixing others.  Two new ones are the Font folder and the Administrative Tools folder.  Johannes also implemented the dialog for formating drives, but this obviously isn&#39;t functional.
</p>
<p>
The Recycle Bin was also fixed with help from Herv&eacute; Poussineau, as previously several issues in Trash_CanTrashFile prevented files from being moved there.  This effectively meant files were deleted directly if one confirmed a deletion request.  This has now been fixed, along with restoring of files and deletion of individual items.  The Printer folder also had some issues, including not showing up and randomly allocating memory.  EnumPrinter has also been partially implemented, but since the printer subsystem itself is not ready a complete fix will need to wait.
</p>
<p>
There still remains a lot of work to do, including fixing up the context menus.  Johannes&#39; job is complicated by the fact that Microsoft did not properly implement all the context menu extensions, instead hardcoding some of them to prevent the user from deleting them.  This is creating something of a mess as he tries to implement all of them in a standard fashion.  His current solution is to rewrite the context menu handling and he is making good progress.
</p>
<h2>Bugfixing</h2>
<p>
One of the nastier bugs hidding in ReactOS code was the system crashing when worker threads were terminated.  Worker threads are kernel mode threads that do something on behalf of device drivers.  A general purpose pool of worker threads exists, maintained by the NT Executive, or drivers could create their group for specific needs.  This issue was encountered by Cameron Gutman while he was testing ReactOS uptime.  After several hours when the dynamic worker threads tried to terminate, the system crashed.
</p>
<p>
The cause of the crash was an improperly written check in PspExitThread, which was supposed to only crash if stack swapping was disabled.  The check was reversed so would cause problems when stack swapping is enabled.  Ironically, another issue existed in KeInitThread, in which the flag enabling stack swapping was set to false when it should have been true, one reason the bug was hidden for so long.  Both issues have been fixed by Stefan Ginsberg and should result in the system being able to stay up longer.  Whether these changes expose even more hacks, only time will tell.
</p>
<h2>ReactOS Compiling</h2>
<p>
There is a &#39;magic&#39; flag in GCC, -enable-stdcall-fixup, that is used when compiling ReactOS.  What it does is in situations where functions that are aliases of others don&#39;t match the number of parameters, this permits them.  This is obviously bad coding practice and just asking for trouble.  Herv&eacute; Poussineau has been slowly fixing the function exports so we can eventually stop using that flag.  This obviously caused a few breakages, but all things considered Herv&eacute; has one of the best track records for fixing breakages, those caused by himself and others.  As far as he can tell, he believes he&#39;s fixed all of these mismatches.
</p>
<p>
Besides fixing exports, Herv&eacute; has been working on another issue involving compiling ReactOS components.  Compiling DLLs is a bit more complex than your regular executable program.  DLLs are basically just a collection of functions for use by other applications.  You of course need to specify which functions you want available for use and which should not be made public.  There are two approaches you can choose, using the export keyword before the function in question or using a .def file to list the functions you want exported.  If you use the .def approach, then at least in GCC, you send dlltool the .def file and the name of the DLL in question.  This will create a .a file that lists functions callable outside the DLL.  The .a file is used whenever you&#39;re writing a program that uses the DLL.  LD will obviously complain since it can&#39;t find the functions in question, but if you link using the .a file with the generated object files, it will proceed.
</p>
<p>
The .def file mentioned above is different for GCC and MSVC.  Because of this, if we attempted to compile a DLL on MSVC with our current .def, it would fail.  To get around this, Herv&eacute; has been converting all of our .def files to .spec files.  He intends to improve Winebuild, a program that converts .spec files to the GCC .def files, so that it will also be able to generate MSVC .def files.  Once this is done, another hurdle to compiling on Microsoft&#39;s compiler will be eliminated.  For those curious about how MSVC creates DLLs, the only difference is it creates .lib files instead of .a files and the two are functionally identical.  Mingw can create both .lib and .a files.
</p>
<h2>Filesystems</h2>
<p>
It&#39;s been mentioned before that the issues with the Common Cache prevent us from running any filesystem more advanced than FAT.  To be fair, even the FAT driver has been hacked to get around the problems in Cc.  However, filesystem drivers need more than the Cc to function properly.  There is also the FsRtl, or the Filesystem Runtime Library.  With the FsRtl also unimplemented, the filesystem drivers ReactOS currently uses were all written not to use it, which makes things much more complicated as FS drivers are supposed to use that API.  While simplistic filesystems can just barely get away with not using it, the features FsRtl provides are essential to implementing ext2/3/4 and NTFS.
</p>
<p>
While Art Yerkes and Aleksey Bragin have been working on the Cc side of things, Pierre Schweitzer has a branch set up for implementing FsRtl and testing the imported ext2 driver by Matt Wu.  One feature of FsRtl that Pierre is currently focusing on is directory change notification, whose lack is currently causing self-refreshing problems with the desktop.  However, FsRtl is probably one of the least researched APIs in NT and even with the documentation from the filesystem development kit there are a lot of black holes.  Currently Pierre is mostly doing research, trying to see what happens when the functions are called in various circumstances.  This research technique is generally called blackboxing and is one used by several ReactOS developers.
</p>
<p>
While a few functions have been implemented, Pierre expects this work to take a while before any visible progress.
</p>

