# Authoring a persona

A PersonaPrism persona is a Claude Agent Skill with a substrate. The skill is short and mostly procedure. The substrate is the persona.

Every example below is verbatim from the shipped [`middle-schooler`](../skills/middle-schooler/) persona and from real runs in [`evals/middle-schooler/`](../evals/middle-schooler/). None are invented for illustration.

## The idea

Do not write down what the reader may not know. Write down the world the reader reasons **from**.

A forbidden-word list suppresses vocabulary and leaves the reasoning intact. Ban *photosynthesis* and you get a reader who says "the plant drinks sunlight to make its food" — the concept delivered whole, the word absent, and the persona sounding more authentic than before. You cannot blocklist your way out of this, because the model can paraphrase around any word.

A world model cannot be paraphrased around. If the reader believes plants eat soil, believes air is nothing, and has never seen a factory floor, those beliefs collide with the draft on their own. You do not forbid the right answer. The reader simply does not have it.

## Layout

```
skills/<persona>/
  SKILL.md              # identity, procedure, audit, output contract
  references/
    substrate.md        # the eight fields — loaded on demand
evals/<persona>/
  drafts/   baseline/   runs/   cases/   GATES.md
```

`SKILL.md` stays short because it is always in context. The substrate carries the weight and loads only when the skill runs.

## The eight fields

### What they know

**1. Experiential world** — concrete things this person has done, handled, or watched.

> Has played video games with health bars, loading screens, inventories, and progress meters.
> Has never had a job, signed anything, paid a bill, had a bank account, or attended a meeting.

This licenses analogy. An analogy reaching outside the list cannot land, and failing to land is itself a reaction. Told that work would ship *behind a flag*, the reader replied: *"A flag is flat and thin, so it wouldn't hide anything."*

**2. Formal instruction** — what school taught, and roughly when. Bounds concepts, not words.

> Has met the *word* atom. Has not been taught atomic structure, bonding, or molecules as assemblies.

**3. Vocabulary, in three tiers** — owned, recognized, unknown.

The middle tier does the work a binary allowed/forbidden list cannot, and it is the field most often left out. Record the **wrong meaning attached**, not just the word:

> **chemical** → "a dangerous liquid, usually in a bottle." Not a category that includes water.
> **fix** (as in *carbon is fixed*) → "repair something broken."

### How they think

**4. Wrong beliefs** — held with confidence, stated flatly, surviving contradiction.

This field does more than the other seven combined. It turns a confused reader into one who reaches a **wrong conclusion** — the difference between "I didn't understand" and "I understood, and what I now believe is false."

Given a draft that explicitly states a crumpled sheet and a flat sheet *"weigh exactly the same amount"*:

> When you crumple paper you squish it all together, so the ball is heavier in your hand than the flat one. That's why it falls faster.

Write beliefs so they survive being corrected once. A belief that yields the first time the text disagrees with it was never a belief.

**5. Reasoning moves** — what inference is available, and what is not.

> Cannot: chain three inferences. Cannot: hold two variables changing at once.

The second line produced this, unprompted:

> Gets a stronger pull, needs a stronger pull. Those are the same words going both ways and I can't hold both of them in my head at the same time.

### How they respond

**6. Attention budget** — how long before disengagement, what causes it, what recovers it.

> Disengages at: a paragraph with three or more unknown words; a sentence over about 30 words; a second consecutive paragraph with nothing concrete in it.
> When disengaged, does not resume.

Without this field a persona finishes everything, which no real reader does. With it you learn where your document lost its audience. On a 2,627-word administrative history the reader stopped at word 729 and reported why:

> That's all one sentence and I lost the end of it, and there's nothing in this part or the part before it that I can picture. I was still thinking about the planes. I didn't go back.

Nothing from the remaining 1,898 words appears in that run — which is the point. Polishing paragraph twenty would have been wasted work.

**7. Posture** — whether confusion is admitted or competence performed, and what the reader does *not* care about.

> Will admit confusion openly. Says "I don't get it" without embarrassment.
> Does not care about importance claims. Being told something is "the most important reaction on Earth" produces no reaction at all.

That second line is a suppressor, and suppressors are as load-bearing as triggers. The draft's opening boast produced silence, exactly as specified, while the sentence beside it produced a misreading.

**8. Reaction vocabulary** — which reaction types this persona may emit. Per-persona, never global.

> `question`, `confusion`, `request`, `misreading`, `disengagement`, `tangent`.
> Not available: critique, methodology, recommendation, praise, summary, or any judgment of the writing as writing.

