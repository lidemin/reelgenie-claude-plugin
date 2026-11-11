# Changelog

Versions of the Claude Code plugin in `plugins/reelgenie`.

## 1.0.5 (11 November 2026)

Brings the plugin skill up to date with the published ReelGenie skill, revision `2026-11-11.7`.

- Uploads work where `storage.googleapis.com` is blocked: the upload tools also return a `reelgenie_upload_url`. Claude PUTs an image there as one file, and a video in 8 MiB parts with `Content-Range` (a `dd` + `curl` loop), then finalizes as usual.
- Claude desktop and claude.ai: uploads go from the code sandbox, which blocks `reelgenie.app` until the user adds it under Settings → Capabilities → Code execution and file creation → Additional allowed domains (on Team or Enterprise, an owner does this), then starts a new chat. Adding the connector does not allow that domain.
- README data handling: uploads can also go through `reelgenie.app/api/upload/...`, not only signed `storage.googleapis.com` URLs.
- Instagram carousels and slide posts: 1 to 20 images or slides (was 1 to 10).
- Finished HeyGen, Canva or Higgsfield videos can be saved straight from the tool's download link with `create_finished_video_post`; only `files.heygen.ai`, `export-download.canva.com` and `d8j0ntlcm91z4.cloudfront.net` links are accepted.
- Connecting accounts: the console page is now **Accounts** (`https://reelgenie.app/app/accounts`). When no account is connected, `list_connected_accounts` returns `next_step` and `connect_url`; Claude gives the user that link. A post can be saved for review before any account is connected.
- Every save returns `post_id`, `review_url` and `next_step` (plus `connect_url` when no account is connected); Claude shares the review link and asks the user to approve.
- The skill mentions the short start-up instructions the server sends.
- The Cursor plugin skill gets the same changes and revision, with a plain "allow network access to `reelgenie.app`" step in place of the claude.ai settings; its README now points to the **Accounts** page. The Cursor plugin version is unchanged.
- No change to permissions or approval: saving never publishes, and a person approves each delivery to TikTok, Instagram or YouTube.

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
