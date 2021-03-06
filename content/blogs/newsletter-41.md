---
title:       "Newsletter 41"
author:      "Z98"
date:        2008-05-15
aliases:     [ "newsletter-41", "node/181" ]
---

<p>
Just a reminder that there really isn&#39;t any set schedule for newsletters anymore.  We (or at least I) publish whenever there&#39;s something to report, and boy do we have a lot of ground to cover.  The past few weeks have been very eventful.
</p>
<h2>0.3.5 and Development Focus</h2>
<p>
Amongst the developers, the joke was that Aleksey&#39;s vacation delayed the release, so it was his fault that we&#39;re behind.  Now, it is Aleksey&#39;s fault, but for a different reason.  Those people who are subscribed to the mailing list may have noticed a rather lengthy statement by him about the current state and focus of development, specifically the lack of quality assurance and proper regression testing.  Because of this, Aleksey has pushed back the release so that some work can go into fixing long standing bugs and other compatibility issues.
</p>
<p>
One thing Aleksey stressed was focusing on bugfixing the Win32 subsystem, getting it to the level that Wine has had it for quite some time.  He believes that people should stop adding new features to it and instead work on maintaining the code already present, which should reduce breakages and limit the number of regressions.  Winetests were pointed out as an easy way to find breakages, though we would need to write tests for other components ourselves.  However, just finding the bugs in Win32 should allow many other programs to run.  Developments in the kernel are shifting more and more failures to the Win32 subsystem, so more attention needs to be paid to it.  His nagging seems to have paid off, as over the past week a great many fixes were committed.  Now we just need to keep going on this track.
</p>
<p>
Right now, Aleksey&#39;s priorities are limited to stability of the OS as a whole and application compatibility.  Compatibility with NT internals is a nice bonus, but for the time being doesn&#39;t yield much in the way of immediate benefits.
</p>
<p>
Aleksey isn&#39;t the only one to have complained about regression testing, as Samuel, the other newsletter writer (in theory), ranted about it not too long ago.  A few other developers have pitched ideas and one I&#39;ve pushed for is including the rostests module in trunk builds.
</p>
<h2>RBuild</h2>
<p>
Possibly spurned on by Aleksey&#39;s position regarding general development, KJK decided to start airing some of his grievances with RBuild.  These problems aren&#39;t new and have been annoying a lot of the developers and testers.  These problems range from poorly constructed solution files for Visual Studio to completely mixed up dependencies.  In many ways, ReactOS has outgrown RBuild, as the lack of modules for certain things result in the need to hack things in.  Marc has been hard at work fixing what he can, but it&#39;s a lot of work for one person to do.
</p>
<h2>Unicode</h2>
<p>
Unicode, that character encoding standard that allows for representation of basically every known language in the world.  NT uses unicode internally and in almost everything else.  The difficult part is all the data and algorithms that go into unicode.  Fortunately, there are other projects out there that have implemented all this.  KJK has decided that he&#39;s going to try the unicode dll, normaliz.dll, using the International Components for Unicode library.  The ICU library is huge and has implemented everything we should need for unicode support, saving us the work.  Wine also once attempted to integrate ICU, but the size of the library proved troublesome.  For us, the biggest problem will likely be the fact ICU is written in C++.  We&#39;ve always had problems with it, partially because of the GCC C++ compiler.  Hopefully KJK can get around them.
</p>
<h2>NoCc</h2>
<p>
According to Alex Ionescu, Cc stands for Common Cache, not Cache Controller.  Just a bit of trivia.  Anyways, the Cc in ROS has always been problematic.  Its original design was wrong on a conceptual level and quite possibly was the cause of a great deal of instability. Even if the system survives the corruption and overwrites committed by Cc, it renders the system more or less unusable in other regards. The most blatant problem is ROS crashing due to massive file copying, which happens whenever a large application is installed.  But this isn&#39;t the only problem.  Aleksey has been working on a new pool manager that is much more strict than what we have now and more NT like in behavior.  We need the new pool manager to fix other problems, such as getting OpenOffice to run.
</p>
<p>
Now the Cc has always been heavily tied to the memory manager.  More appropriately, there isn&#39;t an actual component called the Cc. The Cc just exposes certain services of the Mm.  What we have in ROS right now is a Mm completely different from NT, which results in a very different Cc.  Rewriting the Mm is going to take a long time and Aleksey&#39;s new pool code is part of that effort, but because of how Cc is tied directly into Mm, it&#39;s becoming a major obstacle.  The current solution is to remove caching entirely from the kernel and transfer read/write requets directly to the storage stack drivers, hence the name NoCc.  The hope is to get NoCc ready in time for the 0.3.5 release, which might well be possible.
</p>
<p>
For the long term, after NoCc is working as well as possible, the intention is to add some very simple Least Recently Used caching algorithms.  This will still be a far cry from the Nt Common Cache, but we&#39;ll at least get back on track in terms of proper implementation.
</p>
<h2>Security</h2>
<p>
A lot of people have been especially concerned about the hypothetical security of ReactOS in the future, fearing that by being an NT clone, ReactOS would be vulnerable to the same thing Windows is.  I&#39;m not really going to touch that, since that is still hypothetical and who knows what the future will bring.  But people do raise an interesting point regarding ROS security and its current state. I talked with Herve about this and he offered some enlightening explanations.  In the past, ROS didn&#39;t even have the infrastructure for any security or authentication beyond the usual user-kernel mode transitions, so all the components were written with this in mind.  We&#39;ve come a long way since then, with support for ACLs and other security checks being added over the years.  The problem is so few of the components have been updated to actually use those checks.  Now adding those checks will impact performance, an unavoidable fact.  However, it&#39;s something that needs to be done or we end up with holes left all over the system.  The developers have been working to plug them, but again this takes time.
</p>
<p>
Most of the infrastructure for proper security is in place, with the catch being since so much of it is untested, there may be bugs we aren&#39;t aware of.
</p>
<h2>Welcome Steven Edwards</h2>
<p>
Granted Steven still acted as a liasion between ROS and Wine, he stopped being a formal developer after he resigned as project coordinator back in early 2006.  However, no one truly escapes from us and Steven has returned to the fold.  Hopefully his return heralds a new era of cooperation and reconciliation between us and various parties within Wine.
</p>
<h2>Chinese Language</h2>
<p>
This should have been done a long time ago, but Klemens has finally gotten around to splitting the Chinese language option into Traditional and Simplified.  Now I just need to get in touch with the people who offered to act as translators for Simplified and get the ball rolling.
</p>

