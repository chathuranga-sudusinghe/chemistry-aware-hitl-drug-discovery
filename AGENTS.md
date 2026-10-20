# Project instructions: chemistry-aware-hitl-drug-discovery

## 1. Project purpose and current scope

This is a publication-oriented research project investigating chemistry-aware Human-in-the-Loop (HITL) Agentic AI for reliable, review-budget-constrained small-molecule drug discovery and lead optimization.

The scientific core is medicinal/organic chemistry and chemistry-grounded decision support. Agentic AI, Large Language Models (LLMs), Retrieval-Augmented Generation (RAG), and HITL mechanisms are enabling layers, not substitutes for validated chemistry models or evidence.

The project is **research-first**. A real-world application may be developed only after the research contribution is sufficiently validated. Product engineering, MCP integration, deployment, authentication, dashboards, SaaS architecture, and other production infrastructure are not part of the current research scope unless explicitly approved as a later milestone.

Current open decisions include the therapeutic target/protein system, datasets, exact lead-optimization task, final research questions and hypotheses, final molecular representations, final model architectures, the review-utility formulation, and the final evaluation protocol.

Use `README.md` for the project overview and `docs/` for scientific documentation. `docs/references.md` is the authoritative source registry for literature used in project claims.

## 2. Human ownership and assistant roles

- **Human owner:** owns and directs the project and has final authority over research scope, chemistry assumptions, methodology, datasets, molecular preprocessing, model selection, experiments, implementation acceptance, Git/GitHub operations, licensing, cloud use, and publication claims. AI recommendations are proposals until the owner explicitly accepts them.
- **Claude:** primary coding and implementation agent. Claude may inspect and implement only owner-approved scope. Claude cannot approve its own implementation, change research methodology implicitly, or treat implementation convenience as scientific justification.
- **Codex:** independent reviewer of local repository state and GitHub-visible state. Codex should challenge methodology and implementation where evidence warrants it, but must not modify project files unless the owner explicitly changes its assigned role for a specific task.
- **ChatGPT:** independent reviewer of GitHub-visible committed state. ChatGPT cannot verify local-only uncommitted changes, ignored data, or the local runtime environment through a GitHub review. ChatGPT must not modify implementation files unless the owner explicitly assigns a bounded implementation task.

The owner may temporarily assign a different role to an assistant for a specific bounded task. That exception does not permanently change these default roles.

## 3. Independent review workflow

Default workflow:

Claude implementation -> Codex independent review -> ChatGPT independent GitHub review -> owner compares findings -> Claude implements only owner-approved fixes.

Keep reviews independent where practical. Do not provide one reviewer with another reviewer's conclusions before the first reviewer has completed its own assessment unless the owner requests a comparative review.

For reviewer-driven changes, distinguish:

- confirmed defects;
- evidence gaps;
- methodological risks;
- optional improvements;
- stylistic preferences.

Reviewer agreement is not a substitute for evidence, tests, or owner approval.

## 4. Approval and execution boundaries

Explicit owner approval is required before:

- creating/updating GitHub issues after the initial approved foundation work;
- creating, switching, renaming, deleting, merging, rebasing, resetting, or force-updating branches;
- staging, committing, pushing, merging pull requests, or release operations;
- installing dependencies or changing a lockfile;
- downloading, inspecting, preprocessing, or transforming real molecular/biological datasets;
- changing molecular identity or preprocessing policy;
- training, fine-tuning, evaluating, benchmarking, calibrating, or running inference with real project models/data;
- hyperparameter tuning, cross-validation, ablations, repeated-seed experiments, or final test-set evaluation;
- GPU/CUDA execution, AWS/cloud execution, large downloads, or other expensive compute operations;
- changing the research protocol, chemistry scope, uncertainty policy, review-budget policy, or publication claims.

Bounded read-only repository inspection and planning are allowed unless the owner states otherwise.

