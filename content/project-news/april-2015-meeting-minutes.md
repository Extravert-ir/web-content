---
title:       "April 2015 Meeting Minutes"
author:      "EmuandCo"
date:        2015-05-03
aliases:     [ "node/936" ]
---

<p>2015-04-30<br />
	19:00 UTC<br />
	dev.reactos.org, #meeting</p>
<h2>Proceedings</h2>
<p>Meeting started at 19:09 by Aleksey Bragin</p>
<ul>
    <li>Point 1: Developer Briefings</li>
    <li>Point 2: ReactOS Hackfest 2015</li>
</ul>

<h2>Point 1</h2>
<p><b>Aleksandar Andrejevic:</b> During the last month, Aleksandar has been fixing bugs in various parts of NTVDM, and is planning on fixing more bugs in the near future.</p>

<p><b>Amine Khaldi:</b> Amine was continuing the wine sync effort, while assisting and guiding some new comers that showed up recently, to make sure they contribute to the most urgent needs. He also performed the usual routine of reviewing and committing Jira patches, some spring cleanup and so on. He mentioned one wish for the next month. Some devs should work on dph and special pool revealed defects, along with testman failures.</p>

<p><b>Colin Finck:</b> Colin did some work on the website. Most notably, wrote some components which make it possible to develop own subsystems independently of Drupal. This is currently running on playground.reactos.org. It also included an upgrade of MediaWiki, but this version broke Drupal user integration. This still needs more research when he has time for the website again. This might take a while due to another ReactOS project: Colin's bachelor thesis on developing a printing stack has begun this week. Currently he is doing research on all components involved and digging into the call chains to see their dependencies. More will follow when he creates his branch. Also he told Amine to find somebody to write a proper NT5-style parallel port driver. (So if you wanna help here, contact Amine Khaldi!) This is out of scope of his thesis, but would be highly useful for it. Besides he talked to Jan that day and they want to bring back the Fezile server this weekend or the next one. He got in touch with a staff member of his university this week. He was very open towards supporting ReactOS through the university. Most notably, booking a seminar room for a Hackfest during the lecture-free time is no problem at all. So a Hackfest could be held in Aachen, Germany. First he will wait for the feedback from the doodle page. (http://doodle.com/tdaaie3rbbs5phpb) before continuing the planning.</p>

<p><b>David Quintana:</b> David finished some small fixes on the shellext, then focused mostly on his gamedev stuff, until last week. Last week he was given the task of the ReactOS CE application manager, and he started messing around with it</p>

<p><b>Hermes Belusca Maito:</b> He worked a bit on CMD and just recently on NTVDM, and will continue with that the next months.</p>

<p><b>Pierre Schweitzer:</b> Pierre is writing his PhD thesis and is looking for a job. So his spare time is dedicated to ReactOS infra. He just codes random stuff when he has a bit of time and want to breath. Nothing coordinated. He just take the opportunity to report rapidly about Jira. So, it failed, hard, several times, as you all noticed. He opened a support request at Atlassian and a way to upgrade to Jira6 was found. But now LDAP authentication is failing. After a long discussion, debugging and so on, to make sure nothing is wrong on our side, the whole thing has been given to the Jira devs. He hopes they can find a fix. Then, he could attempt yet another upgrade. So far, no ETA, as he is waiting for Jira devs feedback.</p>

<p><b>Thomas Faber:</b> Thomas has been working on random bug fixes, mostly relating to test failures with and without DPH. He made netshell work a bit better. Most recently he has been looking into a couple fastfat issues with Victor, Pierre & Ged. Future-wise, the ugliest outstanding DPH issue (service argument handling seen in advapi32 and services tests) is pretty high on his todo list. But he does not expect to get to much ROS stuff next month.</p>
  
<p><b>Timo Kreuzer:</b> Recently he was mostly busy with being annoyed @ work, but spent some of his free time on some (according to him) mainly useless stuff, like header improvement, some warning fixes, ARM compilation fixes etc. All in his git repo. He will probably soon go back to something in his eyes more useful.</p>
  
<p><b>Victor Martinez:</b> Victor has been moving into some fixings here and there thanks to Ros devs help improving his windbg skills. At the same time he has recorded 4 videos about "Windbg for Dummies by a Dummie"
and his plan is creating some more videos and link to them in our Wiki. He will keep fixing some more tests, too.</p>

<h2>Point 2</h2>
<p>Colin Finck is planning a ReactOS Hackfest for a while now and after some drawbacks it will most likely take place in Aachen about July/August. Some suggestions were made for topics and goals of the event. Except the aim at coding there will be some schoolings, too. Nothing special is planned right now, but mentioned topics were WinDBG and Windows Internals. The event will be open for external supporters from other projects, too. Colin asks all people who want to take part to check their calendars until end of next week and fill the possile days of taking part to a Doodle page.(http://doodle.com/tdaaie3rbbs5phpb)<p>

<p>Meeting was closed at 21:17 by Pierre Schweitzer</p>
<p>Meeting minutes prepared by Daniel Reimer</p>
