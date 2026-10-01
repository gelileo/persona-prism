# Run — D4b leap years (second "clean" probe), persona run 1

**Draft:** `drafts/d4b-leap-years.md` (whole document)
**Skill version:** 588e831 — substrate still carried the incentive
**Runner:** fresh `general-purpose` subagent, no project context, no conversation history.
**Prompt:** the standard eval prompt in [`../README.md`](../README.md).
**Captured:** 2026-09-30.

Everything below the rule is the agent's output verbatim. Analysis of this run lives in [`../GATES.md`](../GATES.md), not here.

---

### confusion
> After one year, we are six hours ahead. After two years, twelve hours.

Ahead of what though. The calendar ran out of days before the Earth got all the way back around, so it seems like the calendar is the one that's behind. I keep having to flip it around in my head to make "ahead" work.

### question
> So every four years we add that day back.

If we're already a whole day ahead, why do we add a day? Adding one more would make us two days ahead. I thought you'd take one off.

### tangent
> People would be celebrating New Year's in the fall and nobody would know why.

So if it kept sliding, summer break would end up in December? I'd take that. Everybody standing outside in the snow on the last day of school.

### misreading
> It is about eleven minutes less than that.

So the extra day we stick onto February is eleven minutes too long.

### request
> and over centuries that error adds up too

You gave me ten days for forty years before. Give me one of those for this one. How many days off does it actually get?

### question
> Then check the two exceptions.

Which two? I only counted one thing to check, the years ending in 00. Is the divides-by-400 part the second one, or is that still part of the first one?

### question
> They just have fewer birthdays to point at.

What do they do on the years where February 29 isn't there at all? Do they pick February 28, or March 1, or does nothing happen?
