---
title: "GitLab 升級隨筆"
date: "2026-07-10T10:00:00+08:00"
tags: ["note","gitlab",]
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

升級 GitLab 是個全是苦勞的工作。我喜歡在颱風假的時候做這件事，因為颱風假不能出門，同時不會有人上班，所以如果不小心讓 GitLab shutdown 了，也沒有壓力。

這個筆記是在下個颱風假來臨時，當要升級 GitLab 時，我可以把遇到坑坑疤疤重新復習一遍。

## 備份

升級一定有風險，系統升級有賺有賠，升級前應做好備份，並且詳閱 Change Log。

## 查詢 GitLab 升級路徑

GitLab 升級如果照著一定的版號順序往上升，可以保障資料庫的 migration 一切順利，因此查看這個

https://gitlab-com.gitlab.io/support/toolbox/upgrade-path

GitLab 升級路徑查詢網站，十分重要。

有這個升級路徑查詢網站，就成功一半了！

## 升級後確認狀態

狀態確認有三項

1. 網站活著嗎？
  - 通常升級上去 GitLab 會重啟，網站會在啟動狀態上待一陣子，所以看到 502，莫急莫慌莫害怕。如果你去吃個早餐回來，他還沒有好，再來害怕即可。
2. `sudo gitlab-rake gitlab:check`
  - GitLab 其他東西的狀態。
  - 該指令是如果 GitLab 裸裝在機器上的話，才可直接複製貼上的指令。如果用的是 docker 需要去尋找 docker 使用的指令。
3. `sudo gitlab-rake gitlab:doctor:secrets`
  - 檢查 GitLab 執行個體中「加密資料」是否能被目前的 secrets 金鑰正確解密。
  - 該指令是如果 GitLab 裸裝在機器上的話，才可直接複製貼上的指令。如果用的是 docker 需要去尋找 docker 使用的指令。
  - 這個指令可能會執行個一小時都不動，所以其實沒有很大的升級的話，也可以不用檢查他。

## 升級再升級

通常如果好久沒有升級了，那升級路徑一定會長得一個颱風假無法完成，這個時候，你需要兩個颱風假！（X）

通常升級完後，會急著想要升級下一個，但在升級下一個路徑之前，建議先打開一個重要界面一看

https://[domain]/admin/background_migrations

這個界面是 GitLab 內部資料庫的 migration 進度頁面。

幸運的話，這個界面會空空如也；不幸的話，這個頁面會有一堆就算吃一個午餐回來也還消化不完的 migration

身為一個具備耐心的工程師，通常要做的就是等待這坨 migration 消化完，再進行下一步，畢竟大家不會希望一個颱風假回來，GitLab 的內部資料庫亂成一鍋粥的樣子。

## 那個永遠不會動的 migration

當你吃個午餐回來，滿心歡喜打開 migration 頁面，看到他還沒有跑完。不只沒有跑完，有個 `RemoveOldJobTokens: p_ci_builds` 他就停在 0.00% 不動了。考完個 CKA 回來還沒有繼續動。

身為一個不具備耐心的工程師，一定會直覺發現不正常的地方。這個時候你順著查下去，然後發現，他只是在等一個系統閒置的時候才要動。搞什麼東西，颱風天就是你最閒的時候，還想要當系統薪水小偷嗎？

這個時候你需要

`sudo gitlab-rake gitlab:background_migrations:finalize[RemoveOldJobTokens,p_ci_builds,id,'[]']`

強制執行他。

