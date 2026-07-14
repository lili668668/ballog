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
<!-- introduction --><br/>
<!--more--><br/>
<!-- rest of the content --><br/>
## TL;DR<br/>
<br/>
とある理由で、私はいつでもディスク容量を拡張できる必要のある Linux サーバーを1台持っています。LVM のコマンドは本当に覚えづらいので、毎回コマンドを探す時間を救うために、ちょっとしたメモを書いておきたくなりました。<br/>
<br/>
## LVM<br/>
<br/>
正式名称は Logical Volume Manager（論理ボリューム管理）です。うっかりすると LLVM や LLM と打ってしまうので、毎回資料を探すのがとても大変です。<br/>
<br/>
これは Linux のボリューム管理の抽象化レイヤーで、LVM を通じてボリュームサイズの動的な調整、スナップショット、あるいは2つのディスクを1つのボリュームに揉み込むといった小技もこなせます。うっかりボリュームを切り間違える不器用な人にとっての救世主です。<br/>
<br/>
## 善は急げ、さっそくディスクを1つ切ってみよう<br/>
<br/>
1. まずはディスクを1つ買ってきて、あなたのパソコンに取り付けます。<br/>
<br/>
2. 第二歩、物理ボリュームを1つ作成します（どのディスクなのかは自分で調べてね）。<br/>
<br/>
`pvcreate /dev/sdb`<br/>
<br/>
3. 第三歩、ボリュームグループを1つ作成します。<br/>
<br/>
`vgcreate [vg name] /dev/sdb`<br/>
<br/>
4. 第四歩、論理ボリュームを1つ作成します。<br/>
<br/>
`lvcreate -L 20G -n [lv name] [vg name]`<br/>
<br/>
これで論理ボリュームが1つ完成です。あとは楽しくフォーマットしてマウントできます。<br/>
<br/>
## 二つ目のディスク<br/>
<br/>
忘年会の抽選でディスクを1つ引き当て、うきうきしながらパソコンに取り付けたら、次にできることは、<br/>
<br/>
1. 物理ボリュームを1つ作成します。<br/>
<br/>
`pvcreate /dev/sdc`<br/>
<br/>
2. 論理ボリュームを拡張します。<br/>
<br/>
`lvextend -L 20G /dev/[vg name]/[lv name]`<br/>
<br/>
3. あなたの filesystem を変更します（filesystem が ext4 だと仮定します）。<br/>
<br/>
`resize2fs /dev/[vg name]/[lv name]`<br/>
