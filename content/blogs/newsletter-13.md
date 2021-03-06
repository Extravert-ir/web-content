---
title:       "Newsletter 13"
author:      "danceMonkey()"
date:        2006-12-13
aliases:     [ "newsletter-13", "node/153" ]
---

<h2>I'm the new guy(s)</h2>
<p>Yup, that's right, we're the new newsletter writers (those two words should never be used in combination - I promise never to do it again). We fought off a crowd of people breaking their necks to apply, and finally, we're here. So. Who are we? I am Dana Burkart, I will do most of the writing, and my associate - Samuel Serapion - will be providing most of the information. I just want to say that I vow never to turn this newsletter into a carnival. Shall we get on with it? </p>
<h2>A whole lotta change</h2>
<p>It has been a long time since ReactOS has had a writer for the Newsletter. As such, there are a lot of things that need to be covered, and, conversely, many things that must be passed over. Therefore, Samuel Serapion and I have planned to make this a big first newsletter. We are trying to cover most of the changes to the trunk since v0.3 of ReactOS, with a little recap on recent changes and what various developers are working on. We are trying to make this as comprehensible as possible, so it can be useful and informational to the casual ReactOS user. Let it be noted that most newsletters won't be this long; we're just trying to make up for missed ground.</p>
<h2>Recent News</h2>
<ul><li>A new release process has been proposed, and will likely be accepted. The idea: ReactOS will release on a strict and regular schedule. This will have some advantages and disadvantages:
<ul><li>For the casual user who doesn't build ReactOS themselves, this will provide a more up-to-date and realistic view of the project. </li>
<li>In the long run, this will increase ReactOS's popularity, as people will see this is a far-from-dead project. </li>
<li>More developers will be attracted to ReactOS because of how active it is. </li>
<li>In the near future, release quality may suffer. </li>
</ul></li>
<li>You can now build ReactOS on Vista; RosBE has been updated to allow this. </li>
<li>The license page has been omitted from the installer, as some people were offended by it. </li>
<li>Heavy work on kernel I/O (Input/Output) by Alex Ionescu. </li>
<li>Imagesoft is to be developed outside the ReactOS tree. </li>
<li>There is a new branch by arty, with some experimental work on kernel memory management and the cache manager. </li>
<li>Booting on Intel Macs and Parallels VM is partially working. </li>
</ul><h2>Highlight of work since ReactOS 0.3</h2>
<p>(no particular order)</p>
<ul><li>New NDK (Native Development Kit) with versioned headers, by Alex Ionescu </li>
<li>Win32k compatibility project by jimtabor, which is an effort to implement a more compatible GDI interface. </li>
<li>ddraw.dll, a compatible interface for DirectX acceleration, has been being worked on by Magnus Olsen. </li>
<li>Kernel loading with NT bootloader has been worked on. </li>
<li>Freeloader loading windows work has been done. </li>
<li>Windows 2003 thread scheduler by Alex Ionescu. </li>
<li>Partial HAL (Hardware Application Layer) rewrite. </li>
<li>Clipboard implementation (Summer of Code), still unmerged to trunk. </li>
<li>Wingina logon by hpousin, which is the beginning of User Profiles for ReactOS. </li>
<li>NT4 open source USB driver, imported by Aleksey Bragin </li>
<li>bootvid.sys rewrite by Filip Navara. </li>
<li>ReactOS builds with GCC 4.1.2 </li>
<li>Many different Wine synchs. </li>
<li>A device manager has been implemented by Ged Murphy. </li>
<li>Usermode Native and Win32 debugging functionality </li>
</ul><h2>Bug Fixes</h2>
<ul><li>Some networking bugs. </li>
<li>Kernel bugs. </li>
<li>Fixed some shell bugs. </li>
<li>Other bug fixes too numerous to name. </li>
</ul><h2>Developer Status</h2>
<ul><li>Aleksey Bragin is hard at work on winldr, a boot loader for NT 4, 2000, XP, and 2003. This is an effort to allow DualBooting of ReactOS and Windows without using third party booters, such as GRUB. </li>
<li>Christoph von Wittich is currently working on Code::Blocks back-end for Rbuild. </li>
<li>Magnus Olsen is working hard on Direct X. </li>
<li>Peter Ward has been working on RosBE (ReactOS Build Environment). </li>
<li>Timo Kreuzer is working on the ReactOS GDI (Graphics Device Interface). </li>
<li>DrFred is working on Recad, a common application downloader. </li>
<li>Andrew Greenwood is working on Kernel Streaming and the XP sound architecture for ReactOS. </li>
<li>Alex Ionescu is working on improved Kernel compatibility for drivers and many bugfixes. </li>
