# Protocol: self-refine

Context: this skill decays as the exporter, the normalizer and the consumers
move. Run this at the end of a session that used it, while the friction is still
concrete.

## Mission
Make the smallest durable change that stops this session's friction from
recurring, and record it.

## Steps
Make every edit in `<repo>/.skills/nexus-tool-schemas/`, the sync source,
and never in a mirror (`.claude/`, `.codex/`, `.cline/`). Every relative path
below names a file in that folder.

1. Review the session: which step was ambiguous, what you had to discover by
   reading source, what the checks missed or flagged wrongly.
2. Ask the user for one concrete correction if any is available. Theirs outranks
   your read of the session.
3. Pick the single smallest fix. Prefer sharpening a protocol or extending a
   script over adding a file. If the friction was a claim that turned out to be
   false, correcting it is the fix.
4. Apply it in the source folder named above. Nothing that goes stale: no tool
   counts, no agent inventories, no line numbers — if the fact changes when the
   code changes, it belongs in a script that reads the source, not in prose.
5. Append an entry to `../refinement-log.md`: date, observation, change, files.
6. Run `npm run sync:skills` after the last edit, the log line included. It
   copies the source over the three mirrors. An edit made only in a mirror is
   reverted by the next sync, and the skills sync check in PR CI fails on it.
7. Re-run the validation: this skill's own scripts against a current export, plus
   the skill-crafter structure validator on this folder.

## Guidelines
- Pattern: one evidence-backed fix per session. The log should read as a history
  of real problems solved.
- Anti-pattern: refining in the abstract. If nothing went wrong and the user has
  no feedback, log "no change" and stop.
- Anti-pattern: growing the router. New detail goes into a folder file.

## Next
Terminal. Report the change and the log entry to the user.
