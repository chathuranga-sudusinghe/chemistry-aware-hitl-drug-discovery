# Research Gap

## Status

**PROPOSED gap — revised after the Issue #2 Round 1 literature search and Round 1b corrections (2026-10-20).**

The gap below is narrower than the original statement. It is based on a structured but non-exhaustive search ([`literature-search.md`](literature-search.md)) and remains a hypothesis.

## Established adjacent work

The individual components of the original framing already exist:

- human-in-the-loop de novo molecular design with optimization-aware query selection [REF-001];
- HITL active learning with goal-directed acquisition (EPIG targeted at top-scoring molecules) [REF-002, REF-017];
- human–algorithm collaboration for drug-discovery experiment selection under a fixed experimental budget, with expert approve/override (therapeutic peptides; arXiv v1 of REF-007 read in full, published version not assessed);
- decision-oriented selection of drug-discovery experiments using the knowledge-gradient algorithm [REF-040];
- learned models of medicinal-chemist preferences and interfaces for structured chemistry feedback [REF-010, REF-011, REF-012];
- value of information net of human labeling cost [REF-018, REF-019] and team expected utility that includes the human's cost of verifying [REF-031];
- learning to defer, selective classification, and triage, including deferral under expert capacity and intervention-budget constraints [REF-025 to REF-029, REF-041, REF-044];
- retrospective evidence and a published suggestion for triaging expert review by chemical class and model confidence in regulatory (Q)SAR mutagenicity assessment (no implemented, evaluated triage policy in that source), and structured expert-review arguments assessed against outcomes [REF-008, REF-009];
- tool-using and autonomous LLM chemistry agents [REF-003, REF-004], including drug-discovery agent architectures with HITL checkpoints at high-uncertainty points (preprint) [REF-039];
- conformal prediction and selective prediction in chemical ML [REF-005, REF-006].

Therefore the project must **not** claim novelty from any of the following by themselves:

- HITL, active learning, or uncertainty-based querying;
- goal-directed acquisition;
- value of information net of review cost;
- deferral under capacity;
- chemistry-aware expert triage in general;
- structured chemist feedback;
- LLM agents, GNNs, multi-objective optimization, or chemistry tools.

## Candidate gap (revised)

> In the Round 1 literature set, no study was found that, for **small-molecule lead optimization**, combines
> (a) an explicit per-candidate **escalation** decision under a fixed medicinal-chemist review capacity,
> (b) **prioritization** of escalated candidates using lead-optimization-specific chemistry signals and the consequence for the lead decision, and
> (c) **evaluation of expert benefit against independently obtained outcome evidence**.

Here "independently obtained" means evaluation evidence that was not constructed from the signals the policy uses, with no leakage between policy inputs and evaluation outcomes. It does not mean statistical independence from molecular features, which chemical outcomes will not have. The evaluation protocol itself remains **OPEN** (Issues #9–#10).

Each element has precedent elsewhere:

- (a) in general ML deferral and triage, including under capacity and budget constraints [REF-027 to REF-029, REF-041];
- (b) in a suggested triage-by-chemical-class-and-confidence approach in regulatory toxicology [REF-008] and in decision-theoretic VOI [REF-018, REF-031, REF-040];
- (c) in outcome-checked expert arguments in regulatory toxicology [REF-009].

**Assessment:** a contribution would therefore be an **integration and transfer** of established principles to lead optimization, together with a rigorous evaluation design. It would not be a new decision-theoretic principle. Whether this is publishable depends on demonstrating measurable benefit over strong baselines, with a non-circular evaluation.

## Why the comparator is not "uncertainty alone"

A molecule can be highly uncertain yet unimportant to the current lead decision. Conversely, a moderately uncertain candidate may matter because it combines promising potency with a novel scaffold, conflicting ADMET evidence, an SAR anomaly, or a consequential structural liability.

However, the strongest existing methods are already goal-directed:

- **EPIG** targets the top-scoring region [REF-002, REF-017];
- **UCB-type recommendation** is combined with expert selection [REF-007];
- **Thompson sampling** balances exploration and exploitation [REF-001].

Uncertainty sampling itself performed well in a simulated drug-discovery DMTA study [REF-021]. Comparisons must therefore include these goal-directed and uncertainty baselines, not only random or naive uncertainty ranking.

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

Chemical class and model confidence have been suggested as expert-triage signals in regulatory toxicology, supported by retrospective analysis [REF-008]. The lead-optimization-specific signals in this list were not found used for review allocation in Round 1. No final weighting or formula is accepted.

## Principal risks identified by the literature

1. **Expert judgement varies.** Medicinal chemists show limited consistency and consensus, and systematic biases [REF-010, REF-014, REF-015, REF-042]. This documents variability, not error against independent outcomes. Expert agreement cannot serve as ground truth for expert benefit.
2. **External validity and conditional circularity of evaluation.** Prior HITL molecular-design studies evaluated against in-silico oracles [REF-001, REF-002], which is a legitimate design for studying acquisition strategies but limits external validity. Circularity would arise if evaluation labels were constructed to favour the policy's own signals, if information leaked between policy inputs and evaluation outcomes, or if policies were tuned against evaluation outcomes. This project must be designed to avoid these.
3. **Decision change is not decision improvement.** Overturn rates [REF-008] measure change. Correctness requires outcome evidence, as in [REF-009].

## Claim boundary

- No first-of-kind or definitive novelty claim may be made.
- Round 1 (with Round 1b corrections) did not reach saturation: see the Round 2 queue in [`literature-search.md`](literature-search.md) §9.
- Any publication claim requires the Round 2 searches and owner approval.
