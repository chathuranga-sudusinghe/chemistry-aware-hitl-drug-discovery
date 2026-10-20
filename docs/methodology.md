# Proposed Methodology

## Status

**PROPOSED — no implementation or experiment is authorized by this document.**

## Conceptual pipeline

1. Define a target-specific, multi-objective lead-optimization task.
2. Curate approved molecular and, if applicable, protein-structure data.
3. Train fair predictive baselines and graph-based molecular models.
4. Estimate calibrated uncertainty and applicability-domain evidence.
5. Compute chemistry-aware signals such as SAR consistency, scaffold novelty, structural liabilities, synthetic feasibility, and ADMET conflicts.
6. Estimate whether expert review is required (escalation).
7. Rank escalated candidates by expected expert-review utility (prioritization).
8. Allocate a fixed review budget.
9. Collect or simulate clearly labelled review outcomes according to the approved protocol.
10. Evaluate decision quality, reliability, review efficiency, and robustness.

## Candidate predictive models

**PROPOSED:**

- classical molecular fingerprints + Random Forest / gradient-boosted trees as strong non-neural baselines;
- Message Passing Neural Network (MPNN) / Directed MPNN family for 2D molecular prediction;
- a 3D equivariant GNN only if target/pose geometry is necessary and data quality supports it;
- a SMILES/sequence model only as an evidence-backed comparator, not because transformer architecture is inherently preferable.

Model choice must follow the task and dataset rather than the preferred technology.

## Candidate uncertainty methods

Potential methods include:

- deep ensembles;
- conformal prediction;
- inter-model disagreement;
- distance/applicability-domain measures;
- representation-space or chemical-similarity distance.

The protocol must distinguish predictive uncertainty from ordinary variation across random seeds.

## Proposed HITL policy

The current concept uses two stages:

### Stage A — escalation

Determine whether the system should:

- proceed autonomously;
- reject/deprioritize autonomously;
- request additional evidence;
- defer to expert review.

### Stage B — review prioritization

Among candidates requiring review, assign priority according to the expected scientific utility of expert intervention under a fixed review budget.

## Candidate baselines

The final study should consider, where feasible:

- fully autonomous / no human review;
- review-all upper-bound/reference condition;
- random review;
- highest predictive uncertainty first;
- model-disagreement ranking;
- conformal-uncertainty ranking;
- highest predicted objective/activity first;
- information-gain/active-learning acquisition strategy such as EPIG where applicable [REF-002];
- fixed-threshold escalation;
- proposed chemistry-aware review-utility policy.

## Review-budget analysis

Candidate budgets may include multiple fractions (for example 1%, 5%, 10%, 20%, 50%), but exact budgets must be justified and fixed in the protocol before final evaluation.

## Human validation strategy

Because large-scale expert annotation may be impractical, the study may use staged evidence:

1. retrospective historical outcomes where scientifically defensible;
2. clearly labelled simulated oracle feedback for development;
3. rule-derived chemistry checks for narrowly defined phenomena;
4. real expert review on a smaller, pre-specified subset.

These evidence types must never be conflated.

## Agent / RAG layer

The LLM agent may coordinate approved chemistry tools and retrieve literature/database evidence. It should provide traceable explanations and provenance, but it is not the scientific uncertainty estimator or the primary endpoint predictor by default.
