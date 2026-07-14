---
title: "Notes on Upgrading GitLab"
date: "2026-07-10T10:00:00+08:00"
tags: ["note","gitlab",]
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
Upgrading GitLab is nothing but hard, thankless labor. I like to do it during a typhoon day off, because you can't go out anyway, and no one else is working. So if I accidentally shut GitLab down, there's no pressure.<br/>
<br/>
This note is so that the next time a typhoon day off rolls around and I need to upgrade GitLab, I can revisit all the potholes and scars I ran into.<br/>
<br/>
## Backups<br/>
<br/>
Upgrades always carry risk—a system upgrade can pay off or backfire. Before upgrading, make a proper backup and read the Change Log carefully.<br/>
<br/>
## Finding the GitLab Upgrade Path<br/>
<br/>
If you upgrade GitLab by following a specific sequence of version numbers step by step, you can guarantee that the database migrations go smoothly. So check out this:<br/>
<br/>
https://gitlab-com.gitlab.io/support/toolbox/upgrade-path<br/>
<br/>
The GitLab upgrade path lookup site is extremely important.<br/>
<br/>
With this upgrade path lookup site, you're already halfway to success!<br/>
<br/>
## Verifying Status After the Upgrade<br/>
<br/>
There are three things to check:<br/>
<br/>
1. Is the site alive?<br/>
  - Usually after the upgrade GitLab restarts, and the site stays in the "starting up" state for a while. So if you see a 502, don't panic, don't rush, don't be afraid. If you go grab breakfast and it's still not up when you get back, then you can start to worry.<br/>
2. `sudo gitlab-rake gitlab:check`<br/>
  - The status of GitLab's other components.<br/>
  - This command can be copy-pasted directly only if GitLab is installed bare-metal on the machine. If you're using Docker, you'll need to find the Docker equivalent.<br/>
3. `sudo gitlab-rake gitlab:doctor:secrets`<br/>
  - Checks whether the "encrypted data" in the GitLab instance can be correctly decrypted with the current secrets key.<br/>
  - This command can be copy-pasted directly only if GitLab is installed bare-metal on the machine. If you're using Docker, you'll need to find the Docker equivalent.<br/>
  - This command might sit there running for a whole hour without moving, so if it's not a very big upgrade, you can actually skip it.<br/>
<br/>
## Upgrade After Upgrade<br/>
<br/>
Usually, if you haven't upgraded in a long time, the upgrade path will be so long that a single typhoon day off won't be enough to finish it. When that happens, you'll need two typhoon days off! (X)<br/>
<br/>
Usually after finishing one upgrade, you'll be eager to start the next one. But before moving on to the next step in the path, I recommend opening one important interface first and taking a look:<br/>
<br/>
https://[domain]/admin/background_migrations<br/>
<br/>
This interface is the migration progress page for GitLab's internal database.<br/>
<br/>
If you're lucky, this page will be completely empty; if you're unlucky, this page will have a pile of migrations that still won't be done even after you come back from lunch.<br/>
<br/>
As a patient engineer, what you usually need to do is wait for this pile of migrations to finish before proceeding to the next step. After all, no one wants to come back from a typhoon day off to find GitLab's internal database in a total mess.<br/>
<br/>
## The Migration That Never Moves<br/>
<br/>
When you come back from lunch and happily open the migration page, you see it still hasn't finished. Not only is it not finished, but there's a `RemoveOldJobTokens: p_ci_builds` sitting frozen at 0.00%. You go take the CKA exam and come back, and it still hasn't budged.<br/>
<br/>
As an impatient engineer, you're bound to instinctively notice that something is off. At this point you dig into it, and then you discover that it's just waiting for the system to be idle before it will run. What the heck—a typhoon day is exactly when you're at your most idle. Are you trying to be a salaried slacker of a system too?<br/>
<br/>
At this point you need:<br/>
<br/>
`sudo gitlab-rake gitlab:background_migrations:finalize[RemoveOldJobTokens,p_ci_builds,id,'[]']`<br/>
<br/>
to force it to run.<br/>
