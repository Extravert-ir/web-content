---
title:       "January 2017 meeting minutes"
author:      "EmuandCo"
date:        2017-05-24
aliases:     [ "node/42024" ]
---

<p>2017-01-26<br />
	20:00 UTC<br />
	#reactos-meeting</p>
<h2>Proceedings</h2>
<p>Meeting started at 20:16 by Colin Finck</p>
<ul>
    <li>Point 1: FOSDEM participation</li>
    <li>Point 2: Status of scholarships</li>
    <li>Point 3: GSoC USB branch merging</li>
    <li>Point 3: Vadim's USB stack</li>
</ul>

<h2>Point 1: FOSDEM participation</h2>

<p>Colin Finck started this topic giving recent information about FOSDEM participation and who will be there right now. He criticised the current planning a bit because noone knew if someone will be at the FOSDEM booth or not until very recently. This should not happen again. We are at the more prominent K Building again (instead of the hidden "Alternative OS Ghetto")</p>
<p>The discussion mixed up a bit with the booth at CLT2017 in Chemnitz, too. There we have a small problem due to limited space, but Matthias Kupfer being one of the supporters there tried his best to make it possible to join there again. After that discussion went to what apps to show and which eye candy would work best to impress the audience. Some .net apps and Steam were put on top of the list.</p>

<h2>Point 2: Status of scholarships</h2>

<p><b>Giannis Adamopoulos:</b> He started trying to understand how sxs works in windows and what works and what doesn't in ros. So far he has only writen some tests for the core features of sxs. Unfortunately many things don't work. His plan going forward is to also write tests about the hhh^ special way comctl32 replaces the built in implementation of user32. this is also not done very well in ros. The first real result we will see is all controls being themed and not just a few.</p>

<p><b>Hermes Belusca Maito:</b> Up to the first week of January he was playing with Word 2010 installation, the current blocker of which is some NTLM authentication support needed to continue & finish the installation. (This is needed for some licensing stuff that seems to really be needed by the installer, otherwise, the installation seems to finish, but you are granted when you try to start Word by the installation restarting for finishing to install the licenses). He played with encoded's NTLM implementation, which seems to work at first sight, but then he gets strange problems in RPC calls (the installer uses also the NTLM to connect to some RPC port to communicate with the so-called "Office Service Protection" service, see the last blog for details). To refresh his ideas before digging into that problem (that would be, review quickly the ntlm code of encoded + playing with rpc internals) by having* a look at the PPT viewer 2010 (which should otherwise use the same codebase as the non-viewer stuff; primarily for GUI graphics calls) [19:51] and other office viewers. He checked what we got from the debug logs, found two main stuff that could be interesting to implement:</p>
<p>1. NtUserExcludeUpdateRgn (https://jira.reactos.org/browse/CORE-12649) Actually James had a patch for it, so he lets him work on it (and he'll come back to this issue after the fosdem)</p>
<p>2. Implementing some "win32_find_file_data" fixme message that popped out from time to time (this was something inside shell32!CShellLink class). He started to divert himself with the CShellLink class during the last 2 weeks (see https://jira.reactos.org/browse/CORE-12682)</p>
<p>Here Alexander Rechitskiy asked if we can't just port that thing from Wine that allows to have NTLM to work. Office 2010 works in Wine. They have working implementation. (This is the workaround we have running currently). (http://reactos.org/blogs/word-2010-support-weekly-report-part4-update-authentication-failed) Hermes thinks this is possible if you have SAMBA installed on ROS. Due to FOSDEM coming closer things stopped for now to prepare ISO files and CDs and some freeldr bugfixing aswell. Colin asked if some of his printing stack needs fixing, too, especially EnumPrinters. Word 2010 as others, too tend to pop open a printing dialog on startup and then theres nothing more you can do. RPC calls need a bit more work, too which Colin started already for his printing support branch. Still there are some Error Code 0xc004f012 aka "Windows not Activated" left.</p>

<h2>Point 3: GSoC USB branch merging</h2>

<p>Most code from GSoC 2016 still lies in branches and is not merged back. Alexander Rechitskiy and Aleksey Bragin think that a successful GSoC means all has to merged back and that this has to be top priority now. Amine Khaldi added that a merge needs careful review and some work to make it run in ROS and thus he recommends the typical MODULENAME_new tactics to make things not bitrot and easier to integrate.</p>
<p>The lwip driver in it's state doesn't work on ROS yet.</p>
<p>The USB work afaik doesn't revolutionize current USB support, but is needed later for sure.</p>
<p>The AHCI work doesn't work on ROS (it's built for Windows) and needs some work to really work on ROS.</p>
<p>He doesn't have enough data on the NTFS work, although he imagines it's ready for inclusion after a review, too.</p>

<h2>Point 3: Vadim's USB stack</h2>

<p>First question by several participants was regarding vgal's work on USB and if it's based on GSoC 2016 results or not and if it could be merged to FOSDEM CD. The first one was answered by Amine explaining that both are handling completely different modules of the USB stack and thus theres no work based on anything from each other. (usbport, usbhub, usbehci, usbohci and usbuhci are Vadim's work / hidparse, hidparser, libusb and usbhub are GSoC code) Anyone interested can check out the code from: https://github.com/vgalnt/reactos/commits/usbport Right now some devs are participating a test of the components under a Windows 2003 environment finding bugs and reporting them. These are Amine Khaldi, Mark Jansen and Daniel Reimer. Tests happen one module at a time and the improvements are astonishing. We are at a state where you tend to forget if you replaced the Windows files or not. This was the main reason why Hermes asked for integration to FOSDEM CD was the fact that things look nicer and nicer there. AMine took over here and explained some recent happenings. In the past he tried to get in contact to Vadim, because his work he showed up from time to time was looking very promising. Now he is contracted as 3rd developer in stipendium basis. His work Log can be seen here: https://docs.google.com/spreadsheets/d/1rz5ozdIZxd8ZJBA0ImejAJI4t5B4d5uuI9bgwGVyrkw/edit#gid=3 After USB Amine plans to lead him to something else we need badly. Problems are a language barrier (which is no real problem with all those Russians in the project) and his internet connection in Siberia being very bad. Last one is under investigation if we can improve it somehow. What is needed now is code review, testing and logs, because when he gets verbose logs, he identifies and fixes problems. Many participants agreed and want to try the USB stack on real hardware they have lying around to provide logs. What shall not happen is that all the work stays in a branch and everyone forgets about it. SO a plan for a merge will be the next goal here.</p>

<p>Meeting was closed at 22:11 by Colin Finck</p>
<p>Meeting minutes prepared by Daniel Reimer</p>
