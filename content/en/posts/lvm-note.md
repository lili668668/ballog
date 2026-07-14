---
title: "A Little Note on LVM"
date: "2026-07-10T19:00:00+08:00"
tags: ["note","lvm","linux",]
title-images: []
ending-images: []
author: "ballfish"
draft: false
table-of-contents: true
toc-auto-numbering: true
---
<!-- introduction --><br/>
<!--more--><br/>
<!-- rest of the content --><br/>
## TL;DR<br/>
<br/>
For certain reasons, I have a Linux server whose disk size needs to be expandable at any time. Since LVM commands are really hard to remember, I wanted to write a little note to save myself the time I spend looking up the commands every single time.<br/>
<br/>
## LVM<br/>
<br/>
Its full name is Logical Volume Manager. Because it's so easy to accidentally type it as LLVM or LLM, looking things up is painful every time.<br/>
<br/>
It's an abstraction layer for managing Linux volumes. Through LVM you can dynamically resize volumes, take snapshots, or pull off fancy tricks like merging two disks into a single volume. It's a lifesaver for people who are clumsy enough to slice up the wrong volume.<br/>
<br/>
## No Time to Waste—Let's Carve Up a Disk<br/>
<br/>
1. First, you need to go buy a disk and install it in your machine.<br/>
<br/>
2. Second step: create a physical volume (you have to figure out which disk it is yourself).<br/>
<br/>
`pvcreate /dev/sdb`<br/>
<br/>
3. Third step: create a volume group.<br/>
<br/>
`vgcreate [vg name] /dev/sdb`<br/>
<br/>
4. Fourth step: create a logical volume.<br/>
<br/>
`lvcreate -L 20G -n [lv name] [vg name]`<br/>
<br/>
And with that, a logical volume is done. You can happily format and mount it.<br/>
<br/>
## The Second Disk<br/>
<br/>
You won a disk in the year-end lottery, joyfully installed it in your machine, and now you can:<br/>
<br/>
1. Create a physical volume.<br/>
<br/>
`pvcreate /dev/sdc`<br/>
<br/>
2. Extend the logical volume.<br/>
<br/>
`lvextend -L 20G /dev/[vg name]/[lv name]`<br/>
<br/>
3. Modify your filesystem (assuming the filesystem is ext4).<br/>
<br/>
`resize2fs /dev/[vg name]/[lv name]`<br/>
