---
name: voiceprint
description: >
  Build a reusable writing-voice profile from a person's real writing, then draft new text
  in that voice on demand. Use this whenever someone wants Claude to "write like me", "sound
  like me", "capture my voice/tone/style", "clone my writing", "build a voice profile", "make a
  brand voice", "create a persona voice", or stop getting generic AI-sounding drafts. Trigger on
  ANY of: "write this in my voice", "make it sound like me", "this doesn't sound like me", "set
  up my writing style", "give my assistant/brand a voice", or a request to draft an email / post /
  message that should sound like a specific real person or persona. Two modes: BUILD a profile
  from real samples, and DRAFT using an existing profile. Always prefer this skill over winging a
  "sound like you" request, because voice captured from real samples beats voice guessed from a
  vibe.
---

# voiceprint — build a writing voice from real samples, then write in it

## What this is

Most attempts to make an AI "write like me" fail the same way: someone describes their tone
("friendly but professional") and the model generates a generic average of that description. The
result sounds like everyone and no one.

This skill works the opposite way. A person's voice already exists, fully formed, in text they
have already written. The job is not to *invent* a voice from adjectives, it is to *read* real
samples and extract the concrete, repeatable patterns that make their writing recognizably theirs:
how they open, how they hedge, the punctuation they lean on, the words they would never use, the
emoji that mean something to them. Those patterns get written into a self-contained **profile
file**. After that, drafting in their voice is just applying the profile.

The output is complete and reusable: a user points the skill at their own writing and walks away
with a self-contained profile that makes every future draft sound like them.

## The one principle that makes or breaks a profile

**Voice is extracted from real writing, never invented.** Everything in a profile must trace back
to something the person actually wrote, or to something they explicitly confirmed. The moment you
start guessing ("they're a designer, so probably casual"), the profile drifts toward generic and
the whole product loses its value.

Practically, this means: **collect real samples before writing a single line of the profile.** If
the person has not given you samples yet, getting them is step one, not an optional nicety. When a
later sample contradicts the profile, the sample wins and the profile gets updated. The profile is
a description of evidence, and it stays honest to the evidence.

## Two modes

| Mode | When | What happens |
|------|------|--------------|
| **Build** | No profile exists yet, or the user says "build / set up / create my voice" | Collect samples → scope → extract DNA → fill gaps → generate the profile file → verify with a live test draft |
| **Draft** | A profile already exists and the user wants to write something | Load the profile → detect context → draft → quality-check → present |

If you are unsure which mode applies, check whether a profile already exists (see *Where profiles
live* below). No profile → Build. Profile exists → Draft. The user asking to "redo" or "fix" their
voice → Build again (or the refine flow at the end).

---

## BUILD mode — turning samples into a profile

Work through these six steps. They are a sequence, but stay conversational, not robotic: this is a
collaboration to capture something personal, so explain *why* you are asking for each thing.

### Step 1 — Collect real samples (the foundation)

Ask for **5 to 15 real pieces of their own writing**, spread across the situations they actually
write in. Variety matters more than volume: one cold email, one message to a close friend, one
work/client message, one social caption, and one "annoyed but polite" reply will teach you far more
than ten near-identical newsletters.

Make it easy. They can paste text directly, point you at files (a sent-mail export, a `.txt`, a doc),
or drop links. Tell them plainly: *the profile can only capture what it sees, so the wider the
range of samples, the more situations it will nail.* If they give you only formal writing, the
profile will only be good at formal writing, and that is worth saying out loud.

**Do not wait for them to know what to bring, help them find it.** Most people underestimate how much
of their voice is already sitting in their sent folder. Read `references/finding-samples.md` for where
voice lives (ranked by signal) and what to skip. If an email or Gmail connection is available in this
environment, proactively offer it: *"want me to learn your voice from your sent mail?"* It is the
single richest source. Keep it a soft, opt-in suggestion, never automatic, because reading someone's
mail is theirs to allow.

Before analyzing, skim the samples and confirm they are genuinely the person's own unedited writing,
not something already AI-polished. AI-polished samples poison the well: you would be extracting the
model's voice, not theirs. If a sample looks scrubbed, ask for a rougher one.

### Step 2 — Establish scope

Pin down what you are building, because it changes the shape of the profile:

- **Whose voice?** Their own (write *as* them), or a persona / brand / assistant that writes *on
  someone's behalf*? A self-voice and a persona-voice are different templates. See `references/profile-template.md`.
- **Languages?** One, or several? Multilingual voices need per-language patterns, because openers,
  closers, and warmth markers rarely translate one-to-one.
- **Which registers / contexts?** Map the situations they write in (cold stranger, client,
  colleague, friend, family, public/social, bureaucratic). Each becomes a row in the register matrix.