Before requesting permission for a real-data/model execution, provide the exact command, working directory, dataset revision and split, model/configuration, whether train/validation/test data are involved, device/environment, expected runtime, expected RAM/VRAM, expected artifacts/disk usage, network/download impact, and test-seal implications where applicable.

## 5. Git and GitHub governance

- Never commit or push implementation work directly to `main`.
- Tracked repository mutations should be issue-scoped after the initial foundation is established.
- Use branch names in the form `<type>/issue-<number>-<short-topic>`.
- Do not invent issue numbers.
- Do not mix unrelated changes in the same issue, branch, or commit.
- Preserve unrelated owner work.
- Stage explicit files only; do not use blanket staging when a narrower operation is possible.
- Do not place AI vendor names in branch names, commit messages, or authorship trailers unless the owner requests it.

Research-documentation changes that alter methodology are not "documentation-only" changes; they require the same scientific review as code that would implement the methodology.

## 6. Chemistry and molecular-data integrity

Raw molecular and biological data are immutable source evidence. Never silently alter, normalize, remove, or overwrite source records.

Molecular preprocessing is research methodology and requires explicit approval. This includes, but is not limited to:

- SMILES canonicalization;
- duplicate/equivalence handling;
- salts and mixtures;
- disconnected fragments;
- formal charges;
- protonation/ionization states;
- tautomer handling;
- stereochemistry;
- aromaticity and sanitization;
- scaffold definitions;
- conformer generation;
- descriptors/fingerprints;
- protein structure preparation;
- ligand preparation;
- docking/pose preprocessing.

RDKit or another toolkit accepting a structure does not establish chemical identity, stability, synthesizability, biological relevance, or experimental correctness.

For every dataset, document provenance, publication/official source, version/revision, access date, license/terms, local filename/checksum where practical, target definition, units, exclusions, transformations, and known limitations.

Third-party datasets, models, protein structures, papers, and databases retain their own licenses and terms; the repository's Apache-2.0 license does not relicense them.

## 7. Chemistry scope and medicinal-chemistry reasoning

The research should remain chemically substantive. Where scientifically justified, candidate evaluation may include:

- functional groups and structural liabilities;
- protonation, tautomerism, stereochemistry, and conformational effects;
- physicochemical properties;
- scaffold novelty and analogue context;
- Structure-Activity Relationship (SAR) consistency;
- potency/selectivity evidence;
- ADMET trade-offs;
- synthetic accessibility/feasibility;
- protein-ligand interaction evidence;
- applicability-domain and out-of-distribution concerns.

Do not convert these into a single composite score without an approved scientific rationale and sensitivity analysis.

Human feedback should not be reduced to approve/reject if the research question requires chemical reasoning. Structured reasons may include SAR inconsistency, reactivity/stability concerns, metabolic liability, toxicity concern, synthetic infeasibility, target-interaction concern, or other approved categories.

## 8. Model and uncertainty governance

The project should separate at least four conceptual layers:

1. predictive chemistry models;
2. uncertainty/applicability-domain estimation;
3. expert-escalation/review-prioritization policy;
4. LLM agent/RAG orchestration and explanation.

Do not use LLM self-reported confidence as scientific uncertainty.

Candidate molecular ML families currently include message-passing Graph Neural Networks (GNNs), with classical fingerprint-based baselines and potentially 3D equivariant models if the final task requires structural geometry. These remain **PROPOSED** until the protocol accepts them.

Candidate uncertainty methods include deep ensembles, conformal prediction, model disagreement, and distance/applicability-domain measures. Method choice and calibration data are research decisions, not implementation details.

The LLM may orchestrate tools, retrieve literature, synthesize evidence, and explain decisions. It should not be treated as the primary validated predictor of potency, ADMET, toxicity, binding, or other chemistry endpoints unless a future protocol explicitly tests such a role.

## 9. Research integrity, leakage prevention, and evaluation

Never fabricate metrics, citations, dataset facts, model results, chemical claims, timings, hardware results, performance gains, novelty claims, or statistical conclusions.

