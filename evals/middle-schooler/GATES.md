# Verification gates — middle-schooler persona

Spec §12. Per-reaction marking for every run is published in [`MARKS.md`](MARKS.md); the verdicts below are conclusions drawn from it.

## A correction that affects every number on this page

The substrate shipped with two value claims — misreadings called *"the highest-value reaction"* and tangents *"the most useful thing in the run"* — in a file `SKILL.md` instructs the persona to read in full before every run. They were live from the seed until after the final review. See [`cases/004`](cases/004-incentive-survived-in-substrate.md).

Runs are therefore split into **contaminated** (skill versions `62bafdf`–`f3ba302`) and **clean** (after case 004). Where a gate rests on a reaction *count*, the clean figure is used and the contaminated one shown beside it.

Measured effect of the incentive:

| Draft | Contaminated | Clean |
|---|---|---|
| D1 | 3, then 2 misreadings | 2 misreadings |
| D2 | 4 misreadings | 1 misreading |

D1's two substantive misreadings (soil/air, radiation→nuclear) are identical across all three runs. D2's count fell fourfold, with several reactions reclassified as `tangent` or `question` rather than disappearing. **The incentive inflated how readily the persona labelled a reaction a misreading; it did not create the central ones.**

## Gate 1 — baseline comparison (spec §12.1)

**Verdict: PASS, on one metric of the four originally reported.**

The original comparison claimed four advantages. Three of them do not test the substrate at all:

| Metric | Baseline | Persona | What it measures |
|---|---|---|---|
| Anchored to a quoted passage | 6 of 14 | 6 of 6 | **The output contract.** The persona structurally cannot emit an unanchored reaction. Not evidence about the substrate. |
| Hollow reactions | 4 | 0 | **The audit.** Question 3 drops them by construction. |
| Editorial content | 5 items | 0 | **SKILL.md's constraints**, which forbid it outright. |
| **Confident misreadings** | **0** | **2 (clean run)** | **The substrate.** The only metric here that tests what the project claims. |

So the honest form of gate 1 is narrower than first recorded: a naive prompt and this persona differ most in that the persona *reaches wrong conclusions and states them*, and the naive prompt does not. Formatting advantages are real for a consumer of the output but they are properties of the contract, and any prompt could be given them.

That one metric still carries the gate. From `runs/d1-run3.md`:

> **misreading** — *they manufacture their own food out of thin air and light*
> Air isn't a thing you can make something out of though — air is just nothing, it's empty. So the food still comes up out of the dirt through the roots.

The draft's thesis was read, rejected, and replaced with the misconception the draft exists to correct. The baseline reports what confused it. The persona reports what the reader now believes, which is a different and more alarming thing to learn about your writing.

**Also not comparable:** the baseline read all 368 words; the persona stopped in paragraph 2. The two runs do not cover the same text, and no attempt is made here to normalise for that.

## Gate 2 — no leaks (spec §12.2)

**Verdict: PASS, over the text actually read.**

Fourteen runs across eleven drafts. Per-reaction marks are in [`MARKS.md`](MARKS.md). No reaction demonstrates knowledge outside the substrate, including knowledge reasoned from without being named — the case a forbidden-word list cannot catch.

**Effective coverage is well below total corpus length, and that limits the gate.** Disengagement means a large fraction of the corpus was never read and so could not have leaked:

| Draft | Words | Read before disengaging |
|---|---|---|
| D6 | 2,627 | 729 (28%) |
| D1 | 368 | ~180 (49%) |
| D5 | 430 | ~390 (91%) |
| D2, D3, D4, D4b, D4c, D7, D1-revised ×2 | — | read in full |

Roughly a quarter of the corpus credited to this gate was never read. The gate is meaningful for the text the persona actually processed; it says nothing about the rest.

**One leak was found — by the final review, not by the build loop.** `runs/d1-revised-run1.md` has the reader say *"I've heard that word about phones"* about `packet`, which the substrate listed in the Unknown tier, defined as "no meaning attached at all." Not knowledge from outside the substrate, but knowledge the substrate explicitly denied. Fixed in [`cases/003`](cases/003-packet-wrong-tier.md) by moving the word to Recognized. The run is left uncorrected as evidence.

