# PRD: Tenant Isolation for Workspace Analytics

## Background

Analytics currently runs against a shared warehouse with row-level filtering applied at query time. Three enterprise accounts in the current renewal cohort have flagged this during security review, and one has made isolation a condition of renewal. Combined ARR at risk is material.

## Problem

Row-level filtering is enforced in the application layer. Any query path that bypasses the ORM — ad hoc reporting, the export job, the internal support console — has direct warehouse access with no tenant predicate. We have no evidence of cross-tenant exposure, but we also cannot produce evidence of its absence, which is what the security questionnaires ask for.

## Proposal

Move to per-tenant schemas with credentials scoped at the connection level. Provision on tenant creation. Migrate existing tenants in waves ordered by contract value.

## Non-goals

Per-tenant encryption keys. Regional data residency. Both are frequently requested and both are separate efforts.

## Success metrics

- SOC 2 evidence generated without manual attestation
- Churn in the enterprise segment reduced against a 90-day baseline
- No increase in p95 query latency
- Integration surface unchanged for existing API consumers

## Risks

Migration requires downtime per tenant, currently estimated at 40 minutes. Our SLA permits a monthly maintenance window, but two accounts have negotiated custom terms that do not. Legal review pending.

Connection pool exhaustion is the main technical risk. Per-tenant credentials mean per-tenant pools, and at current tenant count we exceed the connection limit on the primary instance. Mitigation is a proxy layer, which adds a dependency to the critical path.

## Sequencing

Provisioning and the proxy land first, behind a flag. Migration waves follow. Decommissioning the shared path is gated on the last wave completing, which is the point at which the questionnaire answer changes from "compensating controls" to "architecturally enforced."

## Rollout and support impact

Support tooling assumes a single connection string. Every runbook that
touches the warehouse needs rewriting, and the on-call rotation needs
retraining before the first wave, not after it. We have historically
under-resourced this and paid for it in escalations.

Customer communication is owned by the account teams for the three
flagged accounts and by lifecycle marketing for everyone else. The
messaging differs: for the flagged accounts this closes a renewal
blocker, and for everyone else it is a maintenance window with no
visible benefit, which is a harder message.

## Open questions

Whether the support console gets a scoped credential per tenant or a break-glass path with audit logging. Product and security disagree. Escalating at the next architecture review.
