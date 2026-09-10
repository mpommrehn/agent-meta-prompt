# AGENTS.md: agent-meta-prompt

Instructions for any coding agent working in this repository. Claude Code
reads this file through `CLAUDE.md`, which holds the single line
`@AGENTS.md`.

## What this project is

A published, abstracted copy of the author's collaboration meta-prompt for
coding agents, with the record of how it was built and the working habits
around it. Prose only; no code beyond what a reader would paste into their
own `AGENTS.md`.

## Ground truth and the two logs

- `STATUS.md`: checkpoint (done, not done, open items, exact next action).
  Gitignored; may be absent on a machine that has not worked here.
- `agent-meta-prompt-EVOLUTION.md`: the construction and evolution log,
  committed and public. Append an entry at every checkpoint. See
  `EVOLUTION-LOG.md` for what an entry holds.
- `HOW-IT-WAS-BUILT.md`: why each rule exists. Read it before changing a
  rule in `META-PROMPT.md`.

## Rules that bound every change

- The author's private root `AGENTS.md` is the source of truth for the
  prompt. Changes flow from there to here, not the other way. When the
  two differ, this file is behind; say so rather than editing the private
  one to match.
- Nothing personal enters this repository: no name except the author's
  GitHub identity, no machine names, addresses, project details from
  private work, voice files, or samples. `{{PRINCIPAL}}` stays a
  placeholder.
- Source guides are cited by title and publisher, never quoted at length.
- Every file passes the agent-style-guide checker in doc mode with no
  failures before a commit. Warnings need a stated reason to keep.
- Version the prompt in the changelog of `HOW-IT-WAS-BUILT.md`; tag the
  repository when a changelog entry lands.
