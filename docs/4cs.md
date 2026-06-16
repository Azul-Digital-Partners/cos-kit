# The 4Cs — Context, Connections, Capabilities, Cadence

The 4Cs are the lens we use at Azul Digital whenever we design a new agent or evaluate an existing one. Whenever you're about to add a skill, build an integration, or decide whether an agent is set up for the work in front of it, walk the 4Cs.

## Context

**What does the agent know before it starts?**

- Does it have a `state/current.md` that reflects what's actually happening?
- Are the relevant people, decisions, and commitments captured in files it will load?
- If a colleague walked into the room cold and read what the agent reads at session start, would they understand the situation?

Without context, the agent is episodic. With context, it's continuous.

**Common failure:** an agent that asks "what's going on?" at the start of every session. The fix is almost never a smarter agent. It's a better state file.

## Connections

**What can the agent reach?**

- Which systems does it have credentials for? (Notion, HubSpot, Outlook, Slack, Gmail, your bank, your CRM.)
- Which read paths are wired? Which write paths?
- Where does each piece of data actually live, and does the agent know which system is the source of truth?

Connections are about *integration topology* — what's plugged in, what isn't, and what the agent has to fake when something isn't wired.

**Common failure:** an agent that summarizes its inbox by re-asking you for the highlights. The fix is wiring the inbox read, not better prompting.

## Capabilities

**What can the agent do?**

- Which skills are defined under `.claude/skills/`? Each skill is a named capability — `/brief`, `/capture`, `/done`, `/ppp`.
- Which workflows are documented under `workflows/`? Each workflow is a repeatable execution path.
- Which tools are sitting in `tools/`? Each tool is a deterministic action the agent can compose.

Capabilities are the verbs the agent has access to. The bigger the verb set, the more leverage per session.

**Common failure:** the same multi-step workflow done from scratch every time. The fix is to name it, write the skill, and call it `/brief` from then on.

## Cadence

**When does the agent show up, and how often?**

- Is there a morning brief? A weekly review? An end-of-day capture?
- Are these triggered manually, on a schedule, by an event, or by Steven saying a phrase?
- Does the agent flag drift on its own (someone hasn't been contacted in three weeks) or only when asked?

Cadence is the *temporal contract* — the rhythms the agent enforces on the work and the rhythms the work enforces on the agent.

**Common failure:** an agent that's only useful when you remember to use it. The fix is naming the cadence — "every Friday at 4pm, run a weekly review and tell me what's drifting."

## How to use the 4Cs

When you're considering a change — a new skill, a new integration, a new agent entirely — write out the four columns:

| C | Today | After the change |
| --- | --- | --- |
| Context | What does it know now? | What will it know? |
| Connections | What can it reach now? | What will it reach? |
| Capabilities | What can it do now? | What will it do? |
| Cadence | When does it show up now? | When will it show up? |

If one column is empty in both rows, you've found a gap. If a column changes dramatically, you've found the substance of the change. If nothing changes, you've found a change that probably isn't worth making.

## The 4Cs vs. the WATC architecture

WATC is the *engineering pattern* — how the layers are structured. The 4Cs are the *evaluation lens* — how you decide what to build next.

WATC gives you reliability. The 4Cs give you direction.

You'll use both, often together. WATC tells you where the new skill or integration goes (tools/, workflows/, context/). The 4Cs tell you whether it's worth building in the first place.
