# Changelog

Versions of the Claude Code plugin in `plugins/reelgenie`.

## Unreleased

- Root README: says a free ReelGenie account is needed, how saving, approval and publishing work, a first message to try, and lists the `get-started` skill and the three commands.
- Skills added without the plugin (for example with `npx skills add`): the `reelgenie` and `get-started` skills no longer say the server is always there. They now give the step to add `https://reelgenie.app/api/mcp/agent` in the agent's MCP settings and sign in. No change to tools, permissions or approval.

## 1.0.8 (16 November 2026)

Fixes from a hand test of 1.0.7 with a fresh chat.

- Signed out: the main skill and the three commands now say the plugin is not signed in and give the `/mcp` step. Before, a first message such as "make my first post" could point to claude.ai connector settings instead.
- Quick first post: Claude leaves `style` out so the default colours are used, unless the workspace has brand colours. In the test its own colour choice was refused for low contrast and it had to retry.
- Updating: the README and the skill give the two commands to update a plugin installed from GitHub, which does not update itself.
- Skill revision `2026-11-16.3`. The Cursor plugin is unchanged. No change to tools, permissions or approval.

## 1.0.7 (16 November 2026)

Gets a new person to a first saved post faster.

- A first post, the quick way: for the first post in a workspace, Claude asks one question (what it is about), makes 3 to 5 slides with `create_slide_post`, saves them for review and shares the link. The questions about audience and goals, and the choice between directions, wait for the second post. A person who asks for something specific gets that instead.
- After the first save, Claude says what happened in two sentences and offers one next step: connect an account, or choose when the post goes out.
- Three commands: `/reelgenie:first-post`, `/reelgenie:review-post` and `/reelgenie:results`.
- `get-started` has short steps for when ReelGenie is not answering: not connected, sign-in expired, tools not showing, permission prompts, a tool error.
- Both skills follow `setup_guide` from `list_connected_accounts` when the server returns it, so first-step wording can change without a plugin release.
- Skill revision `2026-11-16.2`.
- The Cursor plugin is unchanged.
- No change to tools, permissions or approval: saving never publishes, and a person approves each delivery to TikTok, Instagram or YouTube. The plugin still runs no local code.

## 1.0.6 (16 November 2026)

Makes the first few minutes easier for someone new.

- New `get-started` skill: Claude checks which TikTok, Instagram or YouTube accounts are connected and whether any posts are saved, says where you are in two or three sentences, and offers one next step.
- A first post comes before connecting an account: Claude offers to make and save a post for review straight away, then gives the link to connect an account so it can be sent. Saving has always worked without an account; the skill now says to lead with it.
- Claude tells you once that choosing **Always allow** on its permission prompt stops it asking each time it uses ReelGenie.
- The main skill matches the server's current start-up steps. Skill revision `2026-11-16.1`.
- README: a first message to try after sign-in.
- The Cursor plugin is unchanged.
- No change to tools, permissions or approval: saving never publishes, and a person approves each delivery to TikTok, Instagram or YouTube.

## 1.0.5 (11 November 2026)

Brings the plugin skill up to date with the published ReelGenie skill, revision `2026-11-11.7`.

- Uploads work where `storage.googleapis.com` is blocked: the upload tools also return a `reelgenie_upload_url`. Claude PUTs an image there as one file, and a video in 8 MiB parts with `Content-Range` (a `dd` + `curl` loop), then finalizes as usual.
- Claude desktop and claude.ai: uploads go from the code sandbox, which blocks `reelgenie.app` until the user adds it in Settings → Capabilities → Create and edit files → Allowed websites → Manage, with Use the internet while making files on (on Team or Enterprise, an owner allows it in Organization settings → Capabilities), then starts a new chat. Adding the connector does not allow that domain.
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
