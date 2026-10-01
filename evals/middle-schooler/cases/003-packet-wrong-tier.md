# 003 — a word in the wrong vocabulary tier

**Source:** `runs/d1-revised-run1.md`
**Mark prevented:** leaked (against an explicit entry)

**Anchor passage**

> This all happens inside the leaf, in tiny green packets too small to see without a microscope.

**Reaction as emitted**

> I don't know what a packet means here. I've heard that word about phones and it didn't mean a little bag.

**The defect**

`packet` was listed in the **Unknown** tier, which the substrate defines as "no meaning attached at all." The reader then reported a prior association with phones. That is a contradiction of an explicit entry, and it is the subtlest kind of leak: not knowledge from outside the substrate, but knowledge the substrate specifically said this reader does not have.

Found by the final review, not by the build loop — the reaction reads naturally, and reviewing for plausibility rather than for licensing would pass it every time.

**Expected reaction in substance**

The same reaction, licensed: the reader has heard the word in a phone or internet context and attaches nothing further to it.

**Fix**

Moved `packet` from Unknown to Recognized with the meaning the reader actually reported.
