# Literature Review

## Status

Initial verified review. This document is not yet a systematic review and must be expanded before final novelty claims are made.

## 1. Human expertise in molecular design

Human-in-the-loop molecular design is established prior work. Sundin et al. developed a framework in which user feedback helps adapt a multi-parameter optimization scoring function during de novo molecular design, including a medicinal-chemist interaction demonstration [REF-001]. This means the present project cannot claim novelty merely from incorporating medicinal-chemist feedback.

Nahal et al. later combined human-in-the-loop active learning with goal-oriented molecule generation. Their method uses Expected Predictive Information Gain (EPIG) to select molecules for oracle evaluation in order to reduce predictive uncertainty and improve the property predictor guiding generation [REF-002]. This is the closest verified work to the current review-allocation problem and establishes that uncertainty/information-driven expert querying is already an active research direction.

## 2. LLM agents in chemistry

ChemCrow demonstrated that an LLM can be augmented with a set of expert-designed chemistry tools for tasks spanning synthesis, drug discovery, and materials design [REF-003]. Coscientist demonstrated autonomous planning and execution of chemical research tasks using LLMs, tools, documentation search, code execution, and laboratory automation [REF-004].

These studies establish that agentic/tool-using chemistry systems are not novel by themselves. The present project's proposed contribution must therefore lie in a more specific chemistry/decision problem rather than in merely connecting an LLM to chemistry tools.

## 3. Uncertainty, applicability domain, and abstention

Conformal prediction has been described for drug discovery as a framework for sample-specific prediction confidence and applicability-domain-aware QSAR modelling [REF-005]. This supports rigorous uncertainty treatment but does not by itself define how scarce medicinal-chemist attention should be allocated.

Selective prediction has also been applied in chemical toxicity modelling. The AI4PFAS work used an abstention mechanism so the model could decline predictions in low-confidence regions, linking uncertainty to a predict-versus-abstain decision [REF-006]. This is important prior art for selective autonomy and means the present project cannot claim that "knowing when not to predict" is new.

## 4. Emerging research gap

The currently verified literature supports a more specific hypothesis:

- human feedback in molecular design exists [REF-001];
- active-learning selection for human evaluation exists [REF-002];
- chemistry agents exist [REF-003, REF-004];
- calibrated confidence/applicability-domain methods exist [REF-005];
- uncertainty-driven abstention exists in chemical ML [REF-006].

The unresolved question for this project is whether **limited medicinal-chemist cognitive review capacity** can be allocated according to the **expected scientific utility of expert intervention**, using chemically consequential evidence beyond generic uncertainty, and whether separating escalation from prioritization improves multi-objective lead decisions.

## 5. Current positioning

The proposed contribution is therefore not "HITL drug discovery" or "agentic AI for chemistry" in general. It is a candidate **chemistry-aware decision-allocation framework** where expert attention is treated as a scarce scientific resource.

Potential chemistry-specific evidence includes SAR inconsistency, structural liabilities, synthetic feasibility, ADMET conflict, scaffold novelty, applicability-domain concerns, and target-specific evidence. The literature search must still be expanded around value of information, expert triage, human-attention allocation, medicinal-chemistry decision support, and active learning before this gap can be treated as publication-ready.
