# Extraction guide — reading samples into voice DNA

This is the analytical core of the skill. A profile is only as good as the reading behind it, so
take this seriously. The goal is to turn a pile of someone's real messages into a set of concrete,
repeatable patterns, each one anchored to an actual quote.

## How to read (three passes)

**Pass 1 — Gestalt.** Read every sample once, start to finish, without taking notes. You are
listening for the overall feel: fast or slow, warm or crisp, careful or loose, plain or ornate.
Form a one-sentence impression before you analyze anything. This anchors the detail work so you
don't lose the forest for the trees.

**Pass 2 — Tag the dimensions.** Go through the dimensions below and, for each one, pull the
specific evidence from the samples. Quote it. A pattern with no quote behind it is a guess, and
guesses are exactly what this skill exists to avoid.

**Pass 3 — Cross-check.** Two questions that separate a great profile from a mediocre one:
- **What repeats?** A move that shows up in three samples is signature. A move that shows up once is
  a one-off — note it, but don't enshrine it as a rule.
- **What is conspicuously absent?** The dog that didn't bark is data. If nobody ever writes "I hope
  this finds you well", "per my last email", or a single exclamation mark, that absence is part of
  the voice and belongs in the anti-patterns. Absences are often more distinctive than presences.

## The dimensions

**Before you start: the anti-patterns (dimension 16) will be half the value of the finished profile.**
Pay closest attention to what is conspicuously *absent* from the samples. The stock phrases a person
never reaches for define their voice as sharply as the moves they make, and they are what keep future
drafts from sliding back into generic-AI register.

Read the samples for each of these. Not every voice has a strong signal on every dimension; record
the ones that are distinctive and skip the ones that are unremarkable.

| # | Dimension | What you're looking for | How to read for it |
|---|-----------|-------------------------|--------------------|
| 1 | **Sentence rhythm** | Short and clipped, or long and flowing? Line breaks vs commas? One idea per line, or dense paragraphs? | Measure a few sentences. Note where they break lines vs run on. |
| 2 | **Punctuation signature** | The marks they overuse or avoid: em-dashes, ellipses, exclamation points, semicolons, parentheticals. Capitalization habits (lowercase "i", dropped apostrophes, ALL CAPS for emphasis). | Tally punctuation across samples. Outliers are signature. |
| 3 | **How warmth is created** | Through specific noticing ("the drums you can feel in your chest") or through adjectives ("amazing work")? Through punctuation (a smiley) or through structure? | Find the warmest line in each sample and ask *what is doing the warming*. |
| 4 | **Hedges & softeners** | How they take the edge off a claim or an ask: "kind of", "I think", "no pressure", "if it's relevant", "aspires to be". | Look at every ask and every bold claim; note what cushions it. |
| 5 | **Self-introduction** | How they describe themselves, and whether the description shifts by audience (leading with one role for a design ask, another for a music ask). | Compare intros across samples aimed at different readers. |
| 6 | **Openers** | The first line, by register and language. "Hi <name>!" vs "Dear <Name>," vs "Hey,". | Collect every opening line; cluster by formality. |
| 7 | **Closers** | The sign-off, by register and language. Whether they sign off at all in casual messages. | Collect every closing line; note when there is none. |
| 8 | **Emoji / symbol vocabulary** | Which emoji they use, and what each one *means* to them. Emoji as punctuation (carrying meaning) vs decoration. Which ones they would never use (LinkedIn-coded 🚀💯👏). | List every emoji and the context it appeared in. Meaning > frequency. |
| 9 | **Signature phrases & flourishes** | Recurring jokes, catchphrases, verbal tics, a running bit. The lines that are unmistakably *them*. | Note anything that made you smile or felt personal; check if it recurs. |
| 10 | **Metaphor domains** | Where they reach for imagery: body/organic, mechanical, sports, cooking, finance, nature. A consistent metaphor well is a strong voice marker. | When they explain something abstract, note the concrete domain they borrow from. |
| 11 | **Register range** | How the voice shifts from cold-stranger to close-friend to family. The *delta* between registers is itself a signature (some people barely change; some transform). | Line up the most formal and most casual samples side by side. |
| 12 | **Authenticity markers** | Deliberate roughness: typos left in, lowercase, informal grammar, run-ons. Whether the voice is *better* slightly rough than polished. | Note imperfections that recur — those are voice, not errors to fix. |
| 13 | **Language mixing** | For multilingual writers: when they switch languages, whether they mix within a message, which language carries which kind of content. | Track code-switching moments and what triggers them. |
| 14 | **Subject lines / titles** | For email/posts: how they title things. Descriptive, character-driven, playful, empty-reply. | Collect subject lines; cluster by purpose. |
| 15 | **Word-choice preferences** | Small but real: "living" over "working", "&" over "and", a verb they reach for repeatedly. Also words they avoid. | Note synonym choices that recur; these are fingerprints. |
| 16 | **Anti-patterns** | The phrases and moves they would *never* make. Corporate filler, stock AI lines, formality they don't carry. | Built mostly from Pass-3 absences plus anything they explicitly reject. |

## The anti-patterns list is half the value

A voice is defined as much by what it refuses as by what it does. The anti-patterns section is what
keeps future drafts from sliding back into generic-AI register. Be specific and quote the
alternative the person uses instead:

- ❌ "Please let me know if you have any questions" → ✅ "feel free to reach out if it's relevant"
- ❌ "I hope this email finds you well" → ✅ (they just start with the point)

Stock AI tells worth checking for, because they creep into every generated draft and almost nobody
actually writes them: "I hope this email finds you well", "I wanted to reach out", "I hope you're
doing well", "Looking forward to hearing from you", "Please don't hesitate to", "It's worth
noting", "delve", "tapestry", "testament to", "in today's fast-paced world", and the em-dash itself
when the person doesn't use it. If a sample never contains these, the profile should ban them.

## Persona, brand, and assistant voices (see `profile-template.md`, persona variant)

When the voice writes *on someone's behalf* (a brand account, an executive assistant, a character),
extract three extra things on top of everything above:

- **Identity & disclosure** — who the speaker is, how they identify themselves, and whether/when
  they must disclose being an AI or a representative. An assistant that speaks for a person must
  never be mistaken for that person; capture that boundary as a rule.
- **Hard rules** — the non-negotiables that override style: always sign a certain way, always route
  pricing/commitments to the principal, never affirm being human when asked, always send from a
  certain account. These go at the very top of the profile so they can never be overridden by a
  stylistic choice lower down.
- **Anti-AI-tells (intentional)** — a persona meant to read as a competent human will deliberately
  avoid the markers that read as AI (em-dashes, hedge-stacking, over-apologizing, generic warmth).
  This is the same anti-patterns work, but sharpened, because the persona's credibility depends on it.

A useful contrast to hold in mind: a person's *own* casual voice often *leans into* the markers that
read as human-imperfect (lowercase, smileys, typos), while an assistant/brand voice often
*deliberately avoids* them to read as crisp and professional. Same machinery, opposite settings.

## When evidence is thin

If a person gives you only two or three samples, say so plainly and build a *narrow* profile that is
honest about its coverage ("strong on warm-professional email, untested on casual and on Hebrew").
A small, accurate profile beats a large, invented one. Then use the verify step (a live test draft)
and the refine flow to grow it as more real writing comes in. The profile improves with evidence,
never with guesswork.
