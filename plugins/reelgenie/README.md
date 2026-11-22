# ReelGenie for Claude Code

Claude makes the post. ReelGenie stores the exact files, shows a faithful preview, lets you edit captions, and schedules or publishes to your connected TikTok, Instagram and YouTube accounts. Nothing is published until you approve it.

## Install

```bash
claude plugin marketplace add lidemin/reelgenie-claude-plugin
claude plugin install reelgenie@reelgenie
```

Then run `/mcp`, choose **reelgenie** and sign in to ReelGenie. The consent screen lists every permission before you connect.

After that, ask Claude: "Use ReelGenie: make my first post and save it for me to review, then show my connected accounts. If you can't see ReelGenie tools, tell me to run /mcp, choose ReelGenie and sign in, then I'll send this again." Saving works before you connect TikTok, Instagram or YouTube; an account is needed only to send the post. Claude asks permission the first time it uses ReelGenie. Choose **Always allow** and it won't ask each time.

## Update

A plugin installed from GitHub does not update itself. To get the latest version:

```bash
claude plugin marketplace update reelgenie
claude plugin update reelgenie@reelgenie
```

Then restart Claude Code. `claude plugin list` shows the version you have; the newest is at the top of the [changelog](../../CHANGELOG.md).

## What's included

- **MCP server** `https://reelgenie.app/api/mcp/agent`: sign-in, uploads, review links, scheduling, publishing and post performance.
- **Skill** `get-started`: a short first step. Claude checks which accounts are connected and whether any posts are saved, says where you are, and offers one next step.
- **Commands** `/reelgenie:first-post`, `/reelgenie:review-post` and `/reelgenie:results`: shortcuts for a first post, checking a saved post, and seeing how recent posts did.
- **Skill** `reelgenie`: how Claude makes finished slides, uploads them for private review, and asks for your approval before any delivery.

## What the plugin sends and where

The plugin runs no local code, hooks or scripts. It connects Claude to one remote MCP server, `https://reelgenie.app/api/mcp/agent`, operated by ReelGenie. Sign-in uses OAuth through `https://auth.reelgenie.app`; no token is stored in plugin files.

When you ask Claude to save a post, Claude sends the post title, caption and the image or video files you choose to ReelGenie. Files upload to ReelGenie's Google Cloud Storage bucket, either directly through short-lived signed `storage.googleapis.com` URLs or, where that host is blocked, through ReelGenie's own upload address (`reelgenie.app/api/upload/...`). The MCP server issues both, and both are short-lived and private to that upload. ReelGenie sends a post to TikTok, Instagram or YouTube only after you approve that delivery in the conversation. Performance reads return metrics ReelGenie already synced for your own posts.

Privacy policy: https://reelgenie.app/privacy

Setup guide: https://reelgenie.app/claude
