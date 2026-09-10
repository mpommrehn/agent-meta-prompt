# Session hygiene: context-rot thresholds and stop-losses

Adopted 2026-08-21 after a ten-hour add-a-bug, fix-a-bug session and a
delegated executor that reported a verification it had not run. The
principle: **state lives in files, not in the session.** A session should be
killable at any moment with at most fifteen minutes of work lost.

## Thresholds

These are calibration starting points, not laws. Adjust them after you have
watched a few sessions degrade.

| Signal | Threshold | Action |
|---|---|---|
| Context usage | about 50 percent | Finish the current unit of work, checkpoint; only small units after |
| Context usage | about 70 percent | Checkpoint and restart at the next natural boundary; start nothing new |
| Auto-compaction fires | first time | Yellow: wrap the unit, checkpoint, restart |
| Auto-compaction fires | second time | Red: restart now, mid-unit if necessary |
| Wall clock or scope | about two hours, or one gate | Natural boundary; restart even if context looks fine |
| Same file "fixed" | third time | Stop-loss: stop, write up the state, restart with a fresh diagnosis |
| The session re-asks a settled decision | once | Context integrity is gone; restart |
| The session's account disagrees with `git diff` | once | Restart; trust the diff |

## Compact or restart

If the session's valuable state can be written to files, restart. Compact
only when it cannot, which is rare. Even mid-debug, prefer writing a debug
log (hypotheses, ruled-out causes, the next experiment) and restarting. A
fresh session re-reads ground truth; a compacted one trusts a summary.

## The checkpoint prompt

Verbatim, whenever a threshold trips:

> "Update the status doc: done, not done, open items, exact next action.
> Append this session to the evolution log. Commit everything green. Then
> stop."

The status doc is a gitignored `STATUS.md` at the project root with those
four sections. The evolution log is described in `EVOLUTION-LOG.md`.

Start the next session from a brief: the goal, the two or three
ground-truth files, the constraints, and the done-when condition. Have the
session restate the task before acting. A mismatch surfaces then, rather
than after the work.

## Gates and delegation

- Size a gate to fit one session comfortably under the thresholds. A bigger
  gate is two gates with a status line between them.
- A delegated executor's claim of success counts only as a raw command and
  its output in an evidence file that the verifying session inspects. Prose
  saying "verified" counts for nothing. This rule exists because of a
  specific incident, not as a precaution.
- Verification runs in a fresh session, never the maker's.
- Every delegated brief carries written stop-losses: three strikes on one
  file, a time or tool budget, and "the same error blocks you twice: stop
  and write it up, don't retry."
