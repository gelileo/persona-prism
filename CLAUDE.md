# PersonaPrism — working context

A library of Claude Agent Skills, each one a calibrated human reader. A persona is pointed at a draft and returns the reactions that reader would genuinely have, anchored to the passages that provoked them. Those reactions feed a content-authoring agent, which revises; the persona runs again. The reaction list shrinking is the convergence signal.

Public open-source project. Strangers will read these files and write their own personas from them, so the schema and its documentation are product surface, not internal scaffolding.

## Current state

**One persona shipped:** `skills/middle-schooler/` (US grade 7), built to depth and verified against three gates. Eval record in `evals/middle-schooler/`; public docs in `docs/authoring-a-persona.md` and `docs/worked-example.md`.

Design spec: `docs/superpowers/specs/2026-09-30-persona-schema-design.md`. Build plan: `docs/superpowers/plans/2026-09-30-middle-schooler-persona.md`. Read the spec before changing the schema.

**Do not write a second persona yet.** The schema is cheap to change while one persona uses it and expensive once nine do. Known open work is listed in `evals/middle-schooler/GATES.md` under the unexercised and partially-covered gates.

## Locked decisions

| | |
|---|---|
| v1 scope | Persona skills + authoring schema + one worked example |
| Deferred | Batch CLI, CI/CD gating, interactive persona generator, domain-specific substrate packs |
| Artifact format | Real Agent Skills — `skills/<persona>/SKILL.md` with frontmatter and `references/`. Claude-native. A flat-prompt export for other platforms is secondary |
| Persona model | Hand-crafted presets. The five-parameter matrix ships as documentation, not as a generator |
| Output | Reactions anchored to their trigger passage. No diagnosis, no prescribed fix |
| Iteration | Every run is a fresh reader. No memory, no diffing across runs |
| Leakage approach | Substrate-first (B), with a pre-response cognitive audit retained as a cheap second net (A). Two-stage adversarial auditing (C) is deferred to the CLI phase |

## Why substrate, not blocklists

A FORBIDDEN concept list suppresses vocabulary, not reasoning. A persona banned from "photosynthesis" will say "the plant drinks sunlight to make its food," pass its own audit, and have leaked the whole concept while sounding *more* authentic. This is the failure mode most likely to make the project look like it works when it doesn't.

So a persona is specified positively — the world it reasons from: concrete experiences it has had, what it has been formally taught and when, the vocabulary it owns, the reasoning moves available to it, its attention budget, and critically the things it believes that are **wrong** (heavier objects fall faster, heat is a fluid, a bigger number is always better). Every reaction must be licensable by that substrate. Friction is emitted where the text cannot be assimilated into it.

Wrong beliefs are load-bearing, not decoration: they are what produce confident misreadings, and a confident misreading is the highest-value output a persona can produce — it proves the text taught the wrong thing rather than merely failing to teach.

## Reactions are not only questions

The output vocabulary includes questions, confusion statements ("I don't know what a supply chain is"), requests (for an example, an illustration, a number, a citation), and misreadings. **Which reaction types a persona can emit is part of its calibration, not a global list.** A third grader asks for a picture and never asks about methodology. A CTO asks for a number and a timeline and never says "I'm confused" — they say "this is hand-wavy."

## How personas get built

One persona to full depth before any others exist. Nine shallow personas teach nothing; one deep one teaches what the schema must be, and the format is cheap to change while only one persona uses it.

Then grow the substrate from observed failures rather than imagination:

1. Run the persona on a real draft.
2. Mark each reaction: **authentic**, **leaked** (knew something it shouldn't), or **hollow** (generic confusion any model would emit).
3. For each leak or hollow reaction, write the smallest substrate entry that would have produced the right reaction instead.
4. Keep the passage and expected reaction as a regression case.
5. Re-run; confirm it fixed that case and broke nothing else.

Step 4 accumulates the eval suite. That suite is what the deferred adversarial auditor will need, and it is what turns "PersonaPrism prevents knowledge leakage" from a claim into evidence.

Substrate is layered so later personas are cheap: a class-level base plus a persona-level delta. Agent Skills resolve `references/` relative to their own directory, so sharing a base across skills needs duplication, a symlink, or a small build step — unresolved, to be decided in the spec.

## Rules

- Do not add a substrate entry because it sounds plausible. It goes in because it fixed an observed failure, and it arrives with a regression case.
- Do not let a persona explain itself. Reactions carry an anchor and nothing else — no diagnosis, no rewrite suggestion.
- Do not give a persona memory of previous runs, or let it read a diff.
- Do not build domain-specific substrate packs in v1. The substrate specifies the reader's apparatus, which is largely domain-general; the model already knows what a seventh-grade curriculum contains.
- Do not start the CLI, CI integration, or the persona generator until the persona library is good.
- Do not write a second persona until the first is genuinely finished.

## Conventions

Specs live in `docs/superpowers/specs/YYYY-MM-DD-<topic>-design.md`. Persona skills will live under `skills/<persona-name>/`. No build system, test runner, or dependencies exist yet — do not assume any.
