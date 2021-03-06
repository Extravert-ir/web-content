---
title:       "NTFS Write Support GSoC - Week 8"
author:      "coderTrevor"
date:        2016-07-19
aliases:     [ node/14060 ]

---

<h3>Overwriting Files Continues</h3>

This week has been pretty uneventful. I wrote a function to shrink the allocation size of an attribute and another to migrate a resident attribute to non-resident. The former seems to be working, the latter still needs some work.

<h3>Looking Forward (Changing Direction)</h3>
I'm only planning to spend another couple of days working on updating files, then I want to move on to file creation. There are several reasons motivating this thinking. For one thing, it's getting increasingly rare that the items that are still remaining TODO regarding overwriting files are issues that a user will encounter. Despite this fact, they seem to have no problem multiplying!

The other reason is that I'm just getting a little burnt-out on updating files. Even when I make progress, there's nothing new to show anymore. There's only so many times you can see a side-by-side of the same file in Notepad.exe in ROS and Windows before it becomes boring.

The main reason for moving on to file creation is that it just needs to be addressed! If I spend too much time perfecting file overwriting, I risk leaving file creation undone by the end of GSoC. I know nobody wants that!

Last but certainly not least, the driver now has basic write functionality to build on.

Adding the ability to create files will also unlock a lot of potential for testing. So far, I've relied on writing a custom tester that needs to be run in Windows first to create the files it will be testing. It's been made very much with the limitations of the driver in mind. Despite that, it's done an excellent job of finding errors! Automated testing really is essential for this kind of project. I'm looking forward to running some more general filesystem tests (I'm told WINE's tests are quite thorough) and fixing the failures these tests find!




<h3><a href="https://www.reactos.org/forum/viewtopic.php?f=2&t=15599">Discussion</a></h3>
