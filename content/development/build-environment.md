---
title:       "Build Environment"
author:      "Z98"
type:        book
date:        2011-11-12
changed:     2015-02-28
draft:       false
promote:     false
sticky:      false
url:         /development/build-environment
aliases:     [ node/21 ]

---

<p>The Project provides a package of customized compilers and tools to help quickly set up everything needed to build ReactOS called the ReactOS Build Environment (RosBE) for both <a href="http://sourceforge.net/projects/reactos/files/RosBE-Windows/i386/2.1.1/RosBE-2.1.1.exe/download">Windows</a> and <a href="http://sourceforge.net/projects/reactos/files/RosBE-Unix/2.1.1/RosBE-Unix-2.1.1.tar.bz2/download">Unix</a>. The BE includes:</p>
<ul>
	<li>CMake 2.8.12.1</li>
	<li>MinGW GCC 4.7.2</li>
	<li>ninja</li>
	<li>Command-line SVN Client 1.8.5</li>
</ul>
<p>Note that if one wishes to use Microsoft's toolchain either from the command line or Visual Studio, simply make sure the bin directory of RosBE is in the path.</p>
<h2>Build Procedure</h2>
<p>When building using the MinGW toolchain, one must have started the command prompt using the shortcut created by the build environment. This shortcut helps set up the necessary paths and environment variables to make sure all of the necessary compilers and tools are found. It is highly recommended that compilation be done in a separate directory from the source checkout. This keeps the checkout clean and makes it easier to blow away the compiled objects for a truly clean build. The following instructions all assume a separate build directory has been created and is the build environment terminal's current working directory. For the command line build, execute:</p>
<blockquote><code>pathtocheckout/configure</code></blockquote>
<p><em>NOTE: By default, ninja is used&nbsp;for generating the&nbsp;build files. If you want to use makefiles instead, just use the following command:</em></p>
<blockquote><em><code>pathtocheckout/configure Makefiles</code></em></blockquote>
<p>This creates several directories and files in the build directory, the two most important being the host-tools and reactos directories. Before ReactOS can be compiled, some helper tools need to be compiled first. To do this, enter the following commands to move into the host-tools directory and build.</p>
<blockquote><code>cd host-tools &amp;&amp; ninja</code></blockquote>
<p>Once the host tools have been compiled, move into the reactos directory next to the host-tools directory to build ReactOS.</p>
<blockquote><code>cd ../reactos &amp;&amp; ninja</code></blockquote>
<p>The final step is to build an image for installation or testing. The following are the different types of images currently available.</p>
<ul>
	<li>bootcd: An image that can be used to install ReactOS onto a computer, real or virtual.</li>
	<li>bootcdregtest: An unattended installation image that automatically runs through a series of regression tests.</li>
	<li>livecd: An image that can be run on a computer from the CD-ROM.</li>
</ul>
<p>For example, to build a bootcd, use the following command.</p>
<blockquote><code>ninja bootcd</code></blockquote>
<p>Note that this command can be issued even before ReactOS has been built. If the object files have not been generated yet, the build system will simply start a build from scratch before building the image.</p>
<p><em>NOTE: When using makefiles, use <font face="Courier New">make</font> (or <font face="Courier New">makex</font>) instead of <font face="Courier New">ninja</font>.</em></p>
<p>&nbsp;</p>
<p>On Windows systems, it is also possible to build ReactOS using Microsoft's toolchain. ReactOS currently supports using Visual Studio 2010 and 2012. One however needs to execute the configure script from the Visual Studio command prompt instead of the build environment tool prompt. The cmake version bundled with the ReactOS Build Environment must however be in the path somewhere. Generating the command line build is effectively the same as the above instructions. Generating a Visual Studio solution file requires a different argument to be passed to configure like so:</p>
<blockquote><code>pathtocheckout/configure VSSolution</code></blockquote>
<p>Two separate solutions are created, one for the host tools and the other for ReactOS proper. Once again, the host tools must be built first before attempting to build ReactOS. Please note however that while the Visual Studio build boots, it is not entirely working yet.</p>

