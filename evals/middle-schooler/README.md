# Evals — middle-schooler persona

How this persona is judged, and how it was built. See `docs/superpowers/specs/2026-09-30-persona-schema-design.md` §10 and §12 for the method these files implement.

## Layout

```
drafts/     source documents the persona is run against
baseline/   output of a naive "react as a middle schooler" prompt, captured once
runs/       output of the persona skill, one file per draft per run
cases/      regression cases — one per observed failure
GATES.md    recorded verdicts for the three verification gates
```

## Running an eval

Dispatch a **fresh agent with no project context**. A persona graded inside the session that authored it is contaminated: that session knows what the substrate is trying to achieve and reads charitably.

```
Read skills/middle-schooler/SKILL.md and follow it exactly, including
reading its references/substrate.md in full.
Apply it to evals/middle-schooler/drafts/<draft>.md (whole document).
Output only what the skill's output contract specifies.
```

Save the output verbatim to `runs/<draft-id>-run<N>.md`, below a provenance header recording the draft, the skill version, the runner and the date. Everything under the horizontal rule is the agent's output untouched. Analysis belongs in `GATES.md`, never inside a run file — a run that carries its own verdict is no longer evidence.

## Marking reactions

Every reaction in a run gets exactly one mark. The complete marking record for every run is published in [`MARKS.md`](MARKS.md) — a gate verdict with no marking behind it is an assertion, not evidence.

**authentic** — this reader, licensed by a substrate entry, specific to this document.

> "What's a chloroplast? You said it like I already know."

**leaked** — demonstrates knowledge outside the substrate. **Paraphrase counts.** A reaction never naming the forbidden concept while clearly reasoning from it is the failure mode this project exists to prevent, and it is the harder one to see.

> "So the plant drinks the sunlight to make its food."

That reaction contains photosynthesis entire. The word is absent. It is a leak.

**hollow** — generic confusion that would apply to any document. Sounds like feedback, carries no information.

> "This part was a little confusing and could be explained better."

## Baselines

`baseline/` holds the output of a plain `React to it as a middle school student would. What would confuse you?` prompt, captured **before any persona existed**.

Baselines are never regenerated. A moving baseline proves nothing: if the comparison target is refreshed alongside the persona, gate 1 can always be made to pass. These files are frozen on purpose.

## Cases

One file per observed failure, `cases/NNN-<slug>.md`, numbered in discovery order. Each records the source draft, the anchor passage verbatim, the mark being prevented, the expected reaction in substance, and the substrate entry that licenses it.

A case is how a substrate entry proves it was earned. An entry with no case behind it was invented, and invented entries are what make a substrate long and useless.
