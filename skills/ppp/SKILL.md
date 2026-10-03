---
name: ppp
description: End-of-day Progress, Problems, Plans across work, health, and personal. Blocks on meeting outcomes left uncaptured for more than 24 hours. Triggers on /ppp, "PPP", "end of day".
---

Generate an end-of-day Progress, Problems, Plans summary across work, health, and personal.

## Step 0: Uncaptured outcomes (resolve before writing the PPP)

Read the People Pulse in `state/current.md` and the person files touched in the last few days. Find every meeting that happened with no captured outcome.

If any is older than 24 hours, do not write the PPP until it is handled. For each one, show: person, meeting date, days since, what is recorded now. Ask: "What happened? Anything decided or committed?" Then take one action:

- **Capture now.** The user gives the recap. Run the /capture flow inline.
- **Mark as owed.** The user cannot recall or wants to defer. Record "Outcome owed: {specific question}" on the person's row. It stays visible in every brief until answered.
- **Close as low-signal.** A casual meeting with nothing to capture. Use sparingly. Never for a senior contact or an active deal.

This gate exists because open outcomes roll forward silently otherwise, and the system's read on that relationship goes stale.

## Step 1: Pull context

1. `state/current.md`
2. `decisions/commitments.md` for anything due today or this week
3. Today's saved morning brief in `reports/`, if one exists: compare the stack against what happened
4. Anything captured or updated in this session

Ask the user what happened today if it is not already clear.

## Step 2: Present

```
PPP: {Day, Date}

Progress
What moved today. Facts only: deals advanced, commitments met, workouts done, conversations had.

Problems
What is stuck, drifting, or behind, across work, health, and personal. If something was on today's stack and did not happen, name it.

Plans
What has to happen tomorrow and this week. Name the action, the person or goal it ties to, and when.
```

Then list anything that should change in `state/current.md`, and ask whether to run /done.
