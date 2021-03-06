---
title:       "November 2012 Meeting Minutes"
author:      "Z98"
date:        2012-12-20
aliases:     [ "november-2012-meeting-minutes", "node/325" ]
---

<p>2012-11-29<br />19:00 UTC<br />freenode, #reactos-meeting</p>
<p>Proceedings</p>
<hr />
<p>Meeting started at 19:02 by Aleksey Bragin.</p>
<p>
<ul>
<li>Point 1: Contract Status</li>
<li>Point 2: Release Status</li>
<li>Point 3: Website Status</li>
<li>Point 4: VirtualPC Support</li>
</ul>
</p>
<hr />
<p>Point 1</p>
<p>The development team has not been able to get in touch with Magnus Olsen or Mike Nordell for status updates and currently considers these contracts to be voided. Edijs Kolesnikovics reported that work is progressing well, though he faces difficulties in trying to use AutoHotkey to test games. The AHK community is also not a very useful resource in this regard as few use AHK on games. Other issues that cropped up was a failure to install KDE on Windows as part of his initial testing work along with potential license issues with non-open source software. There are also restrictions as to what can be done on the test servers, but Edijs was directed to write the tests anyway so developers at least have something they can try running on their own machines. James Tabor's work also continued, though his progress was more or less self-documented in his commit messages.</p>
<p>Point 2</p>
<p>There were major concerns raised about whether ReactOS is in suitable shape for any sort of release, the biggest being instability in the memory manager having a trickle down effect on the rest of the system. As at this time there are few people intimately familiar with that component of ReactOS, work on it has been stalled for quite some time. Aleksey Bragin pointed out that development need not rely on a perfect underlying system in ReactOS and that higher level components can also be developed and tested on Windows first. However, the state of the ReactOS core is still distressingly brittle from the perspective of many developers and testers. Aleksey also pointed out many bugs exist in Jira that have nothing to do with the core that could see some attention. The testing team however have major reservations about attempting a release in late December, making a release unlikely unless major usability issues can be resolved.</p>
<p>Point 3</p>
<p>Several people involved with the website work were absent due to a variety of real life obligations. Aleksey however proposed that he spend some time with the Drupal based backend to see if he can get it to a working state and then compare it with the Typo3 based site to see which one seems more likely to reach usability first. The project would then run both websites at the same time to help identify any missing content or functionality before killing off the old website.</p>
<p>Point 4</p>
<p>Alexander Rechit pushed the team to consider putting some effort into making ReactOS run on Microsoft VirtualPC without requiring some manual tweaking by a tester or user. Some of the outstanding issues include the VGA emulation giving ReactOS' driver problems, an UniATA problem, and also a kernel trap bug. Aleksey noted that a category for VPC would need to be created in Jira.</p>
<p>Meeting was closed at 20:26 by Aleksey Bragin.</p>
<p>Minutes prepared by Ziliang Guo.</p>
