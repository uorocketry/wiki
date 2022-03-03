---
title: Wiki.js
description: 
published: true
date: 2022-03-03T00:23:25.009Z
tags: 
editor: markdown
dateCreated: 2022-03-03T00:12:35.283Z
---

# Wiki.js

Wiki.js is currently used as the Avionics Wiki. It can be accessed at https://avwiki.uorocketry.ca

## SSH Backup

Every 5 minutes, the wiki does a backup to https://github.com/uorocketry/wiki. While Wiki.js can be configured to a bidirectional sync, for now it only pushes to the repo, overriding any changes potentially made there.

> Wiki.js seems to have a bug with the bi-directional sync. For some reason, it seems to get stuck at past git commits from time to time, overriding changes made in the wiki since then. If it is desired to make any change using the Git repo (say because of a major change that is more easily done outside of Wiki.js) please change the setting back to push as soon as possible.
{.is-warning}