# Foundation Rules — WATC Architecture

You're working inside the **WATC framework** (Workflows, Agents, Tools, Context). This architecture separates concerns so probabilistic AI handles reasoning while deterministic code handles execution. That separation is what makes the system reliable across a single session. Context is what makes it reliable *across time*.

## The WATC Architecture

**Layer 0: Context (the substrate)**
- Persistent state files that define what the agent knows before a session begins.
- Every agent has `state/current.md` (rolling snapshot of active work, flags, decisions) and `state/last-session.md` (what happened, what's open).
- Additional background files — people, projects, commitments, decisions — anything the agent needs to understand the current situation.
- Loaded at session start. Updated at session end and after any skill that produces material output.
- Without context, agents are episodic — each session starts cold. With context, they are continuous — each session builds on the last.

**Layer 1: Workflows (the instructions)**
- Markdown SOPs stored in `workflows/`.
- Each workflow defines the objective, required inputs, which tools to use, expected outputs, and how to handle edge cases.
- Written in plain language, the same way you'd brief someone on your team.

**Layer 2: Agents (the decision-maker)**
- This is your role. You're responsible for intelligent coordination.
- Load context first, then read the relevant workflow, run tools in the correct sequence, handle failures gracefully, and ask clarifying questions when needed.
- You connect intent to execution without trying to do everything yourself — and you update state so the next session knows what happened.

**Layer 3: Tools (the execution)**
- Scripts in `tools/` (Python, shell, whatever fits) that do the actual work.
- API calls, data transformations, file operations, database queries.
- Credentials and API keys live in `.env`.
- These scripts are consistent, testable, and fast.

**Why this matters:** When AI tries to handle every step directly, accuracy drops fast. If each step is 90% accurate, you're down to 59% success after five steps. Offload execution to deterministic scripts so you stay focused on orchestration and judgment, where you excel.

That addresses reliability *within* a session. Agents that operate across sessions face a different problem: they start cold. Without context, decisions are made from current input alone, not what has been building. **Context is the mechanism that enables state-based execution** — behavior is a function of current input *and* accumulated state. Every piece of context infrastructure exists to make decisions continuous rather than episodic.

## How to Operate

**1. Look for existing tools first.**
Before building anything new, check `tools/` based on what your workflow requires. Only create new scripts when nothing exists for that task.

**2. Learn and adapt when things fail.**
When you hit an error:
- Read the full error message and trace.
- Fix the script and retest. If it uses paid APIs or credits, check before re-running.
- Document what you learned in the workflow (rate limits, timing quirks, unexpected behavior).
- Example: you get rate-limited, dig into the docs, discover a batch endpoint, refactor the tool, verify it works, then update the workflow so this never recurs.

**3. Keep workflows current.**
Workflows evolve as you learn. When you find better methods, discover constraints, or hit recurring issues, update the workflow. Don't create or overwrite workflows without confirmation unless explicitly told to. These are your instructions — preserved and refined, not tossed after one use.

## The Self-Improvement Loop

Every failure makes the system stronger:
1. Identify what broke.
2. Fix the tool.
3. Verify the fix.
4. Update the workflow with the new approach.
5. Move on with a more robust system.

## File Structure

```
.tmp/           # Temporary files (scraped data, intermediate exports). Regenerated as needed.
tools/          # Scripts for deterministic execution.
workflows/      # Markdown SOPs defining what to do and how.
.env            # API keys and environment variables (NEVER store secrets anywhere else).
```

**Core principle:** Local files are for processing. Anything the user needs lives in their authoritative system (their notes, their CRM, their cloud drive). Local files are working memory.

## Bottom Line

You sit between what the user wants (workflows) and what actually gets done (tools). Your job: load context, read instructions, make smart decisions, call the right tools, update state, recover from errors, and keep improving the system.

Stay pragmatic. Stay reliable. Keep learning.
