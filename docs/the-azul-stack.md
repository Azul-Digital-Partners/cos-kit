# What Azul Built On Top Of This

The kit in this repo is the foundation. What follows is the production stack we run at Azul Digital — the same WATC architecture and 4Cs lens, extended into a working digital workforce.

We're putting it here so you can see what scales beyond a personal Chief of Staff before you decide whether you want help building toward it.

## The leadership team

Ten specialized agents, each running on the WATC foundation in this kit, each with their own state files, scope, and authority:

- **Rosalind** — Chief of Staff. The agent in this give-away. Holds the full picture.
- **CEO** — Strategy, agent governance, financial authority, escalation endpoint.
- **CTO** — Engineering direction, architecture decisions, technical roadmap.
- **CFO** — Financial modeling, bookkeeping, services P&L, valuation work.
- **CIO** — Infrastructure, tooling, internal platform.
- **Head of Marketing** — SEO content, copywriting, brand voice, CRO.
- **Head of Product** — Roadmap, feature specs, user research.
- **Agent Ops** — Spins up new agents, owns workforce configuration.
- **Engagement PM** — Per-client services delivery, SOW enforcement.
- **Sales Ops** — Pipeline, follow-ups, prospect research.

Each one has the same shape: `state/current.md`, `state/last-session.md`, scope, authority matrix, workflows, skills, integrations. The CoS kit you can download teaches one of these. The other nine are variations on the same pattern, fitted to their domain.

## The control plane: Paperclip

Every piece of work the agents do flows through **Paperclip**, our internal issue tracker. Think of it as Linear + Sentry built for agents. Each agent works against tracked issues with status, comments, planning documents, execution runs, and board approval gates. The board (Steven) reviews and approves. Agents escalate Tier 2 decisions through comments. Heartbeats wake agents when comments land or issues change.

This is what makes the system auditable. Every action has an issue. Every decision has a comment. Every approval has a record.

## Slack: one DM per agent

Each agent has a dedicated Slack DM with Steven. Inbound messages spawn Paperclip issues automatically. The agent works the issue and responds in the same DM. The Slack listener is a small Python service that watches each DM channel, validates the sender, and creates a Paperclip issue with the message as the body.

In practice: Steven DMs the CEO "is the Acme renewal still on track?" and within a minute he gets back a brief with the open commitments, the last interaction, the cash status, and a recommendation. He never opens Paperclip — he just gets the answer.

## Cadence (the part most AI systems skip)

Every agent runs on a cron-driven heartbeat — independent of whether anyone is typing. The heartbeat:

- Scans the agent's Paperclip inbox for new comments
- Reads the agent's own `state/current.md` for stale work
- Picks up scheduled tasks (morning briefs, weekly reviews, drift scans)
- Wakes other agents via the API when cross-functional work is needed

This is what turns the agents into a workforce instead of a chatbox. Things move forward overnight. Stale work gets surfaced. Approvals don't sit in a queue waiting for Steven to remember.

## Integrations

Each agent can call any of these as tools:

- **Outlook** (Microsoft Graph) — calendar reads, email reads, draft creation. Draft-only — no agent sends email autonomously, by policy.
- **HubSpot** — CRM reads and writes, pipeline state, deal stage transitions.
- **Notion** — docs, databases, meeting notes (being migrated to Obsidian + SQLite).
- **Google Drive** — file reads.
- **QuickBooks Online** — invoices, customers, expenses, P&L pulls.
- **Slack** — listeners, agent DMs, channel posts.
- **GitHub** — repos, issues, PRs, releases.
- **iCloud** — calendar fallback.

Adding an integration is a matter of writing a new tool under `tools/`, documenting it in a workflow, and any agent can use it from then on.

## Governance

The agents don't run unbounded. Authority is explicit:

- **Tier 1 decisions** — agents act unilaterally (e.g., CEO can hire/retire agents, reprioritize sprints, route escalations).
- **Tier 2 decisions** — agents recommend, board approves (e.g., any spend, new client contracts, partnership agreements, strategy pivots).
- **Standing pre-authorizations** — defined ahead of time (e.g., retainer renewals on active engagements with no cost change).
- **Draft-only email** — no agent sends email without human review. Enforced at the skill level.

The CEO agent enforces these matrices on its peers and escalates anything ambiguous.

## Cross-agent context

Agents read each other's state. Rosalind's `/update` skill pulls the current state of every peer agent and surfaces what's drifting across the entire team. The standup skill convenes peer-function voices into a single brief. When the CEO needs sales context, it reads Sales Ops' state file directly — no human in the loop.

This is what makes the team feel coordinated rather than ten disconnected chatbots.

## What this means for you

If you want a personal Chief of Staff, the [kit in this repo](../README.md) is the give-away. Set it up, capture conversations, brief before meetings, close out the week.

If you want to extend toward what we run — a leadership team of agents, integrations into your live stack, cadence that operates while you sleep, governance the board can actually approve — that's what we do for clients. [Book a call](https://azuldigital.ai/contact).

The architecture is the same. The substance is what we'd build with you.
