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
<!-- introduction -->
<!--more-->
<!-- rest of the content -->
## TL;DR

因為一些原因，所以我有一臺需要隨時擴展硬碟大小的 Linux server。因為 LVM 的指令真的很難記，所以想要寫一篇小筆記拯救我每次找指令的時間。

## LVM

全名 Logic Volume Manager 邏輯卷管理。因為一不小心就會打成 LLVM 或是 LLM，所以每次找資料都很痛苦。

他是 Linux Volume 管理的抽象層級，透過 LVM 可以做到動態調整 Volume 的大小、快照，或是把兩個硬碟揉成一個 Volume 的花式技巧，是手殘會切錯 Volume 的人的救星。

## 事不宜遲，現在來切顆硬碟

1. 首先你要去買一顆硬碟，然後裝上你的電腦。

2. 第二步，建立一個物理卷（硬碟是哪顆，要自己查喔）

`pvcreate /dev/sdb`

3. 第三步， 建立一個卷群組

`vgcreate [vg name] /dev/sdb`

4. 第四步，建立一個邏輯卷

`lvcreate -L 20G -n [lv name] [vg name]`

這樣就完成一個邏輯卷了，可以開心的格式化、掛載

## 第二課硬碟

尾牙抽到一顆硬碟，開開心心裝上電腦，接下來你可以

1. 建立一個物理卷

`pvcreate /dev/sdc`

2. 擴充邏輯卷

`lvextend -L 20G /dev/[vg name]/[lv name]`

3. 修改你的 filesystem （假設 filesystem 是 ext4）

`resize2fs /dev/[vg name]/[lv name]`
