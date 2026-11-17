# ReelGenie plugins for Claude Code and Cursor

ReelGenie (reelgenie.app) holds your AI agent's finished posts until you approve, then publishes to TikTok, Instagram and YouTube.

| | |
|---|---|
| What it is | Hosted MCP server: `https://reelgenie.app/api/mcp/agent` (OAuth sign-in, no API key) |
| Platforms | TikTok, Instagram, YouTube |
| Approval | A person approves every post, on every plan. Saving a post never sends it. |
| After sending | A result for each account, then views and likes per account |
| Does not do | Generate images or video; other platforms; self-hosting |
| Price | Free: 30 posts a month, 1 brand, 3 connected accounts. Paid from US$19/month |
| Also listed | Claude connector directory; MCP Registry `app.reelgenie/reelgenie` |

This repository holds two plugins for the same ReelGenie MCP server:

- `plugins/reelgenie`: the Claude Code plugin (listed by `.claude-plugin/marketplace.json`).
- `plugins/reelgenie-cursor`: the Cursor plugin (listed by `.cursor-plugin/marketplace.json`). See its [README](plugins/reelgenie-cursor/README.md).

## Claude Code

Claude makes the post. ReelGenie stores the exact files, shows a faithful preview, lets you edit captions, and schedules or publishes to your connected TikTok, Instagram and YouTube accounts. Nothing is published until you approve it.

### Install

```bash
claude plugin marketplace add lidemin/reelgenie-claude-plugin
claude plugin install reelgenie@reelgenie
```

Then run `/mcp`, choose **reelgenie** and sign in to ReelGenie. The consent screen lists every permission before you connect.

### What's included

- **MCP server** `https://reelgenie.app/api/mcp/agent`: sign-in, uploads, review links, scheduling, publishing and post performance.
- **Skill** `reelgenie`: how Claude makes finished slides, uploads them for private review, and asks for your approval before any delivery.

Setup guide: https://reelgenie.app/claude
