# Research Gap

## Status

**PROPOSED gap — requires continued literature validation.**

## Established adjacent work

The current literature confirms that several individual components already exist:

- human-in-the-loop de novo molecular design and preference/reward elicitation [REF-001];
- human-in-the-loop active learning for goal-oriented molecule generation, including Expected Predictive Information Gain (EPIG) [REF-002];
- chemistry agents that use expert-designed tools [REF-003];
- autonomous LLM-based chemical research systems [REF-004];
- conformal prediction for uncertainty and applicability-domain-aware drug-discovery modelling [REF-005];
- selective prediction / abstention in chemical toxicity modelling [REF-006].

Therefore, the project must **not** claim novelty merely from using HITL, active learning, uncertainty, an LLM agent, GNNs, multi-objective optimization, or chemistry tools.

## Candidate gap

The strongest current gap hypothesis is narrower:

> Existing work does not appear, from the currently verified literature set, to fully address chemistry-aware allocation of a **limited medicinal-chemist cognitive review budget** using the **expected scientific utility of expert intervention**, while explicitly separating the decision to escalate a candidate from the decision of how to prioritize review-worthy candidates.

The proposed distinction is:

- **Escalation:** should this candidate require expert review at all?
- **Prioritization:** among review-worthy candidates, which should receive limited expert attention first?

## Why uncertainty alone may be insufficient

A molecule can be highly uncertain yet scientifically unimportant to the current lead decision. Conversely, a moderately uncertain candidate may be high-value because it combines promising potency with a novel scaffold, conflicting ADMET evidence, an SAR anomaly, or a potentially consequential structural liability.

The project therefore proposes to study review utility as a decision problem, not merely an uncertainty-ranking problem.

## Candidate chemistry-aware evidence

Potential review-utility signals include:

- calibrated predictive uncertainty;
- model disagreement;
- applicability-domain / out-of-distribution evidence;
- scaffold novelty;
- local SAR inconsistency;
- structural alerts and reactive motifs;
- synthetic feasibility;
- ADMET conflicts;
- target-specific interaction evidence;
- expected consequence of an incorrect lead-selection decision.

No final weighting or formula is accepted yet.

## Claim boundary

A publication must not use a first-of-kind or definitive novelty claim until a broader structured search has covered expert attention allocation, value-of-information methods, active learning, selective prediction, medicinal-chemistry decision support, and agentic drug discovery.
