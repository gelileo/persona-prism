# Worked example: three passes over a science explainer

One draft, run three times through the `middle-schooler` persona with a revision between each. Every reaction below is verbatim from a real run by a fresh agent with no project context. Nothing is edited for effect, including the parts where the revision did not work.

Full artifacts: [`evals/middle-schooler/`](../evals/middle-schooler/). Per-reaction marking: [`MARKS.md`](../evals/middle-schooler/MARKS.md). Passes 1 and 2 were captured before a defect in the substrate was found and fixed; what that affects is set out in [`GATES.md`](../evals/middle-schooler/GATES.md).

---

## The comparison that justifies any of this

Before the persona existed, the same draft was given to a plain prompt:

> *Read the document. React to it as a middle school student would. What would confuse you?*

It returned fourteen articulate items (`evals/middle-schooler/baseline/d1-naive-prompt.md`). Here is its closing line:

> It's like the author got bored of explaining and started taking notes for themselves.

That is a good observation. No twelve-year-old has ever made it. The naive prompt produces an editor's report in a student's voice: it ranks its own confusion, praises what worked, recommends fixes, and delivers a verdict on the author's process. It also read all 368 words attentively, which is the behavior of someone being paid to.

The persona, on the same draft, read two paragraphs and quit.

| | Naive prompt | Persona | What it measures |
|---|---|---|---|
| Confident misreadings | 0 | 2 | **the substrate** |
| Anchored to a quoted passage | 6 of 14 | 6 of 6 | the output contract |
| Hollow (fits any document) | 4 | 0 | the audit |
| Editorial content | 5 items | none | the skill's constraints |
| Finished the document | yes | no | — |

Only the first row tests what this project claims; the rest are enforced by the format and any prompt could be given them. Persona figures are from `runs/d1-run3.md`, the clean run — see [`GATES.md`](../evals/middle-schooler/GATES.md) for why earlier runs are not used.

The difference is in kind. The naive prompt reports **what confused it**. The persona reports **what the reader now believes**, which is a different and more alarming thing to learn about your writing.

---

## Pass 0 — the original draft

*(Reactions below from `runs/d1-run3.md`.)*

`drafts/d1-photosynthesis.md` opens by announcing that plants "manufacture their own food out of thin air and light." The reader's answer:

> **misreading** — *they manufacture their own food out of thin air and light*
> Air isn't a thing you can make something out of though — air is just nothing, it's empty. So the food still comes up out of the dirt through the roots, and the light is the part that helps it grow.

The draft's entire thesis was read, rejected, and replaced with the misconception the draft exists to correct. Then:

> **disengagement** — *from across the electromagnetic spectrum, though only certain wavelengths are actually absorbed*
> I stopped here. Electromagnetic spectrum, wavelengths — I don't know any of these words and there's like three of them in one sentence. I checked my phone and didn't go back.

Six reactions, covering the first two paragraphs. The remaining 80% of the draft — ATP, glucose, the thylakoid, the factory analogy — was never read, so it produced nothing. **That is the finding.** Polishing paragraph six would have been wasted work.

## Pass 1 — fix the opening

The revision drops the jargon, meets the soil belief head-on with a weighing argument, and replaces "radiation from across the electromagnetic spectrum" with a plain-language description.

The reader finished the document. Ten reactions, spread across all of it, including the last line. **The disengagement was fixed, and reaction count went up.** A shrinking list is the convergence signal only once the reader is reaching the end; before that, more reactions mean more of the document is being read at all.

The core misconception, though, defended itself:

> **misreading** — *Weigh the soil in a pot, grow a plant in it for a year, and weigh the soil again. It is almost exactly the same.*
> The soil stayed the same because you keep watering it. The water puts the food back into the dirt so it doesn't run out. That's the whole reason you have to water a plant instead of just leaving it alone.

The reader was handed a measurement that contradicts the belief and invented a mechanism to rescue it. No adult reviewer predicts this. It is also exactly what real students do.

## Pass 2 — attack the belief with numbers

The second revision replaces the vague weighing argument with the willow-tree experiment: a tree gains 164 pounds while its soil loses two ounces.

The belief did not break. It **retreated**:

> **misreading** — *The soil had lost two ounces.*
> So it did eat some of the dirt, just not very much. Two ounces is small but it's not zero, so the dirt is still part of it.

From "plants eat soil" to "plants eat a little soil." That is real movement, and it is not the same as success.

Meanwhile the new text created new misreadings that did not exist before:

> **misreading** — *So a tree is mostly air*
> Mostly air means a tree is mostly empty inside. So a big tree trunk is kind of hollow and that's why it isn't as heavy as it looks.

> **misreading** — *Wood is built from it. So is a leaf, a stem, and a potato.*
> Wood is made of sugar, so a tree would taste sweet if you licked it. That's why potatoes taste like that, they're the sugar part.

## Where it stands

Three passes. The reader went from quitting in paragraph two to finishing; the central misconception moved from confidently held to partially conceded; and each revision introduced friction of its own. A fourth pass would target "mostly air" and the sugar-taste inference.

This is what the loop actually looks like. It does not converge in one round, revisions create new problems, and the honest version of a worked example shows that rather than a tidy before-and-after.

## The thing that surprised us

An early draft in the eval set was written specifically to have no problems — every term defined on first use, short sentences, a concrete example per idea. It was clean by every readability rule an adult can state. It produced eight reactions, three of them confident misreadings:

> **misreading** — *What it gives off is gas — the same gas you breathe out.*
> So the bubbles have air in them, and air isn't really anything. The bread is puffed up with nothing inside it.

A second attempt at a problem-free draft produced seven.

Readability is a property of the text. Comprehension is a property of the collision between the text and a particular head, and you cannot inspect the text to find it.