Separate:

- observed repository/experiment evidence;
- verified literature evidence;
- inference;
- proposal/recommendation.

Prevent data leakage across molecularly equivalent or near-duplicate records according to an approved identity policy. Random, scaffold, temporal, target-family, and other split strategies are distinct protocols and must not be interchanged casually.

Fit learned preprocessing, calibration, and model-selection procedures only on the data allowed by the protocol. Never use held-out test labels to select preprocessing, features, architectures, thresholds, hyperparameters, calibration rules, review policies, or models.

A final test set, once defined and sealed, must remain unavailable for iterative methodology revision.

Comparisons must use fair and documented tuning budgets, evaluation populations, seeds, and metrics. Negative and null results are valid evidence and must not be hidden.

## 10. Human-review and HITL research integrity

Clearly distinguish:

- simulated oracle feedback;
- rule-derived labels;
- historical retrospective outcomes;
- real medicinal-chemist feedback.

Do not present simulated feedback as human validation.

Review-budget assumptions must be explicit. If review capacity is represented as a percentage, number of candidates, time budget, or cost, document exactly how it is defined and whether all strategies receive the same budget.

The proposed research distinction between **escalation** (does this case need expert review?) and **prioritization** (which review-worthy cases deserve attention first?) should remain explicit unless the owner approves a different formulation.

## 11. Literature, references, and novelty claims

`docs/references.md` is the authoritative reference registry.

Every reference used to support a substantive research claim should have:

- stable `REF-xxx` ID;
- full citation;
- DOI or authoritative URL where available;
- verification status;
- short note on what it supports.

Do not cite papers that have not been verified. Do not claim "first", "novel", "state of the art", or equivalent language without a sufficiently comprehensive literature search.

`docs/literature-review.md` is for synthesis and comparison; it should cite `REF-xxx` IDs rather than duplicate the bibliography.

Potential novelty must be labelled **PROPOSED**, **SUPPORTED**, **CHALLENGED**, or **REJECTED** as evidence evolves.

## 12. Compute and cloud policy

The accepted compute strategy is local-first with cloud burst capacity when justified.

Local development may use the owner's workstation for preprocessing, classical baselines, moderate 2D GNN experiments, uncertainty development, agent/RAG development, and engineering work after the relevant execution is approved.

AWS may be used for experiments that are impractical on the local 8 GB VRAM GPU, such as larger 3D/equivariant models, large ensembles, extensive sweeps, or other approved workloads.

Cloud use must be explicitly approved with expected instance type, runtime, storage/network impact, and cost-sensitive considerations. Do not start or leave cloud resources running without authorization.

Use the same experiment/configuration interface across local and cloud environments where practical to support reproducibility.

## 13. Environment and artifacts

Use `pyproject.toml` as the primary Python project/dependency configuration. Do not create parallel dependency manifests without approval.

Do not commit by default:

- raw/interim/processed datasets;
- model checkpoints;
- large generated predictions;
- experiment outputs;
- environment folders;
- caches;
- credentials/secrets;
- AWS credentials;
- proprietary or unpublished external data.

Tiny synthetic fixtures may be committed when specifically needed for tests.

## 14. Decisions and documentation

Unresolved methodology ideas must be labelled **PROPOSED** or **OPEN**. Only owner-approved decisions may be labelled **ACCEPTED**.

The decision index is `docs/decisions/README.md`. Decisions should record context, status, rationale, alternatives considered, consequences, and supersession history when relevant.

Do not silently change an accepted research decision in code, configuration, documentation, or refactoring.

## 15. Product-translation boundary

The intended long-term direction is to translate validated research into a real-world molecular-discovery application.

That application is **not itself the present research contribution**. The research must remain independently publishable and scientifically evaluable without requiring the final app.

Future product work may include APIs, MCP servers, RAG services, review interfaces, provenance/audit views, model serving, authentication, and cloud deployment, but only after separate owner-approved milestones.
