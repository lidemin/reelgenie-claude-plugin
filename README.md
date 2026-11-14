# ReelGenie for Claude Code

**Claude makes your social post. ReelGenie lets you review it, then schedules or publishes it to TikTok, Instagram and YouTube. Nothing is posted until you approve it.**

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![MCP Registry](https://img.shields.io/badge/MCP_Registry-app.reelgenie%2Freelgenie-green.svg)](https://registry.modelcontextprotocol.io/v0/servers/app.reelgenie%2Freelgenie/versions/latest)
[![Try it without signing up](https://img.shields.io/badge/try_it-no_sign--up-orange.svg)](https://reelgenie.app/try)

## Install

```bash
claude plugin marketplace add lidemin/reelgenie-claude-plugin
claude plugin install reelgenie@reelgenie
```

Restart Claude Code, type `/mcp`, choose **plugin:reelgenie:reelgenie** and sign in. You see which permissions you're granting before you connect. You sign in yourself in the browser; Claude never sees your password.

No account yet? [Sign up free](https://reelgenie.app/app/signup), or [try the review flow without signing up](https://reelgenie.app/try).

**Approval first.** Every post starts private. Saving a post for review never publishes it.

## What you can ask

Start with this one. Claude only reads your setup and tells you the next step; nothing is posted:

> Use ReelGenie to check my workspace and connected accounts, and tell me the next step.

Then, for example:

- "Make a 5-slide Instagram carousel about why our sourdough takes 36 hours, and save it to ReelGenie for review."
- "Upload `./out/launch.mp4` to ReelGenie as a YouTube video with this caption, and give me the review link."
- "Send that post to my TikTok inbox tomorrow at 9am Sydney time." Claude asks you to confirm the exact post, account and time first.
- "Did yesterday's post go out on every account?"
- "How did my last posts do compared with my usual?"

## How approval works

1. Claude saves the finished files and caption to ReelGenie and gives you a review link.
2. You check each slide or the video and the full caption, and fix anything in the conversation or in ReelGenie.
3. You choose the accounts, and either send now or pick a date, time and timezone.
4. You approve. Claude can send an approved post only if you allowed publishing when you signed in; you can always approve in ReelGenie instead.
5. You see the result for each account: **Scheduled**, **Draft ready** (TikTok needs your final step), **Published**, or **Failed** with the platform's reason.

## Platform limits

- **Instagram:** posts directly to eligible connected accounts.
- **TikTok photos:** for most accounts, the post goes to your TikTok inbox as a draft (JPEG or WebP, up to 1080 × 1920). Open TikTok to add music and finish publishing.
- **YouTube:** needs a finished video. Images can't go to YouTube.

ReelGenie doesn't generate images or video. Claude, or the tools you use with it, makes the media; ReelGenie stores the exact files, shows them as they will be sent, and delivers them.

## What's included

This repository holds two plugins for the same ReelGenie connection:

- [`plugins/reelgenie`](plugins/reelgenie): the Claude Code plugin. It adds:
  - the **MCP server** `https://reelgenie.app/api/mcp/agent`, for sign-in, uploads, review links, scheduling, publishing and post results;
  - the **skill** `reelgenie`, which tells Claude how to make finished posts, upload them for private review and ask for your approval before anything is sent.
- [`plugins/reelgenie-cursor`](plugins/reelgenie-cursor): the same connection and skill for Cursor. See its [README](plugins/reelgenie-cursor/README.md).

The plugin runs no local code, hooks or scripts. Only want the skill, or use another agent? See [lidemin/reelgenie-skills](https://github.com/lidemin/reelgenie-skills). ReelGenie also works with Codex, and a ChatGPT plugin is in private preview.

## Plans

- **Free:** $0, with 30 posts a month, 1 brand and 3 connected accounts. No card needed.
- **Paid plans** start at US$19 a month (Solo: unlimited posts, 2 brands, 10 connected accounts).

A carousel sent to several accounts counts as one post, and retries don't count again. Your Claude plan is separate. See [pricing](https://reelgenie.app/pricing).

## Links

- [Set up ReelGenie for Claude](https://reelgenie.app/claude)
- [Try it without signing up](https://reelgenie.app/try)
- [Step-by-step Claude Code guide](https://reelgenie.app/guides/claude-code-social-media-posts)
- [MCP Registry entry](https://registry.modelcontextprotocol.io/v0/servers/app.reelgenie%2Freelgenie/versions/latest)
- [Glama](https://glama.ai/mcp/connectors/app.reelgenie/reelgenie)
- [Privacy](https://reelgenie.app/privacy) · [Terms](https://reelgenie.app/terms) · [Support](https://reelgenie.app/support)

## License

[MIT](LICENSE)