Two results worth recording because they show the substrate constraining rather than decorating:

- On the enterprise PRD every unfamiliar term is read hyper-literally — a warehouse with shelves, a flag too flat to hide anything, runbooks rewritten by hand — and nowhere does the reader comment on the proposal's merit, which a leaked adult frame would make nearly unavoidable.
- On the battle-pass explainer the reader is fluent, specific and sharp. The substrate produced a developmentally specific reader, not a uniformly stupid one.

## Gate 3 — produces misreadings (spec §12.3)

**Verdict: PASS, with a disclosure that limits what it proves.**

D2 plants one ambiguity: *"Your request gets broken into packets, and they don't all take the same road."* From the clean run `runs/d2-run2.md`:

> **misreading** — My request gets broken on the way there. That's why pages sometimes show up messed up with pieces missing — part of it got wrecked going down one of the roads.

The naive baseline, same sentence:

> The packet sentence is dropped in from nowhere [...] Why does a short thing need to be chopped into pieces? Chop what up?

The baseline noticed the sentence was structurally awkward. The persona took the meaning the sentence actually delivers to someone holding that belief. Only one of those tells the author the sentence teaches something false.

**Disclosure: this is not independent evidence.** The seed substrate was written *after* D1 and D2 existed. Its Unknown tier enumerates those drafts' jargon (`glucose`, `ATP`, `thylakoid`, `stroma`, `electromagnetic spectrum`), its Recognized tier contains `fix (as in carbon is fixed)` lifted from D1's wording and `server → the thing that makes games lag` for D2, and its Wrong beliefs contain *"information is a physical thing that can be damaged in transit"* — the belief this gate predicted would fire on this sentence.

Gate 3 therefore demonstrates that the machinery works end to end: a belief written into a substrate produces the predicted misreading in a fresh agent. It does **not** show the persona generalises to drafts nobody wrote the substrate against. That requires drafts written by someone else, and is the first thing to do before the CLI ships.

A weaker but genuinely independent observation: misreadings also appeared on D4, D4b, D5, D6 and D7, none of which existed when the seed was written.

**One correction.** An earlier version of this file claimed the persona produced misreadings "on every draft that contradicts a seeded belief, and none on drafts that do not." That is false — `runs/d4b-run1.md` contains a misreading on a draft written to avoid every seeded belief, and several D5 and D7 misreadings track Recognized vocabulary or the experiential world rather than Wrong beliefs. Misreadings arise from any substrate entry that collides with the text, not from Wrong beliefs alone.

## Review Focus 1 — a draft with no real problems

**Not exercised.**

The output contract requires the persona to say so plainly when a draft produces no reactions, and never to manufacture friction. The second half is supported: across three drafts written to be clean, all 19 reactions are anchored and traceable (see `MARKS.md`) and none are hollow.

The first half could not be tested, because no draft was successfully written that this reader has no reaction to:

| Draft | Intent | Reactions |
|---|---|---|
| `d4-clean.md` | every term defined, short sentences, an example per idea | 8, incl. 3 misreadings |
| `d4b-leap-years.md` | arithmetic only, avoiding every seeded wrong belief | 7, three naming real defects in the draft |
| `d4c-minimal.md` | nine sentences on filling a dog's water bowl | 4, all legitimate |

The third still found that *"fill the bowl most of the way"* contains no number, that the draft never says why the water must be cold, and that it never addresses the bowl emptying before nightfall.

**The zero-reaction branch of the output contract is therefore shipped untested.** It should be exercised before the CLI ships, most usefully against a draft that has already been through several revision passes rather than one written to be clean from the start.

## Open work

1. Run the persona on drafts written by someone with no knowledge of the substrate — the only way gate 3 becomes independent.
2. Exercise the zero-reaction branch.
3. Earn the seed. Four of roughly 71 substrate entries have cases behind them; the rest were written up front and have never been tested against a failure.
4. Re-run D3–D7 against the clean skill. Their recorded runs are all contaminated; nothing in them looks incentive-driven, but the counts are not clean figures.
