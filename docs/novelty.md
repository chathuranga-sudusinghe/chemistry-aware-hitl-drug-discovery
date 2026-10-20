# Novelty Hypotheses

## Status

**Issue #2 Round 1 assessment with Round 1b corrections (2026-10-20).**

- **Status labels:**
  - **PROPOSED:** not yet assessed against sufficient evidence;
  - **SUPPORTED:** closest work documented and none addresses the claim;
  - **CHALLENGED:** substantial overlap found;
  - **REJECTED:** essentially done before.
- No hypothesis is SUPPORTED, because Round 1 did not reach saturation ([`literature-search.md`](literature-search.md) §8–9).
- These labels are research-positioning assessments, not established novelty claims. Changes to them require owner review.

## Summary

| ID | Hypothesis | Status | Remaining PROPOSED element |
|---|---|---|---|
| N1 | Chemistry-aware expected utility of expert intervention | **CHALLENGED** | Operationalising decision consequence for multi-objective small-molecule lead optimization |
| N2 | Separate escalation and prioritization | **CHALLENGED (partially)** | A two-stage design for medicinal-chemist review in lead optimization, shown by ablation to add value over a single ranking |
| N3 | Chemistry-grounded review signals | **CHALLENGED** (partially) | Lead-optimization-specific signals (SAR inconsistency, ADMET conflict, scaffold novelty) for review allocation |
| N4 | Structured medicinal-chemistry feedback | **CHALLENGED** | Using structured reasons to update escalation/prioritization policy |
| N5 | Budget-aware evaluation | **CHALLENGED** | Recommended for reclassification as an evaluation-design commitment rather than a novelty claim (owner decision) |

## N1 — Chemistry-aware expected utility of expert intervention

**Status: CHALLENGED.**

**Hypothesis:** instead of prioritizing human review only by predictive uncertainty or information gain, estimate whether medicinal-chemist intervention is likely to resolve a chemically consequential ambiguity and materially improve a lead decision.

The conceptual form is unchanged and remains a sketch, not a definition:

`review utility = probability of decision change × value of correction − review cost`

**Evidence:**
- Value of information has been defined as the expected reduction in total misclassification risk minus the cost of obtaining a human label [REF-018].
- Team expected utility including the human's verification cost and the cost of mistakes has been optimised [REF-031].
- Decision-theoretic allocation across machine, crowd, and expert tiers under a budget exists [REF-019].
- Decision-oriented selection of drug-discovery experiments (maximising the expected quality of the best compound found) exists [REF-040]. It selects experiments, not medicinal-chemist review.
- Goal-directed (not uncertainty-only) query selection already exists in HITL molecular design [REF-001, REF-002].

**What remains PROPOSED:** operationalising "decision consequence" and "benefit of review" for multi-objective small-molecule lead optimization, with chemistry-specific evidence, and showing measurable benefit over the baselines listed in [`literature-review.md`](literature-review.md) §9.

**Note for Issue #9:**
- The cited VOI formulations take an expectation over possible outcomes and include the cost of errors [REF-018, REF-031].
- Calling the second term "value of correction" presumes that review helps. Harmful or unproductive reviews and reviewer error must be represented when the utility is defined.
- Reviewer variability and inconsistency are documented [REF-010, REF-014, REF-015]. Those studies do not establish error against independent outcomes, so harmful or unproductive reviews and reviewer error remain risks requiring outcome-based assessment.

## N2 — Separate escalation and prioritization

**Status: CHALLENGED (partially).** General deferral and triage overlap substantially, but the exact escalation-then-prioritization decomposition for medicinal-chemist review in lead optimization was not found.

**Hypothesis:** two linked but distinct decisions:

1. **Escalation:** whether a candidate requires expert review.
2. **Prioritization:** how review-worthy candidates are ordered under a limited review budget.

