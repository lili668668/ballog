---
title: "LVM のちょっとしたメモ"
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

とある理由で、私はいつでもディスク容量を拡張できる必要のある Linux サーバーを1台持っています。LVM のコマンドは本当に覚えづらいので、毎回コマンドを探す時間を救うために、ちょっとしたメモを書いておきたくなりました。

## LVM

正式名称は Logical Volume Manager（論理ボリューム管理）です。うっかりすると LLVM や LLM と打ってしまうので、毎回資料を探すのがとても大変です。

これは Linux のボリューム管理の抽象化レイヤーで、LVM を通じてボリュームサイズの動的な調整、スナップショット、あるいは2つのディスクを1つのボリュームに揉み込むといった小技もこなせます。うっかりボリュームを切り間違える不器用な人にとっての救世主です。

## 善は急げ、さっそくディスクを1つ切ってみよう

1. まずはディスクを1つ買ってきて、あなたのパソコンに取り付けます。

2. 第二歩、物理ボリュームを1つ作成します（どのディスクなのかは自分で調べてね）。

`pvcreate /dev/sdb`

3. 第三歩、ボリュームグループを1つ作成します。

`vgcreate [vg name] /dev/sdb`

4. 第四歩、論理ボリュームを1つ作成します。

`lvcreate -L 20G -n [lv name] [vg name]`

これで論理ボリュームが1つ完成です。あとは楽しくフォーマットしてマウントできます。

## 二つ目のディスク

忘年会の抽選でディスクを1つ引き当て、うきうきしながらパソコンに取り付けたら、次にできることは、

1. 物理ボリュームを1つ作成します。

`pvcreate /dev/sdc`

2. 論理ボリュームを拡張します。

`lvextend -L 20G /dev/[vg name]/[lv name]`

3. あなたの filesystem を変更します（filesystem が ext4 だと仮定します）。

`resize2fs /dev/[vg name]/[lv name]`
