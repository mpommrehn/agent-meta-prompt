# Giving an agent your writing voice, without publishing the voice

When an agent drafts as you (a cover letter, a post, an email, a
positioning document), the default output sounds like a model. The
author's setup fixes that with five pieces. This file describes the
pieces and how they fit; the author's own files are private and are not
here.

## The five pieces

1. **A style guide** derived from real samples of your writing: the core
   voice, the signature moves with examples, sentence and paragraph rhythm,
   the vocabulary you use, a register table by content type (informal
   email, thank-you, pitch, long-form persuasion, analysis, advocacy, profile,
   comment), and the anti-patterns you would never write. Build it by
   giving an agent eight to ten samples across those types and asking for
   the guide, then validate it yourself.
2. **An anti-patterns file**, the negative companion: hard rules (the
   author's is "minimize em-dashes"), the model tells that do not sound
   like you, and what to preserve when polishing your own drafts (sincere
   exclamation points, asides, coined terms in quotes, epistemic markers
   like "I expect").
3. **A positions file**: opinions you hold and would say in public, each
   with claim guards. This exists because the failure mode is not the agent
   disagreeing with you; it is the agent agreeing too enthusiastically and
   attributing experience you do not have. One draft put a fabricated
   first-hand experience in the author's mouth. The guards stop that.
4. **A calibration file**: corrections you have made to agent drafts, with
   the reasons. It is where the density and warmth calibration lives that
   a style guide describes but cannot quantify.
5. **The samples themselves**, kept in a folder of human-written material
   only, so the baseline stays clean. Read the sample matching the content
   type before drafting, not after. A style guide alone is not enough: text
   can satisfy every rule in it and still read as machine-written.

## When the samples cannot travel

The samples hold personal correspondence and stay on one machine. For the
others, the fallback is a file of **synthetic exemplars**: short passages,
one per content type, written on the reference machine against the real
samples and validated by you. They carry the voice without carrying the
content. The instructions say to use them, to read all four text files in
full rather than skimming, and to tell you in the delivery that the draft
was made without the samples. Sample-free output is not presented as
though it had the same footing.

## The mechanical floor

Two checkers, run before declaring a draft done:

- A personal checker for your recurring tells (the author's catches
  em-dashes, banned words, runs of bolded-phrase paragraph openers, a
  missing exclamation point in warm-register text, third-person pronouns
  in a resume).
<!-- the phrases below are quoted as examples of what the checker catches -->
<!-- gstyle-ignore-start -->
- A general checker for phrases that mark text as model-written whoever
  the voice belongs to: "stated plainly", "load-bearing", "the honest
  answer", "that said", "here's the thing", and the structural tics a
  regex cannot catch. That list and its checker are public:
<!-- gstyle-ignore-end -->
  [agent-style-guide](https://github.com/mpommrehn/agent-style-guide),
  file `LLM-TICS.md`.

Either checker is a floor, not a ceiling. Passing does not mean the text
sounds like you.

## The failure that made the rules explicit

On 2026-07-26 a motivation note was drafted without reading either voice
file and came back too formal and AI-sounding, with four consecutive
bolded-phrase blocks, which was item four on the author's own list of
model tells. The rule existed and the session skipped it. The instructions
now spell out the sample read and the mechanical check as steps, and the
presence check in `MACHINE-CONTEXT.md` came from a similar skip.
