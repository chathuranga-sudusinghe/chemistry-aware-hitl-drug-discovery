# Research Decision Register

This directory records research and governance decisions that materially constrain later implementation or publication.

## Status vocabulary

- **ACCEPTED** — explicitly approved by the owner.
- **PROPOSED** — candidate direction requiring owner decision and/or evidence.
- **OPEN** — unresolved question.
- **SUPERSEDED** — replaced by a later recorded decision; historical rationale is retained.

## Current decisions

### DR-001 — Research first, product later

- **Status:** ACCEPTED
- **Decision:** Conduct the work as a rigorous research project first. Translate validated outcomes into a real-world application only after research validation.
- **Consequence:** Application architecture, MCP deployment, authentication, SaaS design, and similar product concerns must not drive the scientific protocol.

### DR-002 — Chemistry is the scientific core

- **Status:** ACCEPTED
- **Decision:** The project must engage deeply with medicinal/organic chemistry. Agentic AI and HITL are enabling mechanisms rather than the sole source of novelty.
- **Consequence:** Chemistry-specific evidence such as SAR, ADMET, synthesis/developability, structural liabilities, and target context must be considered where justified by the final task.

### DR-003 — Default AI-assistant roles

- **Status:** ACCEPTED
- **Decision:** Claude is the primary coding/implementation agent; Codex independently reviews local + GitHub state; ChatGPT independently reviews GitHub-visible committed state; the human owner makes final decisions.
- **Consequence:** Reviewers do not approve their own implementation. Temporary role changes require explicit bounded owner instruction.

### DR-004 — Local-first, AWS-burst compute

- **Status:** ACCEPTED
- **Decision:** Use the local workstation for normal development and feasible experiments; use AWS only when approved workloads exceed practical local resources or benefit materially from parallel/cloud execution.

### DR-005 — LLM role separated from scientific prediction

- **Status:** ACCEPTED at high level
- **Decision:** Use the LLM primarily for agent orchestration, RAG/evidence synthesis, tool selection, and explanation. Do not treat LLM self-confidence as scientific uncertainty or assume it is the primary chemistry predictor.
- **Open:** Exact LLM/provider, RAG architecture, and whether any later fine-tuning is justified.

### DR-006 — Molecular ML direction

- **Status:** PROPOSED
- **Proposal:** Use strong classical fingerprint-based baselines plus an MPNN/D-MPNN-family 2D graph model; add a 3D equivariant model only if the final target/task requires reliable structural geometry.
- **Open:** Exact architecture, featurization, endpoints, and tuning protocol.

### DR-007 — Review-policy decomposition

- **Status:** PROPOSED
- **Proposal:** Separate expert escalation from expert-review prioritization and evaluate both under fixed medicinal-chemist review budgets.
- **Open:** Utility definition, labels/ground truth, optimization objective, and final budget schedule.

## Decision-record format for future entries

Each future decision should record:

- identifier and title;
- status;
- context;
- decision/proposal;
- evidence and references;
- alternatives considered;
- consequences;
- date and owner approval context;
- supersession link if later replaced.
