# ReelGenie for Claude Code

Claude makes the post. ReelGenie stores the exact files, shows a faithful preview, lets you edit captions, and schedules or publishes to your connected TikTok, Instagram and YouTube accounts. Nothing is published until you approve it.

## Install

```bash
claude plugin marketplace add lidemin/reelgenie-claude-plugin
claude plugin install reelgenie@reelgenie
```

Then run `/mcp`, choose **reelgenie** and sign in to ReelGenie. The consent screen lists every permission before you connect.

## What's included

- **MCP server** `https://reelgenie.app/api/mcp/agent`: sign-in, uploads, review links, scheduling, publishing and post performance.
- **Skill** `reelgenie`: how Claude makes finished slides, uploads them for private review, and asks for your approval before any delivery.

## What the plugin sends and where

The plugin runs no local code, hooks or scripts. It connects Claude to one remote MCP server, `https://reelgenie.app/api/mcp/agent`, operated by ReelGenie. Sign-in uses OAuth through `https://auth.reelgenie.app`; no token is stored in plugin files.

When you ask Claude to save a post, Claude sends the post title, caption and the image or video files you choose to ReelGenie. Files upload directly to ReelGenie's Google Cloud Storage bucket (`storage.googleapis.com`) through short-lived signed URLs that the MCP server issues. ReelGenie sends a post to TikTok, Instagram or YouTube only after you approve that delivery in the conversation. Performance reads return metrics ReelGenie already synced for your own posts.

Privacy policy: https://reelgenie.app/privacy

Setup guide: https://reelgenie.app/claude
