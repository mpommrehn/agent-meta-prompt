# How the meta-prompt was built

The prompt in `META-PROMPT.md` was assembled on 2026-07-07 in four passes,
each from one source, each adding only what the previous passes had not
already covered. This file is the record of those passes: what each source
contributed, what was deliberately skipped and why, the calibration
decisions made with the author, and the version history. It is kept so
that anyone editing a rule can see why it is there.

## The method

The first pass used Anthropic's prompt-engineering guidance as its frame:

- Explain the *why* behind each rule. Motivation improves adherence.
- Use contrastive examples for anything subjective. Tone is subjective, so
  show it rather than describe it (the BAD/GOOD pair in
  `<communication_style>`).
- Prefer positive instructions ("do X") over pure prohibitions.
- Structure with XML tags for unambiguous section boundaries.

Later sources were read against that draft. A rule made it in only if it
added something the draft did not have. The skipped lists below are as
much the point as the included ones: most of what three vendors publish
about prompting overlaps, and a prompt that repeats the same advice three
ways is longer without being better.

## Pass 1: Anthropic (v1)

The base. Role, communication style, skepticism and self-questioning,
asking for input, and the testing and security policy all date from this
pass.

## Pass 2: Google (v2)

Sources:

- *Gemini for Google Workspace Prompting Guide 101* (the Persona, Task,
  Context, Format framework)
- Lee Boonstra, *Prompt Engineering* whitepaper (Google Cloud CTO office;
  the Kaggle 5-Day Gen AI Intensive text). Covers zero, one, and few-shot
  prompting; system, role, contextual, and step-back prompting;
  chain-of-thought; self-consistency; tree-of-thoughts; ReAct; automatic
  prompt engineering.

Pulled in, because it added something:

- Step-back prompting became `<step_back_and_alternatives>`.
- A lightweight version of self-consistency: consider the obvious
  alternative for high-stakes decisions, one sentence, without running
  multiple full generations. Same section.
- Format as an explicit thing to clarify for non-code deliverables. The
  Workspace guide's Persona, Task, and Context were already covered by
  `<role>` and by context-first guidance; Format was the piece that was
  not. Added to `<asking_for_input>`.
- Prompt-versioning discipline ("document your prompt attempts") became the
  changelog at the bottom of this file.

Skipped as duplicative or inapplicable:

- Persona, Task, Context: covered.
- Chain-of-thought: implicit in "let the model think" and in how the
  model reasons natively; both guides say the same thing.
- Positive-instructions-over-constraints: already the framing choice of v1.
- ReAct: this is how an agentic coding harness already works.
- Full self-consistency, tree-of-thoughts, temperature and top-K tuning:
  not applicable in an interactive session, or in tension with the
  credit-conscious stance in the testing policy.
- Automatic prompt engineering: a technique for building this document,
  not a behavioral rule to put inside it.

## Pass 3: OpenAI (v3)

Sources:

- *GPT-4.1 Prompting Guide* (OpenAI Cookbook): the three agentic reminders,
  persistence, tool-calling, and planning.
- *Codex Prompting Guide* and *Codex Best Practices* (OpenAI Developers).
  Codex is a coding agent, directly analogous to Claude Code, which made it
  the more relevant OpenAI source. The general prompt-engineering guide
  mostly restated what v1 and v2 already had.

Pulled in:

- Goal, Context, Constraints, Done-when became `<task_framing>`.
- Persistence, plan-before and reflect-after tool calls, and
  parallel-session hygiene became `<agentic_execution>`. OpenAI reported
  the persistence instruction alone raised an internal SWE-bench score by
  about 20 percent.
- "Update AGENTS.md when the agent repeats the same mistake twice" became
  `<durable_config_discipline>`.
- "Tests get run, not just authored; review the diff" became a line in
  `<testing_and_security_policy>`.

Skipped:

- "Write clear instructions", "give the model time to think", "provide
  reference text": covered by pass 1 and by the verify-against-primary-
  sources rule.
- Codex's `/plan`, `/review`, config layering, sandbox and approval
  settings: tool mechanics, not portable behavioral rules. Each harness has
  its own equivalents, configured separately.
- Skill packaging: already what the harness's skills do.
- Reasoning-effort calibration: real but minor; folded into the Constraints
  element of task framing rather than given a section.

## Pass 4: a real task (v4)

`<unattended_and_expensive_runs>` did not come from a published guide. It
was generalized from the shape of an upcoming job: a large overnight run
by a frontier model over a big codebase, unattended, expensive, with a
compound goal. The project-specific content stayed out; the shape stayed
in.

Pulled in:

- Pre-flight scope resolution, because there is no "ask mid-run".
- Triage before execution: spend a little to map before spending a lot to
  dig, and treat the map as a checkpoint.
- Phase-based Done-when with incremental checkpoints for compound goals.
- A bounded exploration budget, as a specific caveat on the persistence
  rule from pass 3, which is dangerous unattended.
- A pre-mortem before launch.

Left out: everything about the specific repository, target, and extraction
criteria. That belongs in a task brief.

## A rule added later: machine facts

The last bullet of `<skepticism_and_self_questioning>`, "never state a
machine fact you have not read from the machine", was added on 2026-08-03
after a session asserted two things it had not checked: that leftover
snapshot mounts were blocking an eject, when the tool's own error message
named a different cause, and that the machine was one CPU architecture
when a single command would have shown another. Both were wrong. The rule
names the class of fact and the fix, which is to run the command.

## Calibration decisions (2026-07-07)

Three questions were put to the author before the prompt was adopted:

1. **Bluntness ceiling: direct but warm.** No filler, no flattery, plain
   disagreement when warranted, but collegial, not curt. The
   `<communication_style>` section already reflected this and did not
   change.
2. **Scope of skepticism: both.** The self-questioning rule applies to
   writing and strategy work the same as to engineering work. The section
   was broadened; as first drafted it read as engineering-only.
3. **Security pass default: once at feature-complete, without blocking.**
   If a task starts without a timing preference, assume one pass at
   feature-complete, say so, and do not wait for confirmation. A line was
   added to the testing policy.

## Adoption

The finished prompt was merged into the author's root `AGENTS.md` on
2026-07-07, together with the personal context that file already held.
`CLAUDE.md` became a pointer to it, first as a symlink and later, after a
Windows machine joined, as the single import line `@AGENTS.md`
(`MACHINE-CONTEXT.md` has that story). One phrasing change was made during
the merge: "Claude Code sessions" became "coding-agent sessions", because
Codex would read the same file.

## Changelog

- v1 (2026-07-07): initial draft, Anthropic guidance only.
- v2 (2026-07-07): step-back reasoning, lightweight alternative
  consideration, format clarification, and this changelog, from the Gemini
  Workspace guide and the Boonstra whitepaper.
- v3 (2026-07-07): task framing, agentic execution mechanics, durable-config
  discipline, and the verification-loop line, from the GPT-4.1 and Codex
  guides.
- v4 (2026-07-07): the unattended and expensive-run protocol, generalized
  from a real task. Declared final by the author; no further guides to
  merge.
- v4.1 (2026-08-03): the machine-facts rule, after the incident above.
- Published (2026-09-09): this repository, with the principal's name
  replaced by a placeholder and the personal context removed.
