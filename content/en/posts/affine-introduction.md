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
<!-- introduction -->
<!--more-->
<!-- rest of the content -->
## TL;DR
If you're a fan of the Zettelkasten method—a non-linear, card-based system of note-taking and writing that emphasizes linking ideas rather than organizing them from top to bottom—then you've probably heard of or seen Heptabase.
[Heptabase](https://heptabase.com/) is a visual note-taking tool developed by a Taiwanese team. It revolves around cards and whiteboards, allowing you to freely organize and connect ideas to build your personal knowledge network and better understand complex topics.
The official website provides many tutorials and documentation, so I won’t go into too much detail here. It's feature-rich and beautifully designed.
However, if you're looking for an open-source alternative with similar card and whiteboard concepts, you should definitely check out [AFFiNE](https://affine.pro/).
Besides cards, whiteboards, and Notion-style databases, AFFiNE also supports mind maps, drawing, and more. It places a strong emphasis on privacy and data security, so you can use it entirely offline or even self-host your own server to manage your notes.

## Comparison

<table>
    <tr>
        <th scope="col"></th>
        <th scope="col">AFFiNE</th>
        <th scope="col">Heptabase</th>
    </tr>
    <tr>
        <th scope"row">Core Features</th>
        <td>
            <ul>
                <li>All-in-one document editing, whiteboard drawing, and database management</li>
                <li>Local storage with privacy protection</li>
                <li>Markdown support</li>
            </ul>
        </td>
        <td>
            <ul>
                <li>Whiteboards and mind map visual note-taking</li>
                <li>PDF annotation and multimedia support</li>
                <li>Markdown support</li>
            </ul>
        </td>
    </tr>
    <tr>
        <th scope"row">Platform Support</th>
        <td>
            <ul>
                <li>Desktop app</li>
                <li>Web</li>
            </ul>
        </td>
        <td>
            <ul>
                <li>Desktop app</li>
                <li>Web</li>
                <li>Mobile app</li>
            </ul>
        </td>
    </tr>
    <tr>
        <th scope"row">Sync & Collaboration</th>
        <td>
            <ul>
                <li>Supports local storage and cloud sync</li>
                <li>Free tier includes 10GB cloud space</li>
                <li>Real-time collaboration support</li>
            </ul>
        </td>
        <td>
            <ul>
                <li>Multi-device sync and offline access</li>
                <li>Real-time collaboration support</li>
            </ul>
        </td>
    </tr>
    <tr>
        <th scope"row">Open Source & Privacy</th>
        <td>
            <ul>
                <li>Fully open source, self-hostable</li>
                <li>Local storage by default, privacy-focused</li>
            </ul>
        </td>
        <td>
            <ul>
                <li>Proprietary software, not open source</li>
                <li>Cloud storage with offline access</li>
            </ul>
        </td>
    </tr>
</table>

<br>

Compared to Heptabase’s a lot of official documentation, AFFiNE’s site says:"AFFiNE is not a dedicated tool. You should find your best way to use AFFiNE."
In other words, AFFiNE doesn’t dictate how you should use it—you’re free to explore and shape your own workflow.

Choose Heptabase if you prefer:
1. A beautiful user interface
2. Rich and varied features
3. Clear usage examples
4. Reducing mental load in managing notes

Choose AFFiNE if you prefer:
1. Open-source or self-hostable tools
2. A fully local, offline solution instead of a cloud-based one
3. The freedom to doodle and sketch on whiteboards as you like

## Some Thoughts
I personally switched from Heptabase to AFFiNE a while ago.
The main reason: I realized that I only really used the card + whiteboard feature in Heptabase. I hardly touched the other functionalities. Sometimes, when I was busy, I barely opened the app for a whole month. Paying for a tool I wasn’t fully using made me feel like I was wasting money.
So, earlier this year, I canceled my Heptabase subscription and began searching for alternatives. Thanks to ChatGPT, I discovered AFFiNE!
Setting up a self-hosted AFFiNE instance was super easy—just followed the official documentation and used `docker compose` to get it up and running.
I also appreciate being in control of my own data. It puts my mind at ease when writing notes on, say, system design at work, without worrying whether I’m exposing company secrets to some cloud-based service
That said, during the self-hosting process, I did seriously calculate the costs—and realized that self-hosting a note-taking app may not actually be cheaper than using a cloud-based one. But that’s another story. I’ll probably write a separate post on "Is it more cost-effective to self-host your note-taking app or just pay for a service?"