**Evidence:**
- Deciding which instances go to a human is the core of learning to defer and triage [REF-025, REF-027, REF-028].
- Deferral has been formulated under expert work-capacity constraints with asymmetric error costs [REF-029] (peer-reviewed, TMLR 2024; synthetic experts), and the Bayes-optimal learn-to-defer solution has been derived under constraints including an expert-intervention budget [REF-041]. Online deferral under a budget has been studied as a contextual bandit [REF-044] (preprint).
- In the HITL drug-discovery studies read in full [REF-001, REF-002, REF-007], no separate per-candidate escalation decision was found.

**What remains PROPOSED:** a two-stage escalation-then-prioritization design for medicinal-chemist review in lead optimization. It must be shown by a controlled ablation to add value over a single combined ranking (cf. Codex finding M3).

## N3 — Chemistry-grounded review signals

**Status: CHALLENGED (partially).**

**Hypothesis:** review utility may integrate chemically meaningful signals such as SAR consistency, scaffold novelty, structural liabilities, synthetic feasibility, ADMET trade-offs, target-specific interaction evidence, and calibrated model uncertainty.

**Evidence:** in a retrospective analysis of regulatory (Q)SAR mutagenicity assessment, expert overturns concentrated in specific chemical classes and low-confidence predictions, and the authors suggest triage by chemical class and probability to improve review efficiency [REF-008]. That study does not implement or evaluate a triage policy.

**What remains PROPOSED:** using lead-optimization-specific signals (local SAR inconsistency, ADMET conflict, scaffold novelty, synthetic feasibility, target-interaction evidence) to allocate medicinal-chemist review. This was not found in Round 1.

## N4 — Structured medicinal-chemistry feedback

**Status: CHALLENGED.**

**Hypothesis:** human feedback may capture why a candidate is accepted, rejected, or deferred, rather than only a binary label. Candidate categories include SAR inconsistency, reactivity/stability concern, metabolic liability, toxicity concern, synthetic concern, target-interaction concern, and promising scaffold/analogue evidence.

**Evidence:**
- Tooling for chemistry-specific feedback on desired and undesired substructures and properties exists [REF-012].
- Standardised expert-review arguments mapped to prediction scenarios have been evaluated for correctness [REF-009].
- Clear evaluation categories were associated with convergence of expert judgements on synthesis routes [REF-038].

**What remains PROPOSED:** using structured chemistry reasons to update the escalation and prioritization policy, and testing whether this generalises beyond individual reviewers (cf. RQ5).

## N5 — Budget-aware evaluation

**Status: CHALLENGED.**

**Hypothesis:** evaluate scientific decision quality as a function of expert-review capacity rather than reporting predictive performance alone.

**Evidence:**
- Evaluating outcomes against query or experimental budgets is standard in HITL and active-learning studies [REF-002, REF-007, REF-021].
- Triage is analysed as a function of triage level [REF-028].

**Recommendation (owner decision):** reclassify N5 as an evaluation-design commitment for Issue #10 rather than a novelty claim.

## Explicit non-novel components

The following must not be presented as the project's novelty by themselves:

- HITL molecular design and goal-directed expert querying [REF-001, REF-002, REF-017];
- budgeted human–algorithm collaboration in drug-discovery experiment selection (arXiv v1 of REF-007);
- learned chemist-preference models [REF-010, REF-011];
- value of information net of labeling or verification cost [REF-018, REF-019, REF-031], and decision-oriented drug-discovery experiment selection [REF-040];
- learning to defer, selective classification, triage, and capacity- or budget-constrained deferral [REF-025 to REF-029, REF-041, REF-044];
- the idea of chemistry-aware triage of expert review (retrospective support and a published suggestion in regulatory toxicology) [REF-008];
- structured chemistry feedback tooling and argument categories [REF-009, REF-012];
- tool-using and autonomous chemistry agents [REF-003, REF-004]; HITL checkpoints in drug-discovery agents [REF-039] (preprint);
- conformal prediction and selective prediction in chemical ML [REF-005, REF-006].
