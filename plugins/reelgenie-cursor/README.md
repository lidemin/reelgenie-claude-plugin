# ReelGenie for Cursor

Your agent makes the post; ReelGenie delivers it. Upload the exact images or video your agent created, get a faithful private preview, edit the caption, then schedule or publish to the TikTok, Instagram and YouTube accounts you connected in ReelGenie. Nothing is published until you approve that specific delivery.

ReelGenie does not generate images or video. Your agent or your own tools make the media; ReelGenie stores, previews and delivers it.

## Install

Install **ReelGenie** from the Cursor Marketplace (Customize → Plugins), then open Cursor Settings → **Tools & MCP**, find the ReelGenie server and click **Connect**. Your browser opens ReelGenie's consent page, which lists every permission before you connect. Sign in and approve.

To try it before it is listed, copy the `plugins/reelgenie-cursor` folder to `~/.cursor/plugins/local/reelgenie` and run **Developer: Reload Window**.

Connect your TikTok, Instagram or YouTube accounts on the **Accounts** page, https://reelgenie.app/app/accounts. Free plan: 30 posts a month, 1 brand, 3 connected accounts.

## What's included

- **MCP server** `https://reelgenie.app/api/mcp/agent` (shown as `plugin-reelgenie-reelgenie`): sign-in, uploads, review links, scheduling, publishing, delivery status and post performance.
- **Skill** `reelgenie`: how the agent makes finished slides, uploads them for private review, and asks for your approval before any delivery.

## Try it

- "Upload the three slides in ./out to ReelGenie with this caption and give me the review link."
- "Schedule that post to my TikTok account for tomorrow at 9am." (The agent asks you to confirm first.)
- "Did yesterday's post go out on every account?"

## What the plugin sends and where

The plugin runs no local code, hooks or scripts. It connects Cursor to one remote MCP server, `https://reelgenie.app/api/mcp/agent`, operated by ReelGenie. Sign-in uses OAuth through `https://auth.reelgenie.app`; no token is stored in plugin files.

When you ask the agent to save a post, it sends the post title, caption and the image or video files you choose to ReelGenie. Files upload to ReelGenie's Google Cloud Storage bucket, either directly through short-lived signed `storage.googleapis.com` URLs or, where that host is blocked, through ReelGenie's own upload address (`reelgenie.app/api/upload/...`). The MCP server issues both, and both are short-lived and private to that upload. ReelGenie sends a post to TikTok, Instagram or YouTube only after you approve that delivery. Performance reads return metrics ReelGenie already synced for your own posts.

Privacy policy: https://reelgenie.app/privacy · Terms: https://reelgenie.app/terms · Support: https://reelgenie.app/support
