# The 4Cs of AI Development

Four axes we use at Azul Digital to evaluate any AI system — the Chief of Staff included. When you're deciding whether to add a skill, wire an integration, or whether the agent is set up for the work in front of it, walk the 4Cs.

## Context

**What the AI knows about.**

Files it loads at session start. Notes you've captured. State of the work. People, projects, commitments, decisions. The frontier of what's in its head before you say a word.

Without context, every session starts cold. With context, the agent picks up where the last one left off.

**Common failure:** the agent asks "what's going on?" at the start of every session. The fix is almost never a smarter model. It's a better state file.

## Connections

**What live data it can reach without you giving it.**

The systems it has credentials for — calendar, email, files, CRM, the bank, the codebase. The reads and writes that are wired. The integrations it can pull from on its own instead of waiting for you to paste content in.

A Chief of Staff that can't see your calendar is asking you to do its job.

**Common failure:** the agent summarizes your inbox by asking you for the highlights. The fix is wiring the inbox read, not better prompting.

## Capabilities

**What it can produce — multistep artifacts from a short phrase.**

Skills, workflows, tools. The verbs the agent has access to. The difference between "I'll walk you through it" and "I shipped the draft, the calendar invite, and the brief — all from one phrase."

The bigger the verb set, the more leverage per session.

**Common failure:** the same multi-step workflow done from scratch every time. The fix is to name it, write the skill, and call it `/brief` from then on.

## Cadence

**When it acts on its own, while your laptop is closed.**

Cron jobs. Webhooks. Scheduled triggers. Anything that runs without you typing a prompt.

Most AI systems skip this axis. They only watch when you're watching. Cadence is the difference between an assistant you have to remember to ping and a Chief of Staff that pings you Friday at 4pm because the weekly review is overdue, or flags a stalled deal Sunday morning before Monday.

**Common failure:** an agent that's only useful when you remember to use it. The fix is naming the cadence.

## How to use the 4Cs

When you're considering a change — a new skill, a new integration, a new agent entirely — write out the four columns:

| C | Today | After the change |
| --- | --- | --- |
| Context | What does it know now? | What will it know? |
| Connections | What live data can it reach now? | What will it reach? |
| Capabilities | What artifacts can it produce now? | What will it produce? |
| Cadence | When does it run on its own now? | When will it run? |

If a column is empty in both rows, you've found a gap. If a column changes dramatically, you've found the substance of the change. If nothing changes, you've found a change that probably isn't worth making.

## The 4Cs vs. the WATC architecture

WATC is the engineering pattern — how the layers are structured. The 4Cs are the evaluation lens — how you decide what to build next.

WATC gives you reliability. The 4Cs give you direction.

You'll use both, often together. WATC tells you where the new skill or integration goes (`tools/`, `workflows/`, `state/`). The 4Cs tell you whether it's worth building.
