---
description: Open a saved ReelGenie post, check it, and choose where and when it goes out
argument-hint: "[post title or link]"
---

Help the person check a saved ReelGenie post and decide where and when it goes out.

Post, if given: $ARGUMENTS

With no post named, call `list_finished_posts` and offer the newest one that is waiting for review. Show its title, caption and review link, then follow the "Publish or schedule only with explicit approval" section of the `reelgenie` skill. Nothing is sent until the person approves the exact accounts and time.
