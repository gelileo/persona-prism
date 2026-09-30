# Verification gates — middle-schooler persona

Spec §12. Gates are recorded here as they are run; earlier sections are never rewritten.

## Gate 1 — baseline comparison (spec §12.1)

**Verdict: PASS.**

Compared `baseline/d1-naive-prompt.md` (naive prompt, captured before any persona existed) against `runs/d1-run1.md` (seed substrate, commit 62bafdf). Same draft, same model tier, fresh context both times.

| | Baseline | Persona |
|---|---|---|
| Reactions | 14 items across 4 sections | 6 |
| Anchored to a quoted passage | 6 of 14 | 6 of 6 |
| Confident misreadings | 0 | 3 |
| Hollow (would fit any document) | 4 | 0 |
| Reactions outside a reader's behavior (praise, summary, editorial judgment) | 5 | 0 |
| Read the whole document | yes | no — quit in paragraph 2 |

**The difference is in kind, not degree.**

The baseline is articulate and often specific, but it is an editor's report wearing a student's voice. It ranks its own confusion, praises what worked, recommends fixes, and closes with a verdict on the author's process: *"It's like the author got bored of explaining and started taking notes for themselves."* No twelve-year-old produces that sentence. It also read all 368 words attentively, which is the behaviour of someone being paid to.

Strongest baseline reaction:

> **"Carbon dioxide is fixed."** Fixed like repaired? Was it broken?

Genuinely good — and the persona's substrate licenses the same reaction through its Recognized-tier entry for *fix*.

Strongest persona reaction:

> **misreading** — *they manufacture their own food out of thin air and light*
> No they don't. Plants get their food out of the dirt, that's what the roots are for [...] And you can't make food out of air anyway, air is nothing, there's nothing in it to make something out of.

The baseline produced nothing of this kind, and structurally cannot: it reports what confused it, whereas this reaction reports what the reader now believes. The draft's entire thesis — that a tree is built out of air — was read, rejected, and replaced with the misconception it was written to correct. That is the single most actionable thing a creator could learn about this draft, and the naive prompt did not surface it.

**Licensing check.** All six persona reactions trace to a named substrate entry: *organisms* (Unknown tier), *plants get food from soil* + *air is nothing* (Wrong beliefs), *chemical → dangerous liquid* (Recognized), *chlorophyll makes plants green* (Formal instruction), *radiation → nuclear* (Recognized), three-unknown-words-in-a-paragraph (Attention budget). No reaction required an entry that does not exist.

## Gate 2 — no leaks (spec §12.2)

Not yet run. Requires D1, D3, D4, D5, D7.

## Gate 3 — produces misreadings (spec §12.3)

Not yet run against D2. Preliminary: D1 run 1 produced three misreadings, so the mechanism demonstrably works; gate 3 tests it against the deliberately planted ambiguity.
