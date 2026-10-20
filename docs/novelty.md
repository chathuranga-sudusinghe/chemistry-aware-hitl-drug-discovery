# Novelty Hypotheses

## Status

**PROPOSED.** These are research-positioning hypotheses, not established novelty claims.

## N1 — Chemistry-aware expected utility of expert intervention

Instead of prioritizing human review only by predictive uncertainty or information gain, the project proposes to estimate whether medicinal-chemist intervention is likely to resolve a chemically consequential ambiguity and materially improve a lead decision.

A conceptual form is:

`review utility = probability of decision change × value of correction − review cost`

This is not a final mathematical definition. The meaning of decision change, correction value, and review cost must be operationalized and validated.

## N2 — Separate escalation and prioritization

The project proposes two linked but distinct decisions:

1. **Escalation:** whether a candidate requires expert review.
2. **Prioritization:** how review-worthy candidates should be ordered under a limited review budget.

## N3 — Chemistry-grounded review signals

Review utility may integrate chemically meaningful signals such as SAR consistency, scaffold novelty, structural liabilities, synthetic feasibility, ADMET trade-offs, target-specific interaction evidence, and calibrated model uncertainty.

## N4 — Structured medicinal-chemistry feedback

Human feedback may capture why a candidate is accepted, rejected, or deferred, rather than using only a binary label. Candidate categories include SAR inconsistency, reactivity/stability concern, metabolic liability, toxicity concern, synthetic concern, target-interaction concern, and promising scaffold/analogue evidence.

## N5 — Budget-aware evaluation

The project proposes to evaluate scientific decision quality as a function of expert-review capacity rather than reporting predictive performance alone.

Potential outcome concepts include useful decision changes per expert review and performance-versus-review-budget curves. Final metrics remain open.

## Explicit non-novel components

The following are established ideas and must not be presented as the project's novelty by themselves:

- HITL molecular design [REF-001, REF-002];
- active learning / information-gain selection [REF-002];
- tool-using chemistry agents [REF-003];
- autonomous LLM chemistry systems [REF-004];
- conformal prediction for drug-discovery uncertainty [REF-005];
- selective prediction / abstention in chemical ML [REF-006].
