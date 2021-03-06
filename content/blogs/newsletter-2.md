---
title:       "Newsletter 2"
author:      "TwoTailedFox"
date:        2005-10-23
aliases:     [ "newsletter-2", "node/142" ]
---

<p>Well, would you look at that. Another Sunday. another Newsletter. And Boy has this week been interesting.</p>

<h2>The ReactOS Constitution</h2>

<p>Found <a href="http://www.reactos.org/wiki/index.php/Constitution">here</a>, the new ReactOS Constitution is designed to clarify many of the things we all took for granted, such as who can do what on the project, and to elaborate on how Voting Prodecures should be followed. In addition, it also lays out the responsibilities of all the members of the Board of Directors of the ReactOS Foundation.</p>

<p>It's an interesting read, and I highly recommend it.</p>

<h2>0.2.8 Update</h2>

<p>0.2.8 has been slowly fermenting, and it due for a Monday Release (Day after this newsletter, I'll update it when the new Version's ISO's and whatnot are officially released. WinMine, and other games have been added to 0.2.8, in preparation for release, with several bugfixes making their way back to the 0.2.8 branch.</p>

<h2>VMWare Images</h2>

<p>Many of you who keep up with the latest news at <a href="http://www.vmware.com">VMWare</a>, will know about the 

new VMWare Player. Put Simply, it allows the user to use Images already made by another user. Think of how VMWare is 

right now, and remove the ability to create new Virtual Machines, and you come close to what is freely offered. My 

advice it to watch this space.</p>

<h2>Eye on SVN</h2>

<p>The following are now implemented:</p>

<ul>
<li>GetCaps for HAL - Not working until GdiEntry2 is Implemented in ddraw.dll and IDirectDraw</li>
<li>GetMenuBarInfo - Beginnings of</li>
<li>SetupDiGetDriverInfoDetailA</li>
<li>SetupDiGetDriverInfoDetailW</li>
<li>SetupDiGetDeviceInstallParamsW</li>
<li>SetupDiSetDeviceInstallParamsW</li>
<li>SetupDiGetInfClassA</li>
<li>SetupDiSetDeviceRegistryPropertyW - Untested</li>
<li>MakeAbsoluteSD2 by forwarding to RtlSelfRelativeToAbsoluteSD2</li>
</ul>

<p>New Changes:</p>

<ul>
<li>Improved PSDK, and MSVC Compiling on v6, .NET, 2003 and 2005</li>
<li>Moved DHCP and tcpsvcs to Services</li>
<li>Add support for Control Panel Applets (*.cpl)</li>
<li>Added msconfig</li>
</ul>

<p>Changes to Mouse and Keyboard System:</p>

<ul>
<li>Enable/disable keyboard by writing the controller command byte instead of issuing keyboard commands, the 

keyboard commands seem to confuse some kvm switches.</li>
<li>Use STATUS_IO_TIMEOUT consistently, STATUS_TIMEOUT is not an error condition</li>
<li>Introduce symbolic constants for controller command byte bits</li>
<li>Try to detect mouse early and if its not present, reset the keyboard controller. Some controllers seem to get locked up when writing to a non-present mouse.</li>
<li>Don't check the timeout status bit when reading from the controller. It is often wrong.</li>
<li>Don't treat failure to read keyboard id as a fatal error, we only read it to set KeyboardIsAT, which we then don't use. Still try to detect the keyboard type, but don't fail if it doesn't work.

</li>
</ul>

<p>New Drivers Added:</p>

<ul>
<li>System timer</li>
<li>DMA controller</li>
<li>System speaker</li>
<li>Generic ACPI bus</li>
<li>AT real-time clock</li>
<li>Motherboard resources</li>
<li>EISA programmable interrupt controller</li>
<li>ACPI Fixed Feature Button</li>
<li>Intel 82443BX Pentium(R) II CPU to PCI-Bridge</li>
<li>Intel 82371AB/EB Power Management Controller</li>
<li>Intel 82371AB/EB PCI to ISA Bridge</li>
<li>IDE Controller and Miniport</li>
</ul>

<p>Also:</p>

<ul>
<li>Add Display Class Installer</li>
<li>Allow search of .inf files outside of ReactOSInf directory</li>
<li>Added keyboard.inf
 and added LPT Port to ports.inf</li>
</ul>

<p>These changes are mostly to do with the new Plug-and-Play system in use on ReactOS. As such, we now have many of the common components with installable drivers. ReactOS can also now search for *.inf files outsie of the /Inf directory.</p>

<h2>Update on ROSCMS</h2>

<p>Like ReactOS, the new Content Management System is going to undergo a few changes, mostly internal. We're moving the Newsletters, from 'Static', to 'Dynamic' Pages, much like the  News and Blogs use currently. This also has the nifty side-effect of allowing us to organise our Editions a little easier than before. Code for an XML Backend is in the works, to bring us in closer alignment with the <a href="http://www.winehq.com">WINE</a> Website's way of organising it's own 'WINE Weekly News'.</p>


<h2>Conclusion</h2>
<p>Well, that's all for this week... by all means, let me know what else you want covered. I can be reached at TwoTailedFox (at) Gmail (dot) com. Until then, Happy Compiling!</p>

<p>Stuart Robbins</p>
<p>ReactOS Weekly Newsletter Editor</p>
