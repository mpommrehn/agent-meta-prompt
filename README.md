# agent-meta-prompt

A collaboration meta-prompt for coding agents, and the record of how it was
built from the published prompting guides of Anthropic, Google, and OpenAI.
With it: the working habits that grew up around it over a summer of daily
use, written so you can copy the ones you want.

It is for two readers. Someone about to work with the author and an agent
on a shared codebase, who needs to know how the agent has been told to
behave and why. And anyone setting up Claude Code, Codex, or a similar
harness for themselves, who would rather start from a tested prompt than
from a blank `AGENTS.md`.

## What is here

| File | What it is |
|---|---|
| `META-PROMPT.md` | The prompt itself: role, communication style, skepticism, asking for input, task framing, agentic execution, durable-config discipline, unattended runs, testing and security policy. A placeholder stands where the principal's name goes. |
| `HOW-IT-WAS-BUILT.md` | The four sources, what was taken from each and what was skipped and why, the calibration decisions, and the version history. |
| `SESSION-HYGIENE.md` | Context-rot thresholds, the checkpoint prompt, and the rules for gates and delegated work. |
| `EVOLUTION-LOG.md` | The rule that every project keeps a construction and evolution log, and what an entry holds. |
| `MACHINE-CONTEXT.md` | One `AGENTS.md` across several machines: imports instead of symlinks, per-machine notes files, presence checks. |
| `VOICE-PATTERN.md` | How to give an agent a personal writing voice without publishing the voice: the pattern, not the author's files. |
| `agent-meta-prompt-EVOLUTION.md` | This repository's own evolution log, from the first commit. |

## How to use it

1. Copy the XML block from `META-PROMPT.md` into your `AGENTS.md`. Replace
   `{{PRINCIPAL}}` with your name and the role line with one sentence about
   who you are to the agent.
2. If your harness reads `CLAUDE.md`, make that file the single line
   `@AGENTS.md`. Claude Code expands the import at session start, so both
   names point at one file with no filesystem link.
3. Read `HOW-IT-WAS-BUILT.md` before editing a rule. Each one is there for a
   reason that is written down, and several were deliberately left out.
4. Take the other files as you need them. `SESSION-HYGIENE.md` earns its
   place after your first ten-hour session; `MACHINE-CONTEXT.md` after your
   first Windows machine.

## Where it came from

The prompt was assembled on 2026-07-07 in four passes, one per source, and
has been the root instruction file for every coding-agent session of the
author's since. The habits in the other files were added as they were
learned, most of them after something went wrong once. The dates are in the
files.

The author's own `AGENTS.md` is the source of truth for their machines and
carries private context this repository does not: who they are, how they
write, what they think. This repository is the part that travels.

## Related

- [agent-style-guide](https://github.com/mpommrehn/agent-style-guide): the
  Google developer documentation style as a skill, with a checker. The
  mechanical half of the voice pattern.
- [goldshell-box-tools-productguy](https://github.com/crProductGuy/goldshell-box-tools-productguy):
  a project built under this prompt, with a public evolution log and an
  essay written from it.

## License

MIT. The source guides are cited by name in `HOW-IT-WAS-BUILT.md`; none of
their text is reproduced here.
