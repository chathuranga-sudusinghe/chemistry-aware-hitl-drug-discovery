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

### DR-008 — Dataset-first campaign selection with a separate replication

- **Status:** PROPOSED
- **Context:** Issue #3 requires candidate targets to be compared on public-data availability, assay quality, licensing, and feasibility, and the target is still open. A target with abundant public records can still lack a coherent assay, a reconstructable decision-time order, or a defensible evaluation. Issue #6 (the formal data plan) depends on Issues #3 to #5.
- **Proposal:**
  1. Compare experimental campaigns from public documentation first ([`../candidate-campaigns.md`](../candidate-campaigns.md)), under Issue #3. No record-level check is proposed before the steps in item 5.
  2. Use one coherent campaign as the primary study and an independently sourced dataset as a separately trained replication. Do not pool datasets into one training table, and do not claim generalisation from a single campaign.
  3. Treat chronology reconstructed from order, shipment, or release dates as an assumed-availability analysis unless dated provenance is verified.
  4. Do not rescue a failed candidate through outcome-driven additions. Any correction, new revision, or reassessment requires a documented rationale and owner approval.
  5. Proposed sequence within the current issue order: (a) documentation comparison (Issue #3); (b) the owner decides whether to provisionally accept a shortlist of candidate campaigns as the target candidates (Issue #3); (c) the formal data plan and its approvals (Issue #6); (d) record-level feasibility checks (counts, dates, identity, endpoint overlap) only under explicit owner approval and gates fixed beforehand; (e) final campaign confirmation. Performing record-level checks before target acceptance would require an owner-approved change to Issues #3 and #6.
- **Evidence and references:** [`../candidate-campaigns.md`](../candidate-campaigns.md) (dataset documentation, access dates 2026-10-25 to 2026-10-30). This entry registers no new literature, and publication-derived claims are excluded until they are registered.
- **Alternatives considered:** target-first selection; pooling several databases into one training table; a single dataset only; a ChEMBL-wide primary dataset.
- **Consequences:** The target and datasets remain OPEN. Any inspection of data requires approval under AGENTS.md §4, and gate thresholds belong to Issue #6. Claims from a single campaign are limited to that campaign. Issue #3 stays open after this change: the owner has not accepted a target.
- **Date and approval context:** Proposed 2026-10-29 and revised 2026-10-30 after an independent review. Documented as PROPOSED with the owner's approval of this scope, on branch `docs/issue-3-candidate-campaign-comparison`. Not accepted.

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
