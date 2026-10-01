# 🌈 PersonaPrism

> **Refract your content across a spectrum of human minds.**

PersonaPrism is a library of Claude Agent Skills, each one a calibrated human reader.

Point a persona at a draft. It returns the reactions that reader would genuinely have — questions, admissions of confusion, requests for a picture or a number or a citation, and misreadings — each anchored to the passage that provoked it. Hand those reactions to whatever is authoring the content. Revise. Run it again. The list getting shorter is how you know you're done.

## The problem

Ask an LLM "is this clear for middle schoolers?" and it answers as a smart adult imagining a child. It reasons in clean linear steps, quietly knows things the reader wouldn't, and defaults to agreeable. You get polished approval and no signal.

A reader with enforced cognitive boundaries produces friction that a generic review never surfaces. The most valuable thing a persona can produce isn't a question at all — it's a **confident misreading**, which proves the text taught the wrong thing rather than merely failing to teach.

## The loop

```
   ┌─────────────┐   reactions,   ┌──────────────────┐
   │   draft     │ ─────────────► │ PersonaPrism     │
   │             │                │ (a reader)       │
   └─────────────┘ ◄───────────── └──────────────────┘
          ▲          anchored to           │
          │          passages              │
          │                                ▼
   ┌──────────────────┐            "What's a supply chain?"
   │ your authoring   │ ◄───────── "So the plant eats the sun?"
   │ agent or you     │            "Can you show me a picture?"
   └──────────────────┘
```

Every run is a fresh reader. No memory, no diffing. If a reaction comes back after you fixed it, the fix didn't land.

## Status

**Two personas shipped.** Full eval record published in `evals/`.

- [`skills/middle-schooler/`](skills/middle-schooler/) — US grade 7. Built to depth, verified against three gates.
- [`skills/high-school-junior/`](skills/high-school-junior/) — US grade 11. Validated for differentiation and licensing; leakage gate still open. See its [`GATES.md`](evals/high-school-junior/GATES.md) for what is not yet done.
- [`docs/authoring-a-persona.md`](docs/authoring-a-persona.md) — the eight fields, the build loop, and the two ways substrates go wrong
- [`docs/worked-example.md`](docs/worked-example.md) — one draft, three revision passes, every reaction verbatim
- [`evals/middle-schooler/`](evals/middle-schooler/) — drafts, frozen baselines, every run, and the recorded gate verdicts

The schema survived the second persona unchanged, which is the first evidence it generalises. The two substrates share **one entry out of 67 and 79**, and all ten section headings — what personas have in common is the schema, not the content, so there is no shared base to factor out.

Deferred: the batch CLI, CI/CD gating, and an interactive persona generator. Persona quality has to be settled before there is any point automating it.

### What the gates found

**One metric separates this persona from a naive prompt, and it is the one that matters.** Given the same draft, the naive prompt produced zero confident misreadings; the persona produced two. The persona's other advantages — every reaction anchored to a quoted passage, nothing hollow, no editorial commentary — are enforced by the output contract and the skill's constraints, so they measure the format rather than the substrate. Any prompt could be given them. Reaching a wrong conclusion and stating it flatly is the part that comes from the substrate.

The naive prompt reports what confused it. The persona reports **what the reader now believes**.

**No leaks** across 14 runs and 119 marked reactions — including paraphrased leaks, the case a forbidden-word list cannot catch. Exactly one leak was found, by review rather than by the build loop, and it is recorded rather than quietly fixed. Per-reaction marking is published in [`evals/middle-schooler/MARKS.md`](evals/middle-schooler/MARKS.md).

**We could not write a draft this reader has no reaction to.** Three attempts — including nine sentences of instructions for filling a dog's water bowl — produced eight, seven and four reactions, every one anchored, none manufactured. Readability is a property of the text; comprehension is a property of the collision between the text and a particular head.

### What the second persona showed

Run both readers over the same draft and they fail in opposite directions. At the sentence *"The chlorophyll molecule captures photons and uses their energy to split water…"* the seventh grader **stopped reading**. The junior **restated it fluently, with no hedge, and moved on** — a correct paraphrase with nothing behind it.

A reader who quits tells you where your document broke. A reader who hands your own sentence back to you, confidently and correctly, having understood none of it, tells you something worse: your document manufactures the appearance of comprehension, and neither you nor the reader will notice. That reaction type — `performed-understanding` — is what the grade-11 persona is for.

Same text, same model, same output contract, same audit. The only variable is the substrate.

### What is not proven

This repo argues that evidence should be published rather than asserted, so:

- **The output contract's zero-reaction branch is shipped untested.** It is a code path no run has exercised.
- **Gate 3 is not independent.** The substrate was written after the test drafts existed and contains the belief the gate predicted would fire. It shows the machinery works end to end, not that the persona generalises to drafts nobody wrote the substrate against.
- **Most of the substrate is unearned.** Four of roughly seventy entries were discovered by observed failure and carry regression cases. The rest were written up front from curriculum documents and the misconception literature. The build loop is the standard to work toward; a large seed is debt.
- **A quarter of the eval corpus was never read**, because the reader disengaged. The leak gate covers the text actually processed and nothing beyond it.
- **Most recorded runs were produced under a defect.** The substrate carried a value claim favouring two reaction types for most of the build. It inflated how readily those labels were applied — fourfold on one draft — without creating the central reactions, which survived its removal unchanged. Full accounting in [`GATES.md`](evals/middle-schooler/GATES.md).

## Design commitments

**Substrate, not blocklists.** A persona isn't defined by a list of words it may not say — that suppresses vocabulary while leaving the reasoning intact, and you get a reader who says "the plant drinks sunlight to make food" and has leaked the entire concept while sounding more authentic than ever. Instead each persona specifies the world it reasons *from*: what it has experienced, what it has been taught, the reasoning moves available to it, and the things it believes that are wrong.

**Reactions carry no diagnosis.** A persona reports what it felt and where. It does not explain the underlying flaw or prescribe a fix. The moment it does, it stops being a reader and becomes an editor in a costume.

**Substrate entries should earn their place.** An entry belongs in a persona because it fixed an observed failure, and it should arrive with a regression case attached. The shipped persona meets that bar for four entries out of roughly seventy; the rest are seed. The gap is stated rather than papered over, because a substrate full of plausible untested entries is the failure mode this design is most prone to.

## License

See [LICENSE](LICENSE).
