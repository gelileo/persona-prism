# Verification gates — high-school-junior

Spec §12, applied to the second persona. Per-reaction marking in [`MARKS.md`](MARKS.md).

**Status: validated for differentiation and licensing. Not yet gated on leakage or on independent drafts.**

## Gate 1 — differentiation

The usual gate 1 compares a persona to a naive prompt. For a second persona there is a stronger test available: run it on a draft the *first* persona has already read, and see whether two different readers emerge from the same text.

`d1-photosynthesis.md`, read by both:

| Passage | Grade 7 | Grade 11 |
|---|---|---|
| *"The chlorophyll molecule captures photons…"* | **stopped reading** — disengaged at or just before this sentence in all three runs, producing nothing from it or anything after | **performed-understanding** — restated it fluently, with no hedge, and moved on |
| *"arguably the most important chemical reaction on Earth"* | **no reaction** (Posture: importance claims produce none) | **skepticism** — "according to who… is that from somewhere official or is that just the opener" |
| *"The mass of a tree… comes from the air"* | never reached it | **skepticism** — challenged the claim and asked for a source |
| Whole document | ~180 of 368 words read | read to the final sentence |

On `d6-long.md` (2,627 words) the grade 7 reader stopped at word 729. The junior reached the final paragraph — and its two `skim` reactions record where absorption failed *without reading stopping*, which is the behaviour the grade-11 attention budget specifies and the grade-7 one does not have.

**This is the clearest evidence the repo contains that the substrate does the work.** Same text, same model, same output contract, same audit. The only variable is the substrate, and the two readers fail in opposite directions — one quits, one fluently restates what it did not understand. Neither failure is visible to a generic review, and the second is invisible to the reader themselves.

## What this persona adds

`performed-understanding` is a reaction type the grade-7 persona cannot produce, and it is the reason this persona exists. A reader who quits tells you where your document broke. A reader who paraphrases your sentence back at you, correctly and confidently, having understood nothing, tells you something worse — that your document produces the *appearance* of comprehension, and that neither you nor the reader will notice.

> **performed-understanding** — *Its adoption is determined by the distribution of switching costs…*
> The thesis is that a standard is only incidentally a technical object. Whether it gets adopted depends on how the switching costs are distributed across the parties who'd have to adopt it […] Sixty degrees isn't better than fifty-five.

That is a correct, well-structured restatement. Nothing in it is understood.

## Gate 2 — no leaks

**Provisional pass over two runs.** No reaction reasons from statistics, study design, uncertainty, economics or finance — the boundaries the grade-11 substrate draws. The nearest approach is `d6-run1` #4, where the reader evaluates a source and picks the eyewitness account because it sounds authoritative. That is licensed: Reasoning moves records that this reader struggles to judge source quality, and the reaction demonstrates the struggle rather than escaping it.

Two reactions were flagged — a licensed reaction type carrying an unlicensed concrete premise, cases 001 and 002. Both entries added.

**Not sufficient for a gate 2 verdict.** Two drafts, both written for the other persona, neither aimed at this reader. Gate 2 stays open.

## Not done

1. **No naive-prompt baseline.** The differentiation test above is stronger for a second persona, but a baseline comparison is still the claim a stranger will check first.
2. **No draft written for this reader.** Both runs are on grade-7 material. A grade-11-targeted draft is the obvious next probe, and the first one should be content this persona was not designed around.
3. **No wrong-belief probe.** The grade-7 persona was tested against a draft that explicitly contradicts a seeded belief (`d3-falling-objects.md`). The equivalent here would be a draft that correctly explains why correlation is not causation, or what a scientific theory actually is.
4. **Zero-reaction branch untested**, as with the first persona.
5. **The substrate is almost entirely seed.** Two of 79 entries were earned by observed failure. Same debt as the first persona, and named for the same reason.
