---
name: morning
description: Generate the morning brief. Reads state, priorities, commitments, and people files, then delivers a fixed-format brief with the scoreboard, today's three priorities, and flags. Triggers on /morning, "morning brief", "brief me on today".
---

Generate the morning brief. This is the operating plan for the day.

## Step 1: Pull before writing

Read all of these before writing a word of output:

1. `state/current.md` (the live snapshot)
2. `state/last-session.md` (what was left open)
3. `context/current-priorities.md` and `context/goals.md`
4. `decisions/commitments.md` (anything due today, this week, or overdue)
5. `decisions/open.md` (decisions waiting on the user)
6. `tasks.md` (This Week and Waiting On)
7. Every file under `people/` for its **Last contact**, **Cadence**, and **Senior contact** fields
8. Today's calendar, if a calendar tool is wired in `tools/`. If not, ask the user for today's meetings in one line and move on.
9. `life/health/goals.md` and `life/personal/context.md` for today's health commitments and protected family time

If a source is missing or stale, say so in FLAGS. Do not fill the gap with a guess.

## Step 2: Priority logic

Run these in order. The output feeds TODAY'S STACK and FLAGS.

1. **Goals.** Walk each cycle goal. What is due today, what weekly commitment is not yet done this week, what was missed yesterday. Prefix missed items with [MISSED].
2. **Commitments.** Anything the user owes that is due today or overdue.
3. **Senior-contact cadence.** For every person marked as a senior contact, compute days since last contact. Apply the escalation in `.claude/rules/cos-behavior.md` (day 21 flag, day 30 opens the brief, day 45 at risk).
4. **General drift.** Anyone past their expected cadence. Any goal area that has gone quiet.
5. **Returning items.** Anything deprioritized 7 or more days ago comes back, with its original day count.
6. **Uncaptured outcomes.** Any meeting in the last few days with no captured outcome. Surface it. Do not guess what happened.

## Step 3: Output

Deliver in this fixed structure. No preamble.

```
MORNING BRIEF: {Day, Date}

SCOREBOARD
{One line per scoreboard figure from state/current.md. Write UNKNOWN for any figure you cannot source. Never estimate.}

{Any day-30 senior-contact flag goes here, above everything else.}

HEADLINE
{One sentence: what matters most today and the top risk.}

ON TODAY
{Each meeting: time, who, what is at stake.}
{Protected personal commitments, as fixed constraints.}

TODAY'S STACK
1. {Highest priority: a specific action tied to a named person, deal, or goal}
2. {Second}
3. {Third}

FLAGS
{One line each: senior contacts past cadence with day counts, overdue commitments, drift, missed goals, uncaptured outcomes, returning deprioritized items.}

HEALTH
{Today's training, this week's count against target, any health flag.}

DECISIONS NEEDED
{Each: the decision, why today, what it unblocks.}
```

Stack rules:
- Exactly three items.
- Work, health, and personal compete for the same three slots.
- Fixed commitments (school pickup, a standing family dinner) are constraints, not stack items.

## Step 4: Deliver

1. Show the brief on screen first. Treat it as a draft.
2. Let the user react. Adjust if they correct anything.
3. Once agreed, save it to `reports/{YYYY-MM-DD}-morning-brief.md`.
4. Update `state/current.md` with anything the brief changed (new flags, the scoreboard values you used).

The next session that day reads this saved brief first.
