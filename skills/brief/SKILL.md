---
name: brief
description: Generate a pre-meeting brief for the person or engagement named in the arguments. Triggers on /brief {name}, "brief me on {name}", "prep me for my call with {name}".
---

Generate a pre-meeting brief for the person or engagement named in the arguments.

## Steps

1. Find the person's file in `people/` (all subfolders) by name or company. If ambiguous, ask which one before proceeding.
2. Read the person's file completely.
3. Read `decisions/commitments.md` and pull every commitment tied to this person, both directions.
4. Read `decisions/open.md` and pull open decisions tied to this person or engagement.
5. If a related file exists in `projects/`, read it.
6. If an email or calendar tool is wired in `tools/`, check recent threads with this person. Search sent mail too, so you do not report as open something the user already sent.

## Output

```
{Person Name}, {Company}, {Date}

Who they are: one sentence on their role and what they care about.

Why this meeting: what prompted it, what the user is going in to get.

What success looks like: the outcome to walk out with.

Last conversation: where things stood, what was agreed.

Open commitments:
- You owe them:
- They owe you:

Open decisions: anything unresolved tied to this relationship.

Cadence: days since last contact. If this is a senior contact past 14 days, say so plainly.

Watch list: anything sensitive or worth being careful about.
```

Do not fabricate details. If the file is thin, say so and ask the user to fill in what matters before the meeting. A thin brief is a signal to capture more after this one.

After the meeting, remind the user to run /capture.
