---
title:       "GSoC 2018 weeks 3-4 - understanding BTRFS internals"
author:      "extravert34"
date:        2018-06-14
aliases:     [ node/68777 ]

---

<p>
Hi all!<br>
This two weeks I was diving into btrfs structures and on-disk layout. Writing an ASM program from scratch is not that simple so I decided to convert a VirtualBox image with BTRFS filesystem in it to raw file and write a python script to parse and show internal filesystem structures.
</p>
<p>
It was also useful for understanding how files are stored in FS, because information on <a href="https://btrfs.wiki.kernel.org">btrfs.wiki.kernel.org</a> was not enough for me to understand some corner cases.</p>
<p>So here it is - btrfs_structures.py in (<a href="https://github.com/Extravert-ir/reactos/tree/gsoc2018_python-tools/modules/rosapps/applications/rosinternals/btrfstools">/modules/rosapps/applications/rosinternals/btrfstools</a>)</p>
<img src="/sites/default/files/gsoc2018-4.png" alt="Listing directory items">
<p>This script:</p>
<ul>
	<li>understands the most basic BTRFS structures (header, key and item)</li>
	<li>can display a lot of item types (not all of them, but the most useful for me)</li>
	<li>implements a btree search function so you can walk through different BTRFS trees</li>
	<li>automatically builds a chunk map for logical-to-physical address translation</li>
</ul>

<p>With this script I was able to implement a "bootloader" in python - it finds and reads freeldr.sys file in filesystem blob (see btrfs_playground.py in the same folder)</p>
<p>Now it's time to finally write this as VBR code in ASM. See you in next blog post!</p>
