# Chemistry-Aware HITL Drug Discovery

Research on chemistry-aware Human-in-the-Loop (HITL) Agentic AI for reliable, review-budget-constrained small-molecule drug discovery and lead optimization.

## Research status

**Stage:** research foundation and protocol development.

This repository is research-first. The current objective is to define and validate a rigorous scientific methodology before implementing a real-world application. Productization, MCP integration, deployment, and application engineering are future translation steps after the research contribution has been validated.

## Working research direction

> **Chemistry-Aware Human-in-the-Loop Agentic AI for Review-Budget-Constrained Multi-Objective Lead Optimization**

The central problem is not simply whether an AI model can rank molecular candidates. The research asks whether limited medicinal-chemist review capacity can be allocated to candidates where expert intervention is expected to have the greatest scientific value.

The proposed research direction combines:

- medicinal and organic chemistry;
- Structure-Activity Relationship (SAR) reasoning;
- small-molecule property and activity prediction;
- Absorption, Distribution, Metabolism, Excretion, and Toxicity (ADMET) considerations;
- synthetic feasibility and structural liabilities;
- protein-ligand evidence where justified by the selected target;
- uncertainty quantification and applicability-domain analysis;
- selective autonomy, expert escalation, and human-review prioritization;
- Large Language Model (LLM) agents for orchestration and evidence synthesis, not as the primary chemistry predictor.

## Current research hypothesis space

The leading hypothesis is that **chemistry-aware expected utility of expert review** can outperform uncertainty-only, information-gain-only, score-only, and random review allocation when medicinal-chemist capacity is constrained.

This is a **PROPOSED research hypothesis**, not an established result. The exact therapeutic target, datasets, final hypotheses, final model architectures, and final review-utility formulation remain open until the literature review and protocol are sufficiently mature.

## Repository map

- [`AGENTS.md`](AGENTS.md) — project governance, research integrity, approval boundaries, and AI-assistant roles.
- [`docs/research-overview.md`](docs/research-overview.md) — high-level scientific scope.
- [`docs/research-gap.md`](docs/research-gap.md) — current evidence-backed gap analysis.
- [`docs/research-questions.md`](docs/research-questions.md) — candidate research questions.
- [`docs/novelty.md`](docs/novelty.md) — novelty hypotheses and claim boundaries.
- [`docs/methodology.md`](docs/methodology.md) — proposed methodological framework.
- [`docs/chemistry-scope.md`](docs/chemistry-scope.md) — chemistry depth and open domain decisions.
- [`docs/literature-review.md`](docs/literature-review.md) — scientific synthesis of closest prior work.
- [`docs/literature-search.md`](docs/literature-search.md) — literature search protocol and log.
- [`docs/references.md`](docs/references.md) — verified reference registry.
- [`docs/compute-strategy.md`](docs/compute-strategy.md) — local-first / AWS-burst compute policy.
- [`docs/decisions/README.md`](docs/decisions/README.md) — accepted and proposed research decisions.

## Implementation status

No dataset, molecular preprocessing pipeline, predictive model, agent, RAG pipeline, review-utility model, or production application is implemented at this stage.

Implementation must follow the approved research protocol and the governance rules in [`AGENTS.md`](AGENTS.md).

## License

Licensed under the [Apache License 2.0](LICENSE).
