---
title: "Heptabase 的開源方案 - Affine"
date: "2025-06-22T10:00:00+08:00"
tags: ["sharing","affine",]
title-images: ["/images/affine-introduction/affine-pro-logo.webp",]
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
如果你是卡片盒筆記法的愛好者。有別於傳統線性、由上而下的筆記與寫作系統。你喜歡將想法記錄在一張張卡片紙上，並建立卡片之間的關係連結。你應該聽過或看過 Heptabase 這個工具。<br/>
[Heptabase](https://heptabase.com/) 是一款由台灣團隊開發的視覺化筆記工具，主要元素為卡片（Card）與白板（Whiteboard），讓你能夠自由地組織和連結知識，構建個人知識網絡、深入理解複雜主題。<br/>
Heptabase 官方的網站提供詳盡的使用教學與說明，因此這裡不再多加贅述。它功能齊全且畫面設計也賞心悅目。<br/>
不過如果想要一個也是有卡片與白板概念的筆記軟體，並且是開源的替代方案，那一定要來試試看 [AFFiNE](https://affine.pro/)。<br/>
除了卡片、白板與 Notion 的資料庫概念，還可以畫心智圖、繪圖等功能。而且重視隱私跟資訊安全，所以你可以只使用在 local 而不開啟雲端功能，甚至可以自架一個自己的 Server ，管理自己的筆記資料。<br/>
<br/>
## 比較<br/>
<br/>
<table><br/>
    <tr><br/>
        <th scope="col"></th><br/>
        <th scope="col">AFFiNE</th><br/>
        <th scope="col">Heptabase</th><br/>
    </tr><br/>
    <tr><br/>
        <th scope"row">核心功能</th><br/>
        <td><br/>
            <ul><br/>
                <li>文檔編輯、白板繪圖、資料庫管理三合一</li><br/>
                <li>本地儲存與隱私保護</li><br/>
                <li>支援 Markdown 編輯</li><br/>
            </ul><br/>
        </td><br/>
        <td><br/>
            <ul><br/>
                <li>白板與心智圖視覺化筆記</li><br/>
                <li>支援 PDF 標註與多媒體內容</li><br/>
                <li>支援 Markdown 編輯</li><br/>
            </ul><br/>
        </td><br/>
    </tr><br/>
    <tr><br/>
        <th scope"row">平台支援</th><br/>
        <td><br/>
            <ul><br/>
                <li>桌面應用程式</li><br/>
                <li>網頁版</li><br/>
            </ul><br/>
        </td><br/>
        <td><br/>
            <ul><br/>
                <li>桌面應用程式</li><br/>
                <li>網頁版</li><br/>
                <li>行動裝置</li><br/>
            </ul><br/>
        </td><br/>
    </tr><br/>
    <tr><br/>
        <th scope"row">同步與協作</th><br/>
        <td><br/>
            <ul><br/>
                <li>支援本地儲存與雲端同步</li><br/>
                <li>免費版提供 10GB 雲端儲存空間</li><br/>
                <li>支援多人協作與即時同步</li><br/>
            </ul><br/>
        </td><br/>
        <td><br/>
            <ul><br/>
                <li>支援多裝置同步與離線存取</li><br/>
                <li>支援多人協作與即時同步</li><br/>
            </ul><br/>
        </td><br/>
    </tr><br/>
    <tr><br/>
        <th scope"row">開源與隱私</th><br/>
        <td><br/>
            <ul><br/>
                <li>完全開源，使用者可自行部署</li><br/>
                <li>資料預設儲存在本地，強調隱私保護</li><br/>
            </ul><br/>
        </td><br/>
        <td><br/>
            <ul><br/>
                <li>專有軟體，非開源</li><br/>
                <li>資料儲存在雲端，但支援離線存取</li><br/>
            </ul><br/>
        </td><br/>
    </tr><br/>
</table><br/>
<br/>
<br>
<br/>
但相對於 Heptabase 在官方網站上寫的各類的教學文件，AFFiNE 的官網文件表明：「AFFiNE is not a dedicated tool. You should find your best way to use AFFiNE.」<br/>
AFFiNE 不是一個指導使用者怎麼使用的工具，所以你可以隨意使用這個工具。<br/>
<br/>
假如你喜歡：<br/>
1. 漂亮的界面設計<br/>
2. 豐富多樣的功能<br/>
3. 明確的使用範例<br/>
4. 減少管理筆記以外的心智負擔<br/>
<br/>
推薦可以使用 Heptabase<br/>
<br/>
假如你喜歡：<br/>
1. 開源或可自行管理資料<br/>
2. 更想要一個單機工具，而不是雲端工具<br/>
3. 想要可以在白板上隨意塗鴉<br/>
<br/>
那來試試 AFFiNE 吧！<br/>
<br/>
## 一些心得<br/>
最後來說一下，我自己從 Heptabase 轉到 AFFiNE 一陣子了。<br/>
主因是我發現自己其實使用 Heptabase 時，很簡單的只是想要「卡片與白板」的功能而已，其他的功能很少用到。有的時候忙起來甚至一個月開不到幾次的筆記軟體，常常在想花這個錢，但是沒有把這個工具發揮的淋漓盡致，很愧對我的錢（？）。<br/>
所以大約年初的時候，我就退掉了 Heptabase ，轉而尋找替代方案。感謝 ChatGPT 讓我認識了這個替代方案！<br/>
AFFiNE 的自架方案很簡便，只要照著官網文件，用 docker compose 輕輕鬆鬆就能架起來。<br/>
另外，我覺得可以自己掌握資料，不用擔心在雲端的筆記軟體寫這個公司系統設計的筆記，是不是一種商業機密洩漏（想太多了吧），心理上還是有好過一點。<br/>
不過我在自架的過程中，認真計算了一下成本這件事，意識到也許自架筆記軟體的成本不會比使用雲服務筆記軟體還要便宜，不過這個就是後話了。之後再寫一篇「架設自己的筆記軟體與買筆記服務哪個更划算」的文吧。<br/>
