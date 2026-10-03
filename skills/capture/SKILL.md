---
name: capture
description: Parse a conversation recap and update the system: the person's file, decisions, commitments, and current state. Triggers on /capture, "capture:", "I just talked to", "log this conversation".
---

Parse a conversation recap and update the system.

The user gives a plain-language recap. It may be rough: a voice memo transcript, a few sentences, a stream of thought. Parse it precisely. If the recap points to a file (a transcript, a notes file), read the whole file before extracting anything.

## Steps

1. **Find the person.** Look in `people/` (all subfolders) by name or company. If no file exists, create one from `people/_template.md`. If the name is ambiguous, ask which person before writing anything.

2. **Extract:**
   - What was discussed
   - Decisions made (agreed, approved, resolved)
   - New commitments, both directions, with any dates mentioned
   - Changes to deal, project, or relationship status
   - New open questions

3. **Update the person's file:**
   - Add a new Last Conversation entry at the top of the history
   - Update **Last contact** to the conversation date
   - Update open commitments
   - Never delete earlier entries. Move them below the new one.

4. **Log decisions** in `decisions/log.md`:
   `[YYYY-MM-DD] DECISION: ... | REASONING: ... | CONTEXT: {person or engagement}`

5. **Update commitments** in `decisions/commitments.md`:
   - Add new commitments under You Owe or They Owe
   - Close any earlier commitment the recap shows is done. Closing needs evidence: the recap says it happened, or there is a sent email or delivered file. "They said they would" is not done.

6. **Cross-check the last conversation.** Read what was open from the previous entry with this person. For anything unresolved, ask directly: "Last time you owed them X. Did that get done?" Do not silently roll open items forward.

7. **Update `state/current.md`** if anything material changed: deal status, new risk, a commitment resolved, a senior contact touched (this resets their cadence clock).

8. **Update `tasks.md`** with any new action the user owns. Check for an existing matching task first.

## Confirm

List what you updated, one line per file. Then list anything you could not log accurately without the user's input, as direct questions.
