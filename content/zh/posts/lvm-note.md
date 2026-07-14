---
title: "LVM 的小筆記"
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
因為一些原因，所以我有一臺需要隨時擴展硬碟大小的 Linux server。因為 LVM 的指令真的很難記，所以想要寫一篇小筆記拯救我每次找指令的時間。<br/>
<br/>
## LVM<br/>
<br/>
全名 Logic Volume Manager 邏輯卷管理。因為一不小心就會打成 LLVM 或是 LLM，所以每次找資料都很痛苦。<br/>
<br/>
他是 Linux Volume 管理的抽象層級，透過 LVM 可以做到動態調整 Volume 的大小、快照，或是把兩個硬碟揉成一個 Volume 的花式技巧，是手殘會切錯 Volume 的人的救星。<br/>
<br/>
## 事不宜遲，現在來切顆硬碟<br/>
<br/>
1. 首先你要去買一顆硬碟，然後裝上你的電腦。<br/>
<br/>
2. 第二步，建立一個物理卷（硬碟是哪顆，要自己查喔）<br/>
<br/>
`pvcreate /dev/sdb`<br/>
<br/>
3. 第三步， 建立一個卷群組<br/>
<br/>
`vgcreate [vg name] /dev/sdb`<br/>
<br/>
4. 第四步，建立一個邏輯卷<br/>
<br/>
`lvcreate -L 20G -n [lv name] [vg name]`<br/>
<br/>
這樣就完成一個邏輯卷了，可以開心的格式化、掛載<br/>
<br/>
## 第二課硬碟<br/>
<br/>
尾牙抽到一顆硬碟，開開心心裝上電腦，接下來你可以<br/>
<br/>
1. 建立一個物理卷<br/>
<br/>
`pvcreate /dev/sdc`<br/>
<br/>
2. 擴充邏輯卷<br/>
<br/>
`lvextend -L 20G /dev/[vg name]/[lv name]`<br/>
<br/>
3. 修改你的 filesystem （假設 filesystem 是 ext4）<br/>
<br/>
`resize2fs /dev/[vg name]/[lv name]`<br/>