- **For persona/brand voices:** is there a disclosure or hard-rule layer? (e.g. an assistant that
  must never impersonate its principal, must always sign a certain way, must route certain topics.)
  These become non-negotiable "Hard rules" at the top of the profile.

### Step 3 — Extract the voice DNA

This is the analytical heart. Read the samples against a fixed set of dimensions (sentence rhythm,
punctuation signature, warmth markers, hedges and softeners, self-introduction patterns, emoji
meaning, openers/closers, and crucially the anti-patterns — what they conspicuously *never* do).

**Read `references/extraction-guide.md` now** for the full dimension checklist and how to read a
sample for each one. Do not skip it: the difference between a profile that sounds like the person
and one that sounds generic is almost entirely in how carefully this extraction is done.

Capture every pattern with a concrete example pulled straight from a sample, so the profile is
auditable and the person can recognize themselves in it.

**Before moving on, check for gaps.** If a register, language, or situation the person cares about
has no real evidence in the samples, do not paper over it in Step 5. Go to Step 4 and get more
evidence first. The single most damaging thing you can do here is quietly invent a pattern to fill a
hole, because that is exactly the generic-voice failure the skill exists to prevent. A profile that
honestly says "untested on casual Hebrew" is worth more than one that fakes it.

### Step 4 — Interview to fill the gaps

The samples will not cover everything. For registers or contexts with no sample, either ask for one
more sample (better) or ask a focused question (acceptable). Confirm the things that are easy to get
wrong: phrases they would never use, their real signature/footer, emoji that carry specific meaning,
any words they have strong feelings about. Keep this light, a few targeted questions, not an
interrogation. One question at a time reads as a conversation; a wall of questions reads as a form.

### Step 5 — Generate the profile file

Write a self-contained profile following the anatomy in `references/profile-template.md`. Self-contained
means: someone could hand this single file to a fresh model and it would draft correctly in the
voice, with no other context. Save it to the profiles directory (see *Where profiles live*).

Include a provenance line near the top: how many samples, roughly what date range, so future-you
knows how much evidence backs the profile and when it might be going stale.

### Step 6 — Verify with a live draft

A profile is a hypothesis until it is tested. Immediately draft one realistic message in the new
voice (pick a situation the person actually faces) and show it with the direct question: **"Does
this sound like you? What is off?"** Their correction is gold, it is a fresh sample of what they
*don't* sound like. Update the profile from it. One or two rounds of this is usually enough to lock
the voice in.

---

## DRAFT mode — writing in an existing voice

When a profile exists and the user wants something written:

1. **Load the profile.** Read the matched profile file and treat its contents as authoritative.
2. **Detect context.** From the request, identify recipient, relationship/register, language,
   purpose (share / ask / reply / decline / thank / apply…), and length target. If any of these is
   genuinely ambiguous and would change the draft, ask **one** focused question; otherwise pick the
   most reasonable reading and proceed.
3. **Draft** using the profile's register matrix and voice DNA. Pull real openers, closers, and
   moves from the profile rather than improvising.
4. **Quality-check** against the profile's anti-patterns list before showing anything. If a line
   trips an anti-pattern, rewrite that line.
5. **Present and offer to iterate** (tighten, lengthen, switch register, switch language, send/copy
   if the harness supports it). Never auto-send; always show the draft first.

---

## Where profiles live

Default location: `~/.claude/voiceprint-profiles/<slug>.md` (create the directory if missing). This
keeps profiles outside the read-only skill package so they survive updates and stay private.

A profile may also live inside a specific project (e.g. a brand voice that belongs to one client's
repo) — if the user keeps it there, just read it from where they point you. One file = one voice.
Name files by slug: `maya.md`, `acme-brand.md`, `my-assistant.md`.

---

## Refining a profile later

Voices evolve, and the first profile is never the last word. When the user says "that didn't sound
like me" or hands you a new sample:

1. Identify which specific pattern, register, or anti-pattern is wrong.
2. Update that section in place, anchored to the new evidence.
3. Add a new register row if a situation emerged that the matrix doesn't cover.
4. Never delete a pattern without an explicit "I don't write like that anymore" — the person's
   own correction is the only authority for removal.

The file's history is its changelog. Keep it honest to the latest evidence.

## Bundled resources

- `references/finding-samples.md` — where a person's voice lives across channels (sent email, chats,
  long-form) and what to skip. Read during **Build, Step 1** to help them gather the right samples.
- `references/extraction-guide.md` — the dimension-by-dimension methodology for reading samples.
  Read during **Build, Step 3**.
- `references/profile-template.md` — the profile anatomy (self-voice and persona-voice variants).
  Read during **Build, Step 5**.
- `assets/example-profile.md` — a complete worked example (a fictional freelance illustrator) so you
  can see what a finished, high-quality profile looks like. Skim it before generating your first one.
