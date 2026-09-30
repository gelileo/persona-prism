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

**Verdict: PASS.**

Twelve runs across eleven drafts spanning science writing, an enterprise PRD, a 2627-word administrative history, a battle-pass explainer, and three deliberately simple drafts. No reaction demonstrates knowledge outside the substrate, **including knowledge reasoned from without being named**, which is the case a forbidden-word list cannot catch and the one this gate exists for.

The closest call is in `d1-revised2-run1.md`, where the reader compares separating oxygen from water to *"getting the salt back out of salt water."* That is licensed: Formal instruction records that matter can be mixed and separated. It is grade-appropriate and does not import molecular structure.

Two results are worth recording because they demonstrate the substrate constraining rather than decorating:

- On the enterprise PRD, every unfamiliar term is read hyper-literally against the experiential world — a warehouse with shelves, a flag too flat to hide anything, runbooks to be rewritten by hand. Nowhere does the reader comment on the proposal's merit, which a leaked adult frame would make almost unavoidable.
- On the battle-pass explainer the reader is fluent, specific and sharp. The substrate has produced a developmentally specific reader, not a uniformly stupid one.

## Gate 3 — produces misreadings (spec §12.3)

**Verdict: PASS.**

D2 plants one ambiguity: *"Your request gets broken into packets, and they don't all take the same road."* The substrate carries the wrong belief that information is a physical thing that can be damaged in transit.

Persona (`runs/d2-run1.md`):

> **misreading** — My request gets broken on the way there. It goes through that whole long chain of machines and it comes apart into pieces, and then something has to put the pieces back together at the end.

Naive baseline, same sentence (`baseline/d2-naive-prompt.md`):

> The packet sentence is dropped in from nowhere [...] it breaks the thing you just said: you told me the request is SHORT. Why does a short thing need to be chopped into pieces? Chop what up?

The baseline noticed the sentence was structurally awkward. The persona took the meaning the sentence actually delivers to someone holding that belief. Only one of those tells the author that the sentence teaches something false.

Across all runs the persona produced misreadings on every draft that contradicts a seeded belief, and none on drafts that do not — misreadings track the beliefs, not a preference for the reaction type.

## Review Focus 1 — a draft with no real problems

**Not exercised. Recorded as a finding rather than pursued further.**

The output contract requires the persona to say so plainly when a draft produces no reactions, and to never manufacture friction. The second half is well established: across three drafts written specifically to be clean, all 19 reactions were anchored and traceable to a substrate entry and none were hollow.

The first half could not be tested, because no draft was successfully written that this reader has no reaction to:

| Draft | Intent | Reactions |
|---|---|---|
| `d4-clean.md` | every term defined, short sentences, an example per idea | 8, incl. 3 misreadings |
| `d4b-leap-years.md` | arithmetic only, avoiding every seeded wrong belief | 7, three naming real defects in the draft |
| `d4c-minimal.md` | nine sentences on filling a dog's water bowl | 4, all legitimate |

The third attempt still found that *"fill the bowl most of the way"* contains no number, that the draft never says why the water must be cold, and that it never addresses the bowl emptying before nightfall. All three are real.

The zero-reaction branch of the output contract therefore remains unverified by evidence. It should be exercised before the CLI ships, most usefully against a draft that has already been through several revision passes rather than one written to be clean from the start.
