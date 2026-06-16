# CoS Kit — A Chief of Staff for Claude Code

**Built and open-sourced by [Azul Digital](https://azuldigital.ai).**

This is not an AI assistant in the chatbot sense. It's a **Chief of Staff** that holds the full picture across your work, your health, and your family commitments. It briefs you before meetings, captures conversations after, closes open loops, and flags what's drifting before you notice.

Steven Christopher has been running a version of this on Claude Code for months. It's changed how he runs his work, his health, and his family. He wanted to give the foundation away.

## What you get

- **`CLAUDE.md`** — the WATC foundation rules (Workflows, Agents, Tools, Context) every Claude Code project benefits from.
- **`Build-CoS.md`** — a self-executing setup script. Claude reads it, interviews you for ~20 minutes, and writes your custom Chief of Staff.
- **`docs/`** — the methodology underneath: the WATC architecture, the 4Cs lens (Context, Connections, Capabilities, Cadence), why a Chief of Staff is not an assistant, and what to do after setup.

Personal and health goals compete on equal terms with work. A missed workout streak or a dropped family commitment surfaces with the same weight as a client deliverable. That is the point.

## Quick start

1. **Open Claude Code** on your machine in any empty folder.
2. **Drop `CLAUDE.md` and `Build-CoS.md`** into that folder.
3. **Tell Claude:**

   > Read `CLAUDE.md` first, then follow `Build-CoS.md` to set up my Chief of Staff.

It will preserve the foundation rules, then walk you through nine short interview sections — about you, your work, your goals, your people, your family, your health, and how you like to be talked to.

About 20–30 minutes total. At the end you have a working Chief of Staff customized to you, named whatever you want it named.

## A few things to know

- **The foundation is generic.** `CLAUDE.md` is the WATC architecture — useful across any Claude Code project, not Chief-of-Staff-specific. The setup script preserves it as the base layer and writes a CoS-specific `CLAUDE.md` on top.
- **It's stripped down.** No multi-agent orchestration, no web app, no client tracking, no email automation. Just the core operating system. You grow it from there.
- **It runs entirely on your machine.** Nothing leaves your laptop unless you wire integrations later.
- **After setup, your next session is:** open Claude Code in that folder, say hello, and your Chief of Staff picks up where you left off.

## What this is showcasing

This kit is the foundation of a much larger system we run at Azul Digital — a full digital workforce of specialized agents (engineering, marketing, finance, customer success), all coordinated through the same WATC architecture and the 4Cs lens.

If you want to see how the methodology scales beyond a personal CoS — or you want help wiring integrations (Notion, HubSpot, Outlook, Slack, etc.) into your Chief of Staff — **[book a call with Azul Digital](https://azuldigital.ai/contact)**. The give-away here is real and complete; the call is for when you want to go further.

## License

MIT. See [`LICENSE`](LICENSE). Use it, fork it, ship it, sell what you build on top of it.

## Credits

Built by **Steven Christopher** and the team at **Azul Digital**. Inspired by every founder, operator, and chief of staff who has tried to hold the whole picture in their head and discovered it doesn't fit.

If this helps you, we'd love to hear about it. Open an issue, tag `#azul-cos-kit` somewhere public, or just send a note.
