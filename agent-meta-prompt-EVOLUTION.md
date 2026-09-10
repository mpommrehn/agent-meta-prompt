# agent-meta-prompt: construction and evolution log

One entry per session: the goal in the author's words, questions and
answers, proposals and decisions with reasoning, findings, what was built
and verified, pushback, what was left out. The rule is in
`EVOLUTION-LOG.md`. Nothing here is a credential, an address, or another
person's data.

## 2026-09-09: the repository is proposed and laid down

**Goal, in the author's words.** "I also want to abstract out and create a
repo in mpommrehn GH for my personal-but-not-PII meta-prompts that define
how Claude and other harnesses should work with me. You will see a
meta-prompt someplace, which I created by having Claude combine best
prompting practices from OAI, Anthropic, and Google docs in July. I want to
publish that and how it got created as a new repo, to assist people who
onboard to Claude Code or other coding harnesses with me, to help them get
it right. Think about that and propose."

**The proposal.** A sibling of the author's agent-style-guide repository,
holding: the prompt with a placeholder for the principal's name; the
build record (four sources, what was pulled and skipped, calibration,
changelog), which already existed as a private draft; the session-hygiene
rules; the evolution-log rule with a public worked example; the
multi-machine conventions; and the voice pattern as a pattern only, with
the author's voice files kept private. The private root `AGENTS.md`
remains the source of truth; the repository mirrors it and says so.

**Questions and answers.** Name: `agent-meta-prompt` (the author's pick
from two offered). Placeholder or real name in the prompt: placeholder.
License: MIT (the sibling repository is Apache 2.0; the author chose MIT
here).

**Built.** README, `META-PROMPT.md`, `HOW-IT-WAS-BUILT.md`,
`SESSION-HYGIENE.md`, `EVOLUTION-LOG.md`, `MACHINE-CONTEXT.md`,
`VOICE-PATTERN.md`, `AGENTS.md` with its `CLAUDE.md` pointer, LICENSE, and
this log. Every file was passed through the agent-style-guide checker in
doc mode before the first commit.

**Findings.** The private draft's "adoption plan" section carried Linux
home-directory paths and a symlink scheme that was later replaced; the
public version tells the later story and keeps the paths out. One rule in
the prompt (never state a machine fact you have not read from the machine)
postdates the July build and was added to the changelog as v4.1 with its
incident, so the public history matches the private one.

**Left out.** The author's who-i-am, background, positions, calibration,
and style files; machine notes; any detail of private projects beyond the
one public repository linked as an example. The GitHub remote is added
after the author creates the empty repository; no CLI for that exists on
the build machine.
