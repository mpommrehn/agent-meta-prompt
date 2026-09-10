# One AGENTS.md across several machines

The author works on a Mac, a Windows PC, and a Linux box, and wants one
instruction file, shared verbatim, that is correct on all three. These are
the three conventions that make that work. Each one was adopted after the
alternative failed.

## Imports, not links

Claude Code reads `CLAUDE.md`; Codex and others read `AGENTS.md`. Keep
`AGENTS.md` as the only real file and make every `CLAUDE.md` exactly one
line:

```
@AGENTS.md
```

Claude Code expands the import at session start. The relative path
resolves against the file that holds it, so the same line works at the
root and in every nested project directory.

Do not use a symlink. On Windows a symlink needs Administrator rights or
Developer Mode, and a symlink carried across a filesystem that does not
record ownership arrives as a ten-byte text stub that the harness reads as
gibberish. Do not use a hard link either: editors that save by writing a
temp file and renaming it over the original break the link silently, and
`CLAUDE.md` then serves stale instructions with no visible sign. Both were
tried on 2026-09-03 and both failed.

One trap: when you write the text `@AGENTS.md` inside `AGENTS.md` itself or
any imported file, wrap it in backticks. Imported files are scanned for
imports, so a bare mention makes the file import itself.

## Per-machine notes files

The reference machine holds the complete tree. Other machines hold a
subset, so some files the instructions name do not exist everywhere. Two
rules in `AGENTS.md` keep the one document correct on all of them:

**Rule 1.** At session start, run `ls *-MACHINE-NOTES.md` and read anything
it lists. A `WINDOWS-MACHINE-NOTES.md` (or `LINUX-...`) records what is
present on that machine, what was left behind, which instructions do not
apply there, and any machine-specific rule (for example, which PowerShell
to launch). No such file means you are on the reference machine, where
everything applies as written. Adding a machine means adding a notes file,
with no change to `AGENTS.md`.

**Rule 2.** Check that a path exists before relying on it, and never invent
a substitute. If a required file is missing, say so, follow the fallback
the instructions give for it, and note the gap in the deliverable. Never
silently skip a required read.

Machine-specific detail belongs in the notes file, never in `AGENTS.md`. The
moment you want to write "on Windows, do X" into the shared file is the
moment to write it in the notes file instead.

## Presence checks over path descriptions

Where instructions point at optional material, make the pointer a command,
not a description. The author's writing-voice section says:

```
ls -d samples/ 2>/dev/null ; ls context/voice-exemplars.md 2>/dev/null
```

and branches on the result. An earlier version described the location in
words ("a sibling of this file's parent"), a session misread it, reported
the directory missing, and skipped the read. A command cannot be misread.

## Carrying changes between machines

Files that are in a git repository travel as commits. For repositories
with no remote, `git bundle` onto removable media works and is
reviewable: the receiving side fetches the bundle into a branch, reads the
log, and merges with `--ff-only`. The two or three loose root files
(`AGENTS.md`, its `CLAUDE.md` pointer, the notes file) travel by plain copy
with the original saved once as a backup.

Two Windows-specific settings that bit: Git for Windows sets
`core.autocrlf=true` system-wide, which rewrites shell scripts to CRLF and
breaks them with `bad interpreter: /bin/bash^M`; set it off per repository
that holds scripts. And NTFS has no executable bit, so set
`core.fileMode=false` per repository or every script shows as modified.
Neither changes what is committed.
