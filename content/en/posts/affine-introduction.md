---
title: "AFFiNE: The Open-Source Alternative to Heptabase"
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
If you're a fan of the Zettelkasten method—a non-linear, card-based system of note-taking and writing that emphasizes linking ideas rather than organizing them from top to bottom—then you've probably heard of or seen Heptabase.<br/>
[Heptabase](https://heptabase.com/) is a visual note-taking tool developed by a Taiwanese team. It revolves around cards and whiteboards, allowing you to freely organize and connect ideas to build your personal knowledge network and better understand complex topics.<br/>
The official website provides many tutorials and documentation, so I won’t go into too much detail here. It's feature-rich and beautifully designed.<br/>
However, if you're looking for an open-source alternative with similar card and whiteboard concepts, you should definitely check out [AFFiNE](https://affine.pro/).<br/>
Besides cards, whiteboards, and Notion-style databases, AFFiNE also supports mind maps, drawing, and more. It places a strong emphasis on privacy and data security, so you can use it entirely offline or even self-host your own server to manage your notes.<br/>
<br/>
## Comparison<br/>
<br/>
<table><br/>
    <tr><br/>
        <th scope="col"></th><br/>
        <th scope="col">AFFiNE</th><br/>
        <th scope="col">Heptabase</th><br/>
    </tr><br/>
    <tr><br/>
        <th scope"row">Core Features</th><br/>
        <td><br/>
            <ul><br/>
                <li>All-in-one document editing, whiteboard drawing, and database management</li><br/>
                <li>Local storage with privacy protection</li><br/>
                <li>Markdown support</li><br/>
            </ul><br/>
        </td><br/>
        <td><br/>
            <ul><br/>
                <li>Whiteboards and mind map visual note-taking</li><br/>
                <li>PDF annotation and multimedia support</li><br/>
                <li>Markdown support</li><br/>
            </ul><br/>
        </td><br/>
    </tr><br/>
    <tr><br/>
        <th scope"row">Platform Support</th><br/>
        <td><br/>
            <ul><br/>
                <li>Desktop app</li><br/>
                <li>Web</li><br/>
            </ul><br/>
        </td><br/>
        <td><br/>
            <ul><br/>
                <li>Desktop app</li><br/>
                <li>Web</li><br/>
                <li>Mobile app</li><br/>
            </ul><br/>
        </td><br/>
    </tr><br/>
    <tr><br/>
        <th scope"row">Sync & Collaboration</th><br/>
        <td><br/>
            <ul><br/>
                <li>Supports local storage and cloud sync</li><br/>
                <li>Free tier includes 10GB cloud space</li><br/>
                <li>Real-time collaboration support</li><br/>
            </ul><br/>
        </td><br/>
        <td><br/>
            <ul><br/>
                <li>Multi-device sync and offline access</li><br/>
                <li>Real-time collaboration support</li><br/>
            </ul><br/>
        </td><br/>
    </tr><br/>
    <tr><br/>
        <th scope"row">Open Source & Privacy</th><br/>
        <td><br/>
            <ul><br/>
                <li>Fully open source, self-hostable</li><br/>
                <li>Local storage by default, privacy-focused</li><br/>
            </ul><br/>
        </td><br/>
        <td><br/>
            <ul><br/>
                <li>Proprietary software, not open source</li><br/>
                <li>Cloud storage with offline access</li><br/>
            </ul><br/>
        </td><br/>
    </tr><br/>
</table><br/>
<br/>
<br>
<br/>
Compared to Heptabase’s a lot of official documentation, AFFiNE’s site says:"AFFiNE is not a dedicated tool. You should find your best way to use AFFiNE."<br/>
In other words, AFFiNE doesn’t dictate how you should use it—you’re free to explore and shape your own workflow.<br/>
<br/>
Choose Heptabase if you prefer:<br/>
1. A beautiful user interface<br/>
2. Rich and varied features<br/>
3. Clear usage examples<br/>
4. Reducing mental load in managing notes<br/>
<br/>
Choose AFFiNE if you prefer:<br/>
1. Open-source or self-hostable tools<br/>
2. A fully local, offline solution instead of a cloud-based one<br/>
3. The freedom to doodle and sketch on whiteboards as you like<br/>
<br/>
## Some Thoughts<br/>
I personally switched from Heptabase to AFFiNE a while ago.<br/>
The main reason: I realized that I only really used the card + whiteboard feature in Heptabase. I hardly touched the other functionalities. Sometimes, when I was busy, I barely opened the app for a whole month. Paying for a tool I wasn’t fully using made me feel like I was wasting money.<br/>
So, earlier this year, I canceled my Heptabase subscription and began searching for alternatives. Thanks to ChatGPT, I discovered AFFiNE!<br/>
Setting up a self-hosted AFFiNE instance was super easy—just followed the official documentation and used `docker compose` to get it up and running.<br/>
I also appreciate being in control of my own data. It puts my mind at ease when writing notes on, say, system design at work, without worrying whether I’m exposing company secrets to some cloud-based service<br/>
That said, during the self-hosting process, I did seriously calculate the costs—and realized that self-hosting a note-taking app may not actually be cheaper than using a cloud-based one. But that’s another story. I’ll probably write a separate post on "Is it more cost-effective to self-host your note-taking app or just pay for a service?"<br/>
