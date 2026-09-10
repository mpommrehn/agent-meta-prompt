# The project construction and evolution log

Adopted 2026-09-09, after the story of a five-day project had to be
reconstructed from five session transcripts. Reconstructing it took a
morning. Writing it as the work happened would have taken minutes per
session.

## The rule

Every project built with an agent keeps one file, committed, at the project
root:

```
<project-dir-name>-EVOLUTION.md        for example goldshell-box-tools-productguy-EVOLUTION.md
```

The name is derived from the directory so any harness can find it without
reading anything else. It sits beside the gitignored `STATUS.md` and is read
with it at session start. It travels with the repository, public or
private.

## Purpose

Enough record that someone can later write a coherent narrative of what
was built, how it was defined and extended, and the key recommendations,
prompts, and decisions along the way. The author uses it for portfolio
pieces and to show people how to work with agents. The agent uses it to
pick a project up cold.

It is not a changelog; git has that. It is not a status document;
`STATUS.md` has that. It is the reasoning, in order.

## When to write

- One entry per session, at the checkpoint. The checkpoint prompt in
  `SESSION-HYGIENE.md` includes it.
- One entry at any gate that changes scope.
- Start the file in the first session of a new project, before any code.
- For a project that predates the rule, reconstruct once from transcripts,
  git history, and status documents, and label the reconstruction as such.

## What an entry holds

Ten to thirty lines, date-stamped, newest at the bottom:

- the goal in the principal's words: quote the prompt that set the scope,
  trimmed
- the questions the agent asked, and the answers
- proposals made, the alternative considered, the decision, who made it,
  and why
- findings that changed the design: facts discovered, not code written
- what was built, how it was verified, where it was deployed
- pushback in either direction and how it resolved
- what was left out, deferred, or refused, and why

Name files, commits, and versions only where a reader needs them to find
something. Prefer the reasoning over the artifact list.

## What it must never hold

Credentials, tokens, addresses (IP, MAC, wallet, email, street), other
people's names or data, or anything from a transcript that was itself
sensitive. Before the first push of a public repository, read the whole
file once for this. The log is public by default because the repository
is; write it that way from the first line.

## Per-project pointer

A project's own `AGENTS.md` names the log file explicitly under its
ground-truth files, so the rule survives being read out of context. If you
keep project templates, put the section in the templates.

## A worked example

[goldshell-box-tools-productguy-EVOLUTION.md](https://github.com/crProductGuy/goldshell-box-tools-productguy/blob/main/goldshell-box-tools-productguy-EVOLUTION.md)
is the reconstructed log that prompted the rule, and
[docs/how-this-project-evolved.md](https://github.com/crProductGuy/goldshell-box-tools-productguy/blob/main/docs/how-this-project-evolved.md)
is the essay written from it. This repository's own log is
`agent-meta-prompt-EVOLUTION.md`.
