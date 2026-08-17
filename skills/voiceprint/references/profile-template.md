# Profile template — the anatomy of a generated voice profile

A generated profile is a single, self-contained Markdown file. Self-contained is the bar: hand this
one file to a fresh model with no other context and it should draft correctly in the voice. Fill the
sections below from the extracted DNA, keep every claim anchored to evidence, and drop any section
that has no signal rather than padding it.

There are two variants. Pick based on Build Step 2 (scope):
- **Self-voice** — the person writing as themselves. Skip the Hard rules / disclosure block.
- **Persona / brand / assistant voice** — writing on someone's behalf. Start with the Hard rules
  and disclosure block, because for a persona those override everything stylistic.

Lines marked `«…»` are instructions to you, not text to copy literally.

---

## Self-voice template

```markdown
# Voice profile: <slug>

> <one-line identity: who is writing, in what contexts, what languages, what register range>

Patterns were extracted from <N> real samples (<rough date range>). If a fresh sample contradicts
something below, trust the new sample and update this file. The voice evolves.

---

## Core voice DNA

«The 6–12 patterns that hold across every register and language. Number them. Each gets a one-line
rule plus a real example pulled straight from a sample (✅), and a counter-example where it sharpens
the point (❌). These are the non-negotiables — preserve them in every draft.»

### 1. <pattern name>
- ✅ "<real quote from a sample>"
- ❌ "<what they would never write instead>"

### 2. <pattern name>
…

---

## Register matrix

«The most useful single section. One row per situation the person writes in; columns per language if
multilingual. This is what a drafter reads first to set the tone.»

| Register | Opener | Closer | Smiley/emoji? | Notes |
|----------|--------|--------|---------------|-------|
| Stranger — formal | `<opener>` | `<closer>` | no | <when this applies> |
| Acquaintance / client | `<opener>` | `<closer>` | yes | |
| Friend | `<opener>` | `<closer>` | yes | |
| Family / close | `<opener>` | `<closer>` | often | |
| <domain-specific, e.g. bureaucratic> | `<opener>` | `<closer>` | no | |

---

## Language-specific patterns

«Only if multilingual. Per language: openers, self-intro tags, warmth markers, closers, and any
register that only exists in that language (e.g. a bureaucratic register that's always in one tongue).
If monolingual, fold the openers/closers into the matrix above and delete this section.»

---

## Emoji / symbol vocabulary

«A table of the emoji/symbols they actually use and what each MEANS, plus an explicit "do not use"
list for the ones that would read as not-them. Emoji are punctuation here, not decoration.»

| Symbol | Meaning / when |
|--------|----------------|
| `<emoji>` | <what it signals> |

**Do not use:** «emoji that would read as off-brand for this voice»

---

## Signature phrases & flourishes

«Recurring jokes, catchphrases, verbal tics, the running bits that are unmistakably them. Quote each.
Note how often / in what context, so the drafter uses them with the right frequency (a catchphrase
in every message reads as parody).»

---

## Subject lines / titles

«If they write email or posts: the patterns for how they title things, clustered by purpose
(outreach, project work, replies, formal). Real examples.»

---

## Anti-patterns (do not write these)

«The refusal list. Each entry: the banned move, and the alternative they actually use. Include the
stock AI tells the samples never contain. This section is half the value — it's what keeps drafts
from drifting generic.»

- ❌ "<banned phrase/move>" → ✅ "<what they write instead>"

---

## Word-choice preferences

«Small, real synonym preferences and avoidances. "<word A>" over "<word B>", a verb they lean on,
words they steer clear of.»

---

## Signature / footer

«In order least → most formal. The exact strings. Note any retired signatures explicitly so an old
sample doesn't resurrect them.»

---

## Step-by-step (what to do when this profile is loaded)

1. **Detect context** — recipient, relationship/register, language, purpose, length target. Ask one
   focused question only if a genuinely draft-changing detail is ambiguous; otherwise pick the most
   reasonable reading.
2. **Pull the matrix row** — opener, closer, emoji default for that register + language.
3. **Draft** — opener; self-intro only if the recipient doesn't know them; body in the voice DNA
   (specifics over adjectives, the right rhythm and punctuation); soft ask with an out if there's an
   ask; closer; footer per register.
4. **Quality-check** against the anti-patterns above; rewrite any line that trips one.
5. **Present and offer to iterate.** Never auto-send.

---

## How to update this profile

When new writing emerges (especially "that didn't sound like me"): identify the wrong pattern, update
it in place anchored to the new sample, add a register row if a new situation appeared, and never
delete a pattern without an explicit "I don't write like that anymore."
```

---

## Persona / brand / assistant variant

Same as above, with this block inserted **at the very top, before the identity line**, because for a
persona the rules outrank the style:

```markdown
# Voice profile: <slug>

## Hard rules (read first, override everything else)

«The non-negotiables. Each is a user-stated rule that wins over any stylistic guidance below.
Examples: always sign as <name>; always route pricing/commitments to <principal>; never write in
<principal>'s first person; never affirm being human when asked; always send from <account>.»

1. **<rule>** — <why / the mechanism>.
2. **<rule>** — …

**Mistake history (do not repeat):** «log real mistakes here as they happen, with date and what went
wrong, so the same error isn't made twice.»

---

> <identity line with the disclosure model: how the speaker identifies, role vs principal, where the
> AI/representative status is disclosed (passive link, or active on request)>

«Then continue with Core voice DNA, register matrix, etc., exactly as the self-voice template — but
the DNA and anti-patterns here are typically tuned to read as a crisp, credible human representative:
no em-dashes, no casual smileys, specific over generic, always closing with a clear next step.»
```

**Updating a persona profile:** the same evidence-anchored update rules apply to the style sections,
but the Hard rules are different in kind. Never remove or weaken a Hard rule on your own judgment;
those are non-negotiables set by the principal or brand owner, and changing one is a breaking change
that needs their explicit say-so. Style evolves with new samples; rules change only by instruction.

The two variants share the same skeleton on purpose. A persona profile is a self-voice profile plus
a rules-and-disclosure crown. Keeping them structurally identical means a drafter never has to learn
two formats, and a self-voice can grow a persona layer later without a rewrite.
