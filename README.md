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

**One persona shipped: `middle-schooler` (US grade 7).** Built to depth and verified against three gates, with the full eval record published in `evals/`.

- [`skills/middle-schooler/`](skills/middle-schooler/) — the persona: a short skill file and the substrate it reasons from
- [`docs/authoring-a-persona.md`](docs/authoring-a-persona.md) — the eight fields, the build loop, and the two ways substrates go wrong
- [`docs/worked-example.md`](docs/worked-example.md) — one draft, three revision passes, every reaction verbatim
- [`evals/middle-schooler/`](evals/middle-schooler/) — drafts, frozen baselines, every run, and the recorded gate verdicts

The second persona is not written yet, on purpose: the schema is cheap to change while one persona uses it and expensive once nine do.

Deferred: the batch CLI, CI/CD gating, and an interactive persona generator. Persona quality has to be settled before there is any point automating it.

### What the gates found

**Against a naive prompt on the same draft**, the persona produced 3 confident misreadings to the baseline's 0, anchored 6 of 6 reactions to a quoted passage against 6 of 14, and emitted no editorial content where the baseline emitted five items of it. The naive prompt reports what confused it; the persona reports what the reader now believes.

**No leaks** across twelve runs on eleven drafts — including paraphrased leaks, which is the harder case and the one a forbidden-word list cannot catch.

**One finding worth stating plainly:** we could not write a draft this reader has no reaction to. Three attempts, including nine sentences of instructions for filling a dog's water bowl, produced eight, seven, and four reactions — every one anchored, none manufactured. Readability is a property of the text; comprehension is a property of the collision between the text and a particular head.

## Design commitments

**Substrate, not blocklists.** A persona isn't defined by a list of words it may not say — that suppresses vocabulary while leaving the reasoning intact, and you get a reader who says "the plant drinks sunlight to make food" and has leaked the entire concept while sounding more authentic than ever. Instead each persona specifies the world it reasons *from*: what it has experienced, what it has been taught, the reasoning moves available to it, and the things it believes that are wrong.

**Reactions carry no diagnosis.** A persona reports what it felt and where. It does not explain the underlying flaw or prescribe a fix. The moment it does, it stops being a reader and becomes an editor in a costume.

**Substrate entries earn their place.** Nothing goes into a persona because it sounds plausible. It goes in because it fixed an observed failure, and it arrives with a regression case attached.

## License

See [LICENSE](LICENSE).
