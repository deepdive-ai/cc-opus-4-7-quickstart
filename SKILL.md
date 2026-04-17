---
name: cc-opus-4-7-quickstart
description: One-time guided setup for Claude Opus 4.7 based on Boris Cherny's recommendations — permissions, recaps, focus mode, effort level, and verification loops. This is a TEMPORARY skill — once setup is done, recommend the user delete the skill folder. Use when the user asks to "set up Opus 4.7", "tune Claude Code", "optimize my setup", "make Claude faster", "reduce permission prompts", or mentions any of: focus mode, recaps, effort level, /go, /simplify, verification.
---

Opus 4.7 Quickstart
====================

> **Temporary onboarding skill.** This is a guide, not ongoing automation. After walking the user through the setup, remind them they can safely delete the `cc-opus-4-7-quickstart/` folder — it's done its job.

Boris Cherny's (Claude Code PM) six recommendations for getting the most out of Opus 4.7. When this skill is invoked, walk the user through the list, explain what each feature does, and offer to configure the ones that need configuring.

The six recommendations
-----------------------

### 1. Opus 4.7 itself

The default model. Adaptive thinking (no more thinking budgets — you tune _effort_ instead, see #5). Stronger on long-horizon work, tool use, and following verification loops.

### 2. `/fewer-permission-prompts` skill

Ships with Claude Code. Scans session history for safe bash/MCP commands that repeatedly hit permission prompts, then recommends entries to add to the allowlist.

*   **When to use:** especially valuable if the user is _not_ running auto mode.
*   **How to apply:** run `/fewer-permission-prompts` and accept the recommended additions to `.claude/settings.json` or `.claude/settings.local.json`.

### 3. Recaps

Short summaries of what an agent did and what's next, shown when returning to a long-running session. No setup — just know they exist so you use them instead of re-reading the whole transcript.

### 4. Focus mode (`/focus`)

Hides intermediate tool calls and shows only the final result. Trust-the-model UX.

*   **When to recommend:** users who trust 4.7 to pick the right commands/edits and only want to see the outcome.
*   **How to apply:** `/focus` toggles it on/off. No config file change needed.

### 5. Effort level

4.7 uses adaptive thinking. Tune with **effort** instead of thinking budgets.

*   **Lower effort** → faster responses, fewer tokens, good for routine work.
*   **Higher effort** → more intelligence, better for hard problems.
*   **How to apply:** configurable in CLI settings. Tell the user to pick per-task — don't set once and forget.

### 6. Give Claude a way to verify its work

The biggest multiplier. Always has been, more important with 4.7.

Verification looks different per task:

*   **Backend:** make sure Claude knows how to start the server/service and hit it end-to-end.
*   **Frontend:** install the **Claude Chromium extension** so Claude can drive the browser.
*   **Desktop apps:** use computer use.
*   **Long-running work:** verification is how you know the code still works when you come back.

Boris's personal pattern — prompts end in `/go`, a skill that:

1.  Tests end-to-end (bash / browser / computer use)
2.  Runs `/simplify`
3.  Opens a PR

How to run this skill
---------------------

When invoked, do the following:

1.  **Ask which ones the user wants to set up.** Present the six as a numbered list. Don't force all six — some (recaps, Opus 4.7 as default) are automatic.

2.  **For each selected item, do the setup:**

    *   **#2 (permissions):** offer to invoke `/fewer-permission-prompts` now. If the user isn't in an active session with history, tell them to run it after a day of normal use.
    *   **#4 (focus mode):** explain the `/focus` toggle. Nothing to configure.
    *   **#5 (effort):** ask what their typical workload looks like (quick edits vs hard debugging) and recommend a default effort level. Point them at the CLI setting.
    *   **#6 (verification):** ask what kind of work they mostly do (backend / frontend / desktop / mixed). Then:
        *   Backend → ask for the dev command (`npm run dev`, `go run`, etc.) and suggest saving it in `CLAUDE.md` so Claude always knows how to boot the service.
        *   Frontend → point them to the Claude Chromium extension and offer to walk through install.
        *   Desktop → explain computer use is the answer.
        *   Offer to build them a `/go` skill tailored to their stack (test command + `/simplify` + PR creation via `gh`).

3.  **Don't dump all six at once unless asked.** Walk them through one at a time — ask if they want to move on before continuing.

4.  **At the end, tell them to delete the skill.** Once they've worked through the items they care about, this skill has nothing left to do. Recommend removing the `cc-opus-4-7-quickstart/` folder from their skills directory so it doesn't keep firing on unrelated "tune my setup"-style prompts later.

Source
------

Boris Cherny, Claude Code PM, thread posted on X covering Opus 4.7 recommendations. Six numbered points: (1) Opus 4.7, (2) `/fewer-permission-prompts`, (3) recaps, (4) `/focus`, (5) effort level, (6) verification + `/go` pattern.
