---
name: get-started
description: Start here when someone is new to ReelGenie. Use when they just connected or installed ReelGenie, say "get started", "set up ReelGenie", "I'm new" or "what now", ask what ReelGenie can do, or want to make their first post. Checks which TikTok, Instagram or YouTube accounts are connected and whether any posts are saved, says where they are in two or three plain sentences, and offers one next step.
---
Use this as the first stop for a new person. Keep it short: check, say where they are, offer one next step, then hand off. Use this plugin's bundled ReelGenie connection. If ReelGenie does not answer, see "If ReelGenie is not answering" at the end, then come back here.

## 1. Check

1. Call `list_connected_accounts`. Read `workspaces`: each has `account_group_id`, a name and its `accounts` (platform and whether it is active). Keep `connect_url` when it is returned; it comes back only when a workspace has no active account.
2. Call `list_finished_posts` for the workspace you will use, passing its `account_group_id`. An empty `posts` with no `next_cursor` means no posts yet. With several workspaces, use the one that has an active account, or check each one.

Report only what the tools returned. If a call fails, say so and stop; do not guess.

When `list_connected_accounts` returns `setup_guide`, those are the server's current first steps for this person. Follow them where they differ from sections 3 and 4 below; the server's copy is the newer one.

## 2. Say where they are

Two or three plain sentences, for example: "ReelGenie is connected. No TikTok, Instagram or YouTube account yet, and no posts yet." Name the connected accounts when there are some. If they asked what ReelGenie does: it keeps the finished images or video made in this chat as posts they can check, then sends them to TikTok, Instagram or YouTube after they approve. Claude's own tools make the media; ReelGenie does not. Only those three platforms.

## 3. Offer one next step

Pick the first that fits and offer only that one, as a question the person can answer with yes:

- **No posts yet:** offer to make a first post and save it for them to check now, the quick way described in section 4. Saving works without a connected account. Then give `connect_url` as the step that lets it be sent, with: "Instagram only connects professional accounts (Business or Creator); you can switch in the Instagram app. YouTube needs a YouTube channel on the Google account you choose."
- **Posts but no active account:** lead with `connect_url` and the same sentence, and ask them to tell you when it is done. Then call `list_connected_accounts` again.
- **Posts and an account:** offer the most useful one of these: check a post that is waiting (`status` `READY_FOR_REVIEW`) and choose when it goes out; or, when posts are already out, see how recent ones did; otherwise make the next post.

Do not list every feature, and do not ask them to pick a workspace or name a skill.

## 4. A first post, the quick way

The aim is one saved post within a few minutes, so the person sees ReelGenie work before any setup questions. For this first post only:

1. Ask one question: what the post is about. Skip it if they already said.
2. Do not ask for the profile's missing fields and do not offer several directions to choose from. Read the workspace profile and use what it already holds.
3. Call `create_slide_post` with 3 to 5 slides: a `hook`, two or three `points` slides and a `closing`, plus a title, a caption and a few hashtags. If the person brought finished files, save those instead.
4. Read it back with `get_finished_post` and give the person its `review_url`.
5. Close the loop in two sentences, then offer one next step: "Your first post is saved in ReelGenie. Nothing is posted until you approve it." Say it is a quick sample they can change or replace. With no account connected, the next step is the `connect_url`; otherwise it is choosing when the post goes out.

If the person asks for something specific (their own design, a reference post, a video, a particular look), do that instead. Their brief always comes first. The fuller questions about audience and goals belong to the second post, not the first.

## 5. Remind them once

"Nothing is posted until you approve it. Claude asks permission the first time it uses ReelGenie. Choose Always allow and it won't ask each time." Never promise views, followers or growth.

## 6. Hand off

When they say yes, do the work as ../reelgenie/SKILL.md describes rather than repeating its rules here: making and saving a post, checking a saved post, choosing accounts and a time, approving, and reading how recent posts did.

## If ReelGenie is not answering

Work out which of these it is, give the one step that fits, then check with `reelgenie_health`:

- **No ReelGenie tools at all:** the plugin is installed but not connected. Ask the person to run `/mcp`, choose `plugin:reelgenie:reelgenie` and sign in. The browser shows ReelGenie's consent page; they sign in and approve.
- **Tools ask for sign-in, or calls fail as unauthorized:** the sign-in has expired. Run `/mcp` and sign in again; nothing saved is lost.
- **Just connected, but the tools do not appear:** start a new Claude Code session so it reads the tool list again.
- **Claude asks permission before each ReelGenie call:** choosing Always allow stops it asking each time.
- **A tool answers with an error:** read the error to the person as it is. Do not guess a cause or retry a save blindly.
