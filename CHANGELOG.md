# Changelog

Versions of the Claude Code plugin in `plugins/reelgenie`.

## 1.0.4 (11 November 2026)

- The skill now describes the posting allowance as it works today: Free teams created from November 2026 have 30 posts per team per month, resetting on the 1st at 00:00 UTC; older Free teams keep 10 posts per UTC day; Solo, Team and Agency plans have unlimited posts. It points Claude to the `plan` and `publishing_allowance` that `list_reelgenie_workspaces` returns instead of assuming a daily limit.
- Plain wording: "URL variants" is now "URL versions" (also in the Cursor plugin skill).
- Skill revision `2026-11-11.1`. No change to tools, permissions or approval: saving never publishes, and a person approves each delivery to TikTok, Instagram or YouTube.

## 1.0.3 (9 November 2026)

- Brought the plugin skill up to date with the published ReelGenie skill.

## 1.0.2 (27 October 2026)

- Added the display name, support, docs and terms links.

## 1.0.1 (24 October 2026)

- Prepared the plugin for directory submission.

## 1.0.0 (23 October 2026)

- First release: the ReelGenie MCP server and the `reelgenie` skill.
