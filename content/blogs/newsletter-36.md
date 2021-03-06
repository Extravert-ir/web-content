---
title:       "Newsletter 36"
author:      "Z98"
date:        2008-01-08
aliases:     [ "newsletter-36", "node/176" ]
---

<h2>General Developments</h2>
<p>
Aleksey and Herve have been working on the PnP problem, which many people are experiencing through the unresponsive mouse or keyboard.  At least some of the problem&#39;s been fixed, since people seem to have better success.  In an attempt to squash the rest of the bug, Aleksey is updating the Remote Procedure Call code in ROS.  Also, a working RPC would also allow WIDL, our substitute for MIDL (Microsoft Interface Definition Language), a method for software components written in different programming languages to communicate, to finally work.
</p>
<p>
Other people have reported problems with trying to install ReactOS on QEMU with kqemu enabled.  Aleksey is also investigating this problem and believes it to be due to VFAT.  This may not be fixed in time for release.
</p>
<p>
While we haven&#39;t been following the two month release schedule that well, the project is releasing much faster than in the past.  This means two things.  One, trunk is behaving quite nicely.  Two, the developers are breaking less and less things.  Both obviously help with development, but there&#39;s a limit to what the current manpower is capable of achieving.
</p>
<h2>More Newcomers</h2>
<p>
We have yet two more developers joining us.  Everyone, welcome Andrey Korotaev, unC0Rr on IRC, and Dmitry Chapyshev, Lentin on IRC.  Andrey is an especially brave one, selecting to to try and tackle the long neglected Cache Controller/Manager rewrite.  How important is the CC?  Well, the lack of a proper one prevents us from supporting more complex filesystems like ext3, NTFS, and such.  So far, he&#39;s been working to get the CC branch to a point where it can compile again, though much of it will have to be updated for the current kernel.  Dmitry on the other hand likes variety and has worked on several components of ReactOS, including the installer and various DLLs plus various translations for Russian.
</p>
<h2>SharpOS</h2>
<p>
ReactOS is not the only project aiming to clone certain Microsoft technologies, but these guys are even more ambitious. SharpOS is an attempt to write an operating system completely in C#, something similar to what Microsoft did with the Singularity project.  They&#39;ve also adopted the microkernel design Microsoft used and in many ways are breaking many conventions in OS design and programming.  SharpOS just released their first milestone so go check them out.  We of the ReactOS project wish them the best of luck.
</p>

