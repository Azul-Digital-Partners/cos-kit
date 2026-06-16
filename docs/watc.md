# The WATC Architecture

**Workflows, Agents, Tools, Context.**

Most AI projects ask the model to do all four jobs at once — remember the situation, decide the steps, execute them, and produce the result — inside a single prompt. The fix isn't a better model. It's separating the layers so each one does the job it's actually built for.

## The four layers, top to bottom

### Context (Layer 0 — the substrate)

Persistent state the agent reads before it does anything. This is the difference between an agent that asks "what's going on?" every session and one that already knows.

- `state/current.md` — the rolling snapshot. What's active, what's flagged, what's been decided recently.
- `state/last-session.md` — what happened in the last session and what was left open.
- `context/`, `life/`, `people/`, `decisions/` — durable identity, goals, relationships, and history.

**Context is loaded at session start and updated after every material change.** If something material happens and doesn't land in state, it's invisible to the next session.

### Workflows (Layer 1 — the instructions)

Plain-language SOPs in `workflows/`. Each one names the objective, the inputs it needs, the tools it calls, the outputs it produces, and how to handle edge cases. Written the way you'd brief a colleague.

Workflows evolve. When the agent learns something new — a rate limit, a better API, a recurring failure mode — the workflow gets updated. The workflow is the institutional memory of how work gets done.

### Agents (Layer 2 — the decision-maker)

This is the LLM. Its job is coordination, not execution. The agent reads context, picks the right workflow, runs tools in the right sequence, handles failures, asks clarifying questions when needed.

The agent is not trying to be a database, a script runner, or a search engine. It's making judgment calls — what to do, when, and what to escalate.

### Tools (Layer 3 — the execution)

Scripts in `tools/`. Python, shell, whatever. They make API calls, transform data, write files, query databases. Deterministic, testable, fast.

If something can be done by a script, do it in a script. Reserve the model for the parts that actually need judgment.

## Why separate them

A simple example. You want a morning brief. The naive approach: ask the LLM to "give me a brief on what's going on."

What you get back is generic, often wrong, and never the same twice.

The WATC approach:
1. **Workflow** (`workflows/morning-brief.md`) says: read state/current.md, read this week's calendar via `tools/get_calendar_day.sh`, read inbox via `tools/read_outlook_mail.py`, cross-check open commitments, produce a brief with these sections.
2. **Tools** do the deterministic work — fetching calendar, fetching inbox, with auth and pagination handled correctly.
3. **Context** (state files, people files, commitments) gives the LLM everything it needs to know without re-asking.
4. **Agent** synthesizes — what's on the calendar, what's overdue, what changed in the inbox, what's drifting on the watch list — into a brief that's *yours*, not generic.

Each layer does what it's good at. The result is consistent across sessions, hard to drift, easy to debug.

## The compounding accuracy problem

The reason this matters: when the LLM tries to do every step directly, errors compound.

- 1 step at 90% accuracy → 90% success.
- 5 steps at 90% accuracy → 59% success.
- 10 steps at 90% accuracy → 35% success.

Move every step you can to deterministic tools (which run at 100% when wired correctly), and the only thing the agent has to get right is *which* tool to run and *what* to do with the output. Accuracy stays high because the chain stays short.

## State-based execution

WATC also solves the *across-sessions* reliability problem. Each session has the previous one's output as input. The agent's behavior is a function of:

```
behavior = f(current_input, accumulated_state)
```

Not:

```
behavior = f(current_input)
```

This is why the agent feels continuous instead of starting from zero every session. It already knows what was decided last time, what's still open, and what you flagged as drifting. You don't have to restate the situation.

## How this kit uses WATC

- `CLAUDE.md` — the foundation rules. The WATC architecture itself.
- `Build-CoS.md` — a workflow that scaffolds a Chief of Staff: context files, state files, people files, decision logs, and a CoS-specific `CLAUDE.md` that imports the foundation.
- After setup, your `tools/` directory starts empty. Add tools as you wire integrations. Add workflows as recurring patterns emerge.

The goal is for *your* Chief of Staff to look like *your* operating system — the four layers in place, the substance fitted to you.

## Read next

- [`4cs.md`](4cs.md) — the lens you use to design new agents and skills.
- [`why-not-an-assistant.md`](why-not-an-assistant.md) — the identity that keeps the Chief of Staff from drifting back into "what task can I do for you."
- [`after-setup.md`](after-setup.md) — what to do in your first week with your CoS.
