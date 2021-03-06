---
title: Wiki.js
description: 
published: true
date: 2022-03-03T22:36:33.154Z
tags: 
editor: markdown
dateCreated: 2022-03-03T00:12:35.283Z
---

# Wiki.js

Wiki.js is currently used as the Avionics Wiki. It can be accessed at https://avwiki.uorocketry.ca

## SSH Backup

Every 5 minutes, the wiki does a backup to https://github.com/uorocketry/wiki. Wiki.js is configured to do a bidirectional sync, so any changes made on Git will also affect the wiki. Most of the time, changes should be made directly in the wiki. Making changes in Git should be reserved only for massive changes, such as folder renames or mass modifications.

## Search Engine

A local Elasticsearch instance is used as the search engine. It provides slightly better search than the Postgres engine. However, its memory usage is significantly higher, so we could switch back to Postgres if we need more RAM in the future.