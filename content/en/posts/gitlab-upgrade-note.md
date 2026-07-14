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
<!-- introduction -->
<!--more-->
<!-- rest of the content -->
## TL;DR

Upgrading GitLab is nothing but hard, thankless labor. I like to do it during a typhoon day off, because you can't go out anyway, and no one else is working. So if I accidentally shut GitLab down, there's no pressure.

This note is so that the next time a typhoon day off rolls around and I need to upgrade GitLab, I can revisit all the potholes and scars I ran into.

## Backups

Upgrades always carry risk—a system upgrade can pay off or backfire. Before upgrading, make a proper backup and read the Change Log carefully.

## Finding the GitLab Upgrade Path

If you upgrade GitLab by following a specific sequence of version numbers step by step, you can guarantee that the database migrations go smoothly. So check out this:

https://gitlab-com.gitlab.io/support/toolbox/upgrade-path

The GitLab upgrade path lookup site is extremely important.

With this upgrade path lookup site, you're already halfway to success!

## Verifying Status After the Upgrade

There are three things to check:

1. Is the site alive?
  - Usually after the upgrade GitLab restarts, and the site stays in the "starting up" state for a while. So if you see a 502, don't panic, don't rush, don't be afraid. If you go grab breakfast and it's still not up when you get back, then you can start to worry.
2. `sudo gitlab-rake gitlab:check`
  - The status of GitLab's other components.
  - This command can be copy-pasted directly only if GitLab is installed bare-metal on the machine. If you're using Docker, you'll need to find the Docker equivalent.
3. `sudo gitlab-rake gitlab:doctor:secrets`
  - Checks whether the "encrypted data" in the GitLab instance can be correctly decrypted with the current secrets key.
  - This command can be copy-pasted directly only if GitLab is installed bare-metal on the machine. If you're using Docker, you'll need to find the Docker equivalent.
  - This command might sit there running for a whole hour without moving, so if it's not a very big upgrade, you can actually skip it.

## Upgrade After Upgrade

Usually, if you haven't upgraded in a long time, the upgrade path will be so long that a single typhoon day off won't be enough to finish it. When that happens, you'll need two typhoon days off! (X)

Usually after finishing one upgrade, you'll be eager to start the next one. But before moving on to the next step in the path, I recommend opening one important interface first and taking a look:

https://[domain]/admin/background_migrations

This interface is the migration progress page for GitLab's internal database.

If you're lucky, this page will be completely empty; if you're unlucky, this page will have a pile of migrations that still won't be done even after you come back from lunch.

As a patient engineer, what you usually need to do is wait for this pile of migrations to finish before proceeding to the next step. After all, no one wants to come back from a typhoon day off to find GitLab's internal database in a total mess.

## The Migration That Never Moves

When you come back from lunch and happily open the migration page, you see it still hasn't finished. Not only is it not finished, but there's a `RemoveOldJobTokens: p_ci_builds` sitting frozen at 0.00%. You go take the CKA exam and come back, and it still hasn't budged.

As an impatient engineer, you're bound to instinctively notice that something is off. At this point you dig into it, and then you discover that it's just waiting for the system to be idle before it will run. What the heck—a typhoon day is exactly when you're at your most idle. Are you trying to be a salaried slacker of a system too?

At this point you need:

`sudo gitlab-rake gitlab:background_migrations:finalize[RemoveOldJobTokens,p_ci_builds,id,'[]']`

to force it to run.
