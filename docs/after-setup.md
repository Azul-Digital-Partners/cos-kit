# After Setup — Your First Week with Your Chief of Staff

You ran `Build-CoS.md`, answered the interview, and now you have a working Chief of Staff. Here's how to break it in.

## Day 1 — Open a session and let it read

Open Claude Code in your CoS folder. Say:

> Hello.

That's it. Your CoS will read `state/current.md`, the foundation rules, the context files, and your life files. It should come back with a snapshot of where you are — top-of-mind priorities, anything flagged, what's on your calendar this week, who's drifting.

If it asks "what's going on?" or "what would you like to work on" — push back. Say:

> You're being an assistant. Read state/current.md and brief me on what's drifting.

That recalibrates the relationship.

## Day 2 — Capture your first conversation

Have a real conversation. Could be a client call, an internal sync, a coffee with a friend you've been meaning to catch up with. Then come back and say:

> Capture: I just talked to [Name]. [Recap in plain language.]

Your CoS will:
1. Update the person's file in `people/`.
2. Log any decisions made in `decisions/log.md`.
3. Update `decisions/commitments.md` if you committed to anything (or they did).
4. Cross-check open items from last time — and ask if anything unresolved was addressed.
5. Update `state/current.md` if anything material changed.

This is the loop that makes the CoS feel useful. Every captured conversation makes the next session sharper.

## Day 3 — Brief before a meeting

Before your next meeting with someone in your `people/` folder, say:

> Brief me on [Name].

You should get back:
- Who they are and why you're meeting.
- What success looks like walking out.
- The last conversation summary and what was left open.
- Open commitments — both directions.

If the file is thin, the brief will be thin. That's not a failure; that's a signal to capture more.

## Day 4 — End of day, run a PPP

At end of day, say:

> PPP.

(Progress, Problems, Plans.)

Your CoS will give you a short pass across work, health, and personal. What got done, what's stuck, what's next. This is also when state gets updated.

## Day 5 — Look at what's drifting

Say:

> What's drifting?

Your CoS will scan people files, commitments, and goals for anything past its expected cadence. Active clients you haven't touched in two weeks. Pipeline that's gone cold. Workouts that are off pace. A family commitment you haven't acted on.

Drift detection is the muscle most operators don't have. The CoS does.

## Through the week — Update as you go

Every meaningful decision: log it. Every captured conversation: update the person's file. Every shift in priority: update `current-priorities.md`. The CoS will only know what you tell it.

## End of week — Session close

When you're done for the week, say:

> Close out.

The CoS will write `state/last-session.md` and update `state/current.md`. Next Monday, when you open Claude Code and say hello, it will pick up exactly where you left off.

## Common adjustments

- **"It's too verbose."** Edit `.claude/rules/communication-style.md` to demand shorter responses. Or just tell it once: *"From now on, default to bullets, max 10 lines."*
- **"It missed something."** That's a state file gap. Either you didn't capture, or `state/current.md` is stale. Update the file.
- **"It's asking me things it should know."** Either the context file is wrong, or you're invoking the wrong skill. Look at what it read at session start and update.
- **"It feels generic."** Re-run the interview for one section that came out shallow. Or just hand-edit the context file. Your CoS is yours; edit freely.

## What to do once the muscle is there

After a couple weeks, you'll start to notice the recurring workflows. *Every Monday I do X. Every Friday I do Y. Before every client call I do Z.* That's when you write skills.

Drop a file in `.claude/skills/{skill-name}/SKILL.md` with a description, a trigger, and the steps. Now the CoS has a named verb for that workflow. The next time you'd normally do it from scratch, you just say `/skill-name`.

Skills are how the system gets sharper over time. Build them organically. Don't try to write twelve on day one.

## What this kit doesn't ship

By design, the give-away is the foundation. You won't find:

- Integrations to Notion / HubSpot / Outlook / Slack out of the box.
- Multi-agent orchestration.
- A web app.
- Email automation.
- Health tracker integrations.

All of those are wireable, and the WATC structure makes them straightforward. You write `tools/{integration}.py`, document it in a workflow, and the CoS can use it. Or — if you want help wiring them — [book a call with Azul Digital](https://azuldigital.ai/contact). We do this for a living.
