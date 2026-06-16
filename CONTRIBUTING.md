# Contributing to CoS Kit

Thanks for being here. This kit is small on purpose — most "improvements" are better made downstream in your own fork. But there are a handful of contributions we actively want.

## What we want

- **Bug reports.** The setup script breaks on edge cases — different OSes, different starting folder states, ambiguous user answers. If `Build-CoS.md` does something weird, open an issue with what happened and what you expected.
- **Doc clarifications.** If a section in `docs/` confuses you, a sentence somewhere is wrong, or a diagram doesn't render right on your platform — flag it.
- **Workflow examples.** If you wire an integration (Notion, HubSpot, Outlook, etc.) and want to share the workflow file as an example, we'd love a PR adding it under `docs/examples/`.
- **Better Mermaid diagrams.** If you can draw the WATC or 4Cs concepts more clearly, send a PR.

## What we don't want (in this repo)

- **Feature creep.** Multi-agent orchestration, web UI, hosted versions — these belong in your own fork or in a separate project. The give-away kit stays focused on "personal CoS in Claude Code, set up in 30 minutes."
- **Pre-wired integrations.** Same reason. The kit teaches the WATC pattern; specific integrations live in your fork.
- **Renamed branding.** Forks can be branded anything you like. The upstream stays "Azul Digital" branded — that's the lead-gen mechanic that funds the give-away.

## How to contribute

1. **Open an issue first** for anything non-trivial. We'd rather discuss before you spend time on a PR that's out of scope.
2. **Keep PRs small.** One change per PR. Easier to review, easier to land.
3. **Match the voice.** Plain, direct, no AI-template patterns ("In conclusion…", "Furthermore…"). If you're unsure, copy the cadence from existing docs.
4. **Test the setup.** If you touched `Build-CoS.md` or `CLAUDE.md`, run the setup end-to-end against an empty folder and confirm it still produces a clean CoS.

## Code of conduct

Be a decent person. Disagree with ideas, not people. The maintainers reserve the right to lock or hide any thread that crosses the line.

## Maintainers

[@stevenchristopher](https://github.com/stevenchristopher) and the team at [Azul Digital](https://goazuldigital.com).