`tangent` earns its place — it is the second most frequent type across the shipped runs, and it catches what a reader carries away rather than what they stumbled on:

> So all the air I breathe is plant garbage. Plants throw it out and I breathe it in. That's kind of gross and I'm going to think about it now every time I breathe.

## The skill file

`SKILL.md` carries, in order: a two-sentence identity; an instruction to read the substrate in full before reacting; the procedure; the reaction vocabulary; the output contract; the constraints.

The output contract is rigid, and it is what makes a run machine-readable:

```markdown
### <reaction type>
> <the passage that provoked it>

<the reaction, first person, in character>
```

Nothing else. No severity, no ranking, no diagnosis, no suggested fix.

### The audit

Before emitting, each candidate reaction is checked. The first question is the one that matters:

1. **Which substrate entry licenses this?** Name it. A reaction that cannot cite one is invented and gets dropped.
2. Does it use vocabulary above the owned tier?
3. Is it hollow — would it fit any document?
4. Is its type in this persona's reaction vocabulary?

Question 1 is what makes the substrate binding rather than decorative. Questions 2–4 are vocabulary and format checks, and vocabulary checks alone are exactly what this approach exists to replace.

A leak is not only a forbidden word. Reasoning correctly from a concept you do not have is a leak even when the word never appears.

## The loop

Do not write a substrate in one sitting. Entries invented up front sound plausible and never fire; the ones that matter are discovered.

1. Run the persona on a real draft.
2. Mark every reaction **authentic**, **leaked**, or **hollow**.
3. For each leak or hollow reaction, write the smallest entry that would have produced the right reaction instead.
4. Keep the passage and expected reaction as a regression case.
5. Re-run. Confirm it fixed that case and broke nothing else.

**An honest note about the shipped persona:** most of its substrate is seed — written up front from curriculum documents and the misconception literature, not discovered by the loop. Four entries were earned by observed failures and carry cases. That is a weaker provenance than this section prescribes, and the gap is recorded in [`GATES.md`](../evals/middle-schooler/GATES.md). Treat the loop as the standard to work toward, and treat a large unearned seed as debt rather than as a finished substrate.

## The three ways substrates go wrong

**Too narrow.** An entry that fixes its case only by naming that case's specific content has memorized an answer. Generalize it to the reader trait it reveals.

**Too broad.** A prose paragraph describing how the reader thinks in general licenses anything, which means it licenses nothing. Every entry is one concrete line.

**Ungrounded but plausible.** The one to watch for. The shipped persona once reached for "the bottles under our sink" when no entry mentioned household chemicals. The reaction was *right* — and licensed by nothing. The model was drawing on its own idea of childhood and citing the substrate afterward. That is how a substrate becomes decorative: entries pass review because the author agrees with them, not because they did any work.

Reviewing for plausibility will never catch this. Review by asking, for each reaction, **which line licensed it** — and go look at the line.

## Two rules for the skill file itself

**Never tell a persona which of its reactions you value.** An early version of `middle-schooler` called misreadings "the most useful thing you can produce" and called tangents "the most useful thing in the run." A persona that knows the scoring produces the favoured type, and a manufactured misreading is worse than none: it is a confident wrong statement the creator will try to fix in a draft that never caused it. Describe the *condition* under which a reaction occurs and say nothing about its worth.

**The substrate is prompt, not documentation.** This is where the project's own worst defect came from. The praise was removed from `SKILL.md` and left in `substrate.md`, which the persona reads in full before every run — so for most of the build it was still live, and the falsification test that was supposed to prove otherwise had never actually been performed. Anything you write in a substrate as a note to yourself is an instruction to the persona. Rationales, priorities, explanations of why an entry matters: all of it is read as direction. See [`cases/004`](../evals/middle-schooler/cases/004-incentive-survived-in-substrate.md).

**Never let the persona explain itself.** A reaction carries its anchor and nothing else. The moment a persona explains why the writing caused its reaction, it has stopped being a reader and become an editor in a costume — and you are back to the generic review the project exists to replace.

## One thing worth knowing before you start

A draft can satisfy every readability rule an adult can name — every term defined on first use, short sentences, a concrete example per idea — and still hand this reader three false conclusions. The first "clean" draft written for the eval set was written specifically to produce no reactions. It produced eight:

> **misreading** — *What it gives off is gas — the same gas you breathe out.*
> So the bubbles have air in them, and air isn't really anything. The bread is puffed up with nothing inside it.

A second attempt produced seven. A third — nine sentences about filling a dog's water bowl — produced four.

Readability is a property of the text. Comprehension is a property of the collision between the text and a particular head, and you cannot inspect the text to find it.
