# Run — D5 enterprise PRD, persona run 1

**Draft:** `drafts/d5-enterprise-prd.md` (whole document)
**Skill version:** 588e831 — substrate still carried the incentive
**Runner:** fresh `general-purpose` subagent, no project context, no conversation history.
**Prompt:** the standard eval prompt in [`../README.md`](../README.md).
**Captured:** 2026-09-30.

Everything below the rule is the agent's output verbatim. Analysis of this run lives in [`../GATES.md`](../GATES.md), not here.

---

### misreading
> Analytics currently runs against a shared warehouse with row-level filtering applied at query time.

Everybody's stuff is kept in one big warehouse together, so it's all sitting on shelves in the same building and they sort out whose is whose when somebody comes to pick something up.

### request
> Combined ARR at risk is material.

Just say the number of dollars. I can't tell if that's like a thousand dollars or a million dollars, and those are really different.

### misreading
> Any query path that bypasses the ORM — ad hoc reporting, the export job, the internal support console — has direct warehouse access with no tenant predicate.

The support console is a console they keep in the office, and it's plugged straight into the warehouse, so that one can pull up anything in there.

### confusion
> We have no evidence of cross-tenant exposure, but we also cannot produce evidence of its absence, which is what the security questionnaires ask for.

They say nothing got out, and then right after they say they can't show that nothing got out. Those sound like the same thing to me. I don't get how you can say it but not show it.

### misreading
> Migrate existing tenants in waves ordered by contract value.

Waves keep coming once they start and you can't stop them, so after the first one starts, the rest just come whether anybody is ready or not.

### misreading
> Churn in the enterprise segment reduced against a 90-day baseline

That one's the bad one. Everything else on the list stays the same or goes up, and that one goes down, so that's the part where it gets worse.

### confusion
> No increase in p95 query latency

I don't know what p95 is and I don't know what latency is. I can't even tell if this one is something they want or something they don't want.

### tangent
> Migration requires downtime per tenant, currently estimated at 40 minutes.

40 minutes of it just being off. That's way longer than any loading screen I've ever sat through. I'd have given up and gone and done something else like four times.

### tangent
> Our SLA permits a monthly maintenance window, but two accounts have negotiated custom terms that do not.

A window you're only allowed to open once a month. I keep picturing a real window on the side of the building and everybody has to climb through it before it shuts again.

### misreading
> Per-tenant credentials mean per-tenant pools, and at current tenant count we exceed the connection limit on the primary instance.

They have more pools than the limit lets them have. Having more of something than you're allowed to have sounds like they're ahead of everybody, not like something's wrong.

### tangent
> Provisioning and the proxy land first, behind a flag.

Behind a flag. A flag is flat and thin, so it wouldn't hide anything. You'd see the whole thing sticking out around the edges.

### confusion
> the questionnaire answer changes from "compensating controls" to "architecturally enforced."

I don't know what either of those two things in the quote marks means, so I can't tell which one is the one you want to be.

### misreading
> Every runbook that touches the warehouse needs rewriting

There are books in the warehouse too, and every single one of them has to get written over again by hand before they're done.

### disengagement
> The messaging differs: for the flagged accounts this closes a renewal blocker, and for everyone else it is a maintenance window with no visible benefit, which is a harder message.

I stopped here. This part and the part right before it are both just people telling other people things, and there's nothing left in it I can picture. I didn't read the rest.
