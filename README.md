# cc-opus-4-7-quickstart

> **Temporary skill — install, run once, then delete.** This is a guided setup, not ongoing automation. Once your Opus 4.7 setup is tuned, the skill has done its job and you can remove the folder.

A Claude Code skill that walks your agent through Boris Cherny's six recommendations for getting the most out of Claude Opus 4.7.

Boris is the PM for Claude Code. His thread covered:

1. **Opus 4.7** — adaptive thinking (tune *effort*, not thinking budgets)
2. **`/fewer-permission-prompts`** — scans session history and recommends allowlist additions
3. **Recaps** — short "what happened / what's next" summaries when returning to long sessions
4. **Focus mode (`/focus`)** — hide intermediate work, see only the result
5. **Effort level** — low for speed, high for hard problems
6. **Verification** — give Claude a way to check its own work (servers, Chromium extension, computer use, `/go` skill)

When invoked, the skill walks you through the list, asks which items you want to set up, and tailors verification setup (backend dev command, frontend Chromium extension, or desktop computer use) to your actual stack.

## Install

Drop the `cc-opus-4-7-quickstart/` folder into one of:

- `~/.claude/skills/` — available in every project
- `.claude/skills/` in a specific project — scoped to that project

Or give your agent this prompt:

> Install the cc-opus-4-7-quickstart skill from https://github.com/deepdive-ai/cc-opus-4-7-quickstart into my `~/.claude/skills/` folder.

## Triggering

The skill fires on phrases like:

- "set up Opus 4.7"
- "tune Claude Code"
- "optimize my setup"
- "reduce permission prompts"
- or any mention of focus mode, recaps, effort level, `/go`, `/simplify`, verification

## After you've used it

Delete the `cc-opus-4-7-quickstart/` folder from your skills directory. The setup tips are now reflected in your Claude Code config — you don't need the skill firing on every "tune my setup"-adjacent phrase forever.

## Related

- [claude-go-skill](https://github.com/deepdive-ai/-go) — the `/go` ship-it skill built during setup

## License

MIT. Use it, fork it, ship it.
