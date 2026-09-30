# Authoring a persona

A PersonaPrism persona is a Claude Agent Skill with a substrate. The skill is short and mostly procedure. The substrate is the persona.

This guide describes the eight fields, the loop that fills them, and the two ways substrates go wrong. Every example below is taken from the shipped `middle-schooler` persona and from real eval runs, not invented for illustration.

## The idea

Do not write down what the reader may not know. Write down the world the reader reasons **from**.

A forbidden-word list suppresses vocabulary and leaves the reasoning intact. Ban *photosynthesis* and you get a reader who says "the plant drinks sunlight to make its food" — the concept delivered whole, the word absent, and the persona sounding more authentic than before. You cannot blocklist your way out of this, because the model can paraphrase around any word.

A world model cannot be paraphrased around. If the reader believes plants eat soil, believes air is nothing, and has never seen a factory floor, those beliefs will collide with the draft on their own. You do not have to forbid the right answer. The reader simply does not have it.

## The eight fields

### What they know

**1. Experiential world** — concrete things this person has done, handled, or watched.

> Has played video games with health bars, loading screens, inventories, and progress meters.
> Has never had a job, signed anything, paid a bill, had a bank account, or attended a meeting.

This is what licenses analogy. An analogy reaching outside the list cannot land, and failing to land is itself a reaction. When an enterprise PRD said work would ship *behind a flag*, the reader replied: *"A flag is flat and thin, so it wouldn't hide anything."*

**2. Formal instruction** — what school taught, and roughly when. Bounds concepts, not words.

> Has met the *word* atom. Has not been taught atomic structure, bonding, or molecules as assemblies.

**3. Vocabulary, in three tiers** — owned, recognized, unknown.

The middle tier does the work a binary allowed/forbidden list cannot do, and it is the field most often left out. Record the **wrong meaning attached**, not just the word:

> **chemical** → "a dangerous liquid, usually in a bottle." Not a category that includes water.
> **fix** (as in *carbon is fixed*) → "repair something broken."

### How they think

**4. Wrong beliefs** — held with confidence, stated flatly, surviving contradiction.

This field does more than the other seven combined. It is what turns a confused reader into one who reaches a **wrong conclusion**, which is the difference between "I didn't understand" and "I understood, and what I now believe is false."

Given a draft that explicitly states a crumpled sheet and a flat sheet *"weigh exactly the same amount"*, the reader answered:

> When you crumple paper you squish it all together, so the ball is heavier in your hand than the flat one. That's why it falls faster.

Write beliefs so they survive being corrected once. A belief that yields the first time the text disagrees with it was never a belief.

**5. Reasoning moves** — what inference is available, and what is not.

> Cannot: chain three inferences. Cannot: hold two variables changing at once.

The second line produced this, unprompted:

> Gets a stronger pull, needs a stronger pull. Those are the same words going both ways and I can't hold both of them in my head at the same time.

### How they respond

**6. Attention budget** — how long before disengagement, what causes it, what recovers it.

Without this field a persona finishes everything, which no real reader does. With it you learn where your document lost its audience — usually the single most useful thing a run tells you.

**7. Posture** — whether confusion is admitted or competence performed. A curious child says "I don't get it." A CTO says "this is hand-wavy." Same friction, different surface.

**8. Reaction vocabulary** — which reaction types this persona may emit. Per-persona, never global. A twelve-year-old asks for a picture and never asks about methodology.

## The loop

Do not write a substrate in one sitting. Entries invented up front sound plausible and never fire; the ones that matter are discovered.

1. Run the persona on a real draft.
2. Mark every reaction **authentic**, **leaked**, or **hollow**.
3. For each leak or hollow reaction, write the smallest entry that would have produced the right reaction instead.
4. Keep the passage and expected reaction as a regression case.
5. Re-run. Confirm it fixed that case and broke nothing else.

Stop when fresh drafts stop producing leaks and hollow reactions — not when the file reaches some length.

## The two ways substrates go wrong

**Too narrow.** An entry that fixes its case only by naming that case's specific content has memorized an answer. Generalize it to the reader trait it reveals.

**Too broad.** A prose paragraph describing how the reader thinks in general licenses anything, which means it licenses nothing. Every entry is one concrete line.

There is a third failure that looks like neither, and it is the one to watch for: a reaction that is *plausible for this kind of person* but licensed by **nothing in the substrate**. The shipped persona once reached for "the bottles under our sink" when no entry mentioned household chemicals. The reaction was right. It was also ungrounded — the model was drawing on its own idea of childhood and citing the substrate afterward. That is how a substrate becomes decorative: entries pass review because the author agrees with them, not because they did any work.

## Two rules for the skill file itself

**Never tell a persona which of its reactions you value.** An early version of `middle-schooler` called misreadings "the most useful thing you can produce," and got three in six reactions. A persona that knows the scoring will produce the favoured type, and a manufactured misreading is worse than none — it is a confident wrong statement the creator will try to fix in a draft that never caused it. Describe the *condition* under which the reaction occurs and say nothing about its worth.

(The falsification test is easy: remove the praise and re-run. If the reactions were licensed they survive. If they were produced to satisfy the instruction they vanish. In this case they survived.)

**Never let the persona explain itself.** A reaction carries its anchor and nothing else — no diagnosis, no cause, no suggested fix. The moment a persona explains why the writing caused its reaction, it has stopped being a reader and become an editor in a costume, and you are back to the generic review the project exists to replace.

## One thing worth knowing before you start

A draft can satisfy every readability rule an adult can name — every term defined on first use, short sentences, a concrete example per idea — and still hand this reader three false conclusions. That happened on the first "clean" draft written for the eval set, which was written specifically to produce no reactions and produced eight.

That is the whole argument for building personas this way. Readability is a property of the text. Comprehension is a property of the collision between the text and a particular head, and you cannot check it by looking at the text.
