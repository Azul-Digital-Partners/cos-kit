---
name: done
description: Close out this session. Writes state/last-session.md and updates only the parts of state/current.md this session changed. Triggers on /done, "close out", "wrap up", "end session".
---

Close out **this session**. Nothing else.

Scope rule: write only what this session produced. Do not review the whole day (that is /ppp). Do not regenerate state tables this session never touched.

## 1. Write `state/last-session.md`

Use the shape in `templates/session-summary.md`:
- What this session covered
- What was captured or updated, by file
- Decisions made or logged
- Commitments added or closed
- Open items handed to the next session, with dates where they exist

## 2. Update `state/current.md`, only what changed

- Change the date at the top to today
- Add or resolve Open Decisions raised this session
- Add or clear Commitments at Risk raised this session
- Update People Pulse rows for anyone contacted or discussed this session
- Update the Scoreboard only if this session produced a new sourced number
- Update Health or Personal only if this session produced new information

If a section did not change this session, leave it alone. Stale data rewritten with today's date is worse than no update.

## 3. Check for expired overrides

Scan `state/current.md` and `.claude/rules/` for temporary rules or banners ("paused until", "ignore X for now"). If one has passed its expiry date, or has no expiry date, list it for the user to keep, renew, or remove.

## 4. Confirm

One sentence: what is open going into the next session.

A session without /done means the next session starts blind.
