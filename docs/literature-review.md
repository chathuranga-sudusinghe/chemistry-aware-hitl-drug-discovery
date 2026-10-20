# Literature Review

## Status

**Round 1 structured narrative review with Round 1b corrections (Issue #2, 2026-10-20).** Saturation has not been reached.

- The search protocol, queries, and screening log are in [`literature-search.md`](literature-search.md). This is not a systematic review, and saturation is not claimed.
- Every claim below cites a `REF-xxx` entry in [`references.md`](references.md).
- Where a reference was read at abstract level only, the claim does not go beyond the abstract.
- Statements marked **Assessment** are project inferences, not findings of the cited sources.

## 1. HITL molecular design and chemist preference elicitation (Topic A)

**HITL molecular design is established.**

- **Sundin et al. [REF-001]:**
  - adapt a multi-parameter optimization scoring function from chemist feedback (desirability bounds from binary feedback; a Gaussian-process component from continuous feedback);
  - compare query strategies and find that Thompson sampling, which balances exploration and exploitation, performed best in one task;
  - note that query selection must find high-scoring molecules because the learned model acts as a reward function.

  This query selection is already **optimization-aware**, not uncertainty-only.
- **Nahal et al. [REF-002]:** refine the property predictor that guides generation with HITL active learning. EPIG [REF-017] is aimed at the top 1000 molecules by predicted score, so acquisition targets information about the *promising* region rather than global uncertainty.

**Chemist preferences can be learned, at the cost of known noise.**

- Choung et al. [REF-010] learned a ranking from more than 5000 pairwise annotations by 35 chemists, selected by active learning. Inter-rater agreement was moderate (Fleiss' κ 0.40 and 0.32) and intra-rater consistency fair (Cohen's κ 0.60 and 0.59).
- Interpretable decompositions of binary chemist preferences have been proposed explicitly to expose bias, noise, and inconsistency [REF-011].
- Tooling exists to collect feedback on desired or undesired substructures and properties beyond like/dislike [REF-012].
- Expert feedback has been used to personalise synthetic-feasibility scoring [REF-013].

**Closest identified framework: He et al. [REF-007].**

- **Setting:** a human–algorithm collaboration framework for sequential drug-discovery experiments under a fixed experimental budget.
- **Mechanism (arXiv v1):**
  - each round, the algorithm proposes a batch selected by model uncertainty and a batch selected by a UCB-type search score;
  - a domain expert chooses which candidates are tested and may override the algorithm.
- **Published abstract:** describes attention management and ends its practice-and-policy sentence with "use AI to route scarce expert attention to the most informative experiments".
- **Version boundary:** only arXiv v1 was read in full. The published journal version may differ in design and evaluation, and the statements below apply to v1 only.
- **Limitations relative to this project (v1):**
  - therapeutic peptides, not small-molecule lead optimization;
  - a single expert;
  - retrospective database labels;
  - every round's recommendation set is reviewed, with no per-candidate escalation decision;
  - no chemistry-specific review signals.

**Expert involvement in Bayesian optimization is an active topic.** Prior work treats expert advice as costly and unreliable, guaranteeing that the required expert labels decline over time and that untrustworthy advice does no harm [REF-022]. Intermittent, randomly timed expert feedback can still help a chemistry BO campaign (workshop evidence) [REF-023].

**Assessment:** human feedback, goal-directed query selection, and budgeted expert involvement in molecular design are all established. None of the HITL drug-discovery studies read in full (REF-001, REF-002, REF-007 v1) makes a separate per-candidate decision about *whether* expert review is warranted, and none models per-candidate review cost.

## 2. Value of information and decision-theoretic query selection (Topics B, C)

The general form of the project's conceptual review-utility expression is established:

- **Kapoor, Horvitz and Basu [REF-018]** define the value of information of labeling a point as the expected reduction in total misclassification risk, with class-dependent misclassification costs, **minus the cost of obtaining the label**. They use it to triage human labeling effort.
- **Nguyen, Wallace and Lease [REF-019]** apply decision-theoretic active learning to allocate items across machine, crowd, and expert tiers under a budget.
- **Negoescu, Frazier and Powell [REF-040]** choose which molecules to test so as to maximise the expected quality of the best compound discovered, using the knowledge-gradient algorithm with a Bayesian prior that exploits correlations between molecules. This is a decision-oriented formulation for drug-discovery experiment selection (abstract-level reading). It selects experiments, not medicinal-chemist review.
- **Bansal et al. [REF-031]** express team expected utility through final-decision quality, the human's cost of verifying, both parties' accuracies, and the cost of mistakes. The most accurate model is not necessarily the best teammate.

In drug-discovery active learning, the choice of query strategy materially affects outcomes. In a simulated DMTA cycle with docking scores as an assay proxy, uncertainty-based sampling outperformed greedy and hybrid strategies [REF-021]. This is evidence that "uncertainty-only" is a strong baseline and not a strawman. A 2015 review of drug-discovery active learning exists [REF-020] but was not read.

**Assessment:** "expected benefit minus review cost" is not a new principle [REF-018, REF-031], and decision-oriented selection for drug discovery exists for experiments [REF-040]. A contribution must lie in how *benefit* and *decision consequence* are operationalised for multi-objective small-molecule lead optimization, and in showing that this operationalisation improves decisions over strong goal-directed baselines [REF-002, REF-007, REF-017].

## 3. Deferral, triage, and capacity-constrained escalation (Topic D)

**Whether a case should go to a human is a mature problem in general machine learning.**

- **Learning to defer** (a framing traced to [REF-024], read at metadata level only) jointly trains a predictor and a rejector from samples of expert decisions [REF-025].
- **Selective classification** rejects inputs to guarantee a target risk [REF-026]. A survey exists [REF-033] but was not read.
- **Triage:**
  - effective automation requires instance-level estimates of both algorithmic and human error [REF-027];
  - for a fixed triage level, the optimal policy thresholds the per-instance difference between model and human error [REF-028].
- **Capacity constraints:**
  - deferral has been formulated with asymmetric error costs and individual expert work-capacity limits, solved globally with constraint programming, and tested with synthetic fraud analysts [REF-029] (peer-reviewed, TMLR 2024);
  - the Bayes-optimal learn-to-defer solution has been derived under constraints that include an expert-intervention budget [REF-041];
  - online deferral under a budget with partial feedback has been studied as a contextual bandit [REF-044] (preprint);
  - benchmarks for deferral use synthetic experts with adjustable decision processes and work-capacity constraints, and algorithm rankings were found to vary significantly with the available experts [REF-043];
  - reducing the number of expert predictions needed to learn deferral has been studied with real radiologists [REF-030].
- **Complementarity:** whether hybrid human–machine combinations outperform either alone depends on how the confidence of each is expressed [REF-032].

**Retrospective evidence motivating chemistry-aware triage of expert review exists in regulatory toxicology.**

- Under ICH M7, expert review overturned 26% of default (Q)SAR mutagenicity predictions for 1002 drug impurities. It resolved 91% of equivocal and 75% of out-of-domain calls [REF-008].
- Overturns concentrated in particular chemical classes (e.g., primary aromatic amines, aldehydes, Michael acceptors) and in low-confidence predictions. The authors **suggest** triaging by chemical class and probability to improve review efficiency; the study is retrospective and does not implement or evaluate a triage policy [REF-008].
- A later study assigned standardised expert arguments to recurring prediction scenarios and assessed how often each argument reached the correct resolution [REF-009].

**Assessment:**
- Escalation under limited capacity is established in general ML [REF-027 to REF-029, REF-041].
- A chemistry-aware triage idea (chemical class plus model confidence) has retrospective support and a published suggestion in regulatory mutagenicity assessment [REF-008]. Demonstrated effectiveness of an implemented triage policy was not found in that source.
- What Round 1 did **not** find is a lead-optimization study that combines a per-candidate escalation decision, a fixed medicinal-chemist capacity, lead-optimization-specific chemistry signals, and outcome-based evaluation. Given the search limits in [`literature-search.md`](literature-search.md) §8–9, this is an absence in the searched set, not evidence of absence.

## 4. Reliability of chemist judgement: contrary and limiting evidence (Topic F)

Expert review is not a noise-free oracle:

- **Lajiness et al. [REF-014]:** 13 medicinal chemists were "not very consistent" in which compounds they rejected, including a hidden subset previously rejected by a senior chemist.
- **Kutchukian et al. [REF-015]:** chemists typically used only one or two parameters when selecting fragments, showed low consensus, agreed mainly on what was undesirable, and were often unaware of what drove their choices.
- **Choung et al. [REF-010]:** only moderate inter-rater agreement, even with a pairwise design intended to reduce anchoring bias.
- **Stroganov et al. [REF-042]:** in D3R Grand Challenge 4, human decisions showed systematic biases. Human experts could compete with blind algorithms in some areas, but performed significantly worse in data-rich tasks such as binding-affinity prediction (abstract-level reading).
- **Voinarovska et al. [REF-038]:** expert chemists' assessments of synthesis routes converged when they were given clear evaluation categories. This supports structured feedback categories as a means of improving consistency.
- **Segall [REF-016]:** lead decisions are multi-parameter trade-offs, often made with desirability functions, Pareto methods, or probabilistic methods that account for predictive and experimental uncertainty.

**Assessment and implications:**
- These studies document **variability, inconsistency, low consensus, and bias** in chemist judgement [REF-010, REF-014, REF-015, REF-042]. Except where outcomes were available (REF-009, REF-042), they do not establish that a reviewer's decisions were *incorrect* against independent outcomes. Reviewer error remains a risk requiring outcome-based assessment.
- A review policy cannot treat expert agreement or disagreement as ground truth.
- If expert benefit is measured by agreement with one reviewer, results may reflect that reviewer's preferences rather than better chemistry. This is relevant to the independent-evaluation question raised in the Issue #2 review (M2).
- Reviewer variability needs to be modelled or measured. Learning-to-defer methods that model human error per instance [REF-025, REF-027, REF-028, REF-030] offer a formal route.

## 5. Uncertainty and applicability domain (Topic E; light coverage)

- **Conformal prediction** provides object-specific prediction intervals or sets with error-rate guarantees and an applicability-domain interpretation for QSAR [REF-005].
- **Selective prediction:** abstention in high-uncertainty regions has been applied to PFAS toxicity [REF-006].
- **Method comparisons:**
  - deep ensembles and bootstrapping outperformed MC-dropout for graph-based molecular property prediction, and out-of-domain uncertainty remains difficult [REF-034];
  - under data shifts on ADME endpoints, no single UQ method consistently won, and combining distance-based and model-based metrics through error models improved uncertainty estimates [REF-035].

**Assessment:** uncertainty-method selection should be treated as an empirical question under the project's chosen split and shift (Issue #8). Conformal guarantees should be stated with their exchangeability assumption; that is a project assessment and is not stated in the REF-005 abstract.

## 6. LLM agents in chemistry and drug discovery (Topic G)

- **Established systems:**
  - tool-using chemistry agents [REF-003];
  - autonomous experimental-research systems [REF-004];
  - a broad review of chemistry LLMs and agents identifies data quality, interpretability, and benchmarks as key challenges [REF-036].
- **LLMs versus chemists:**
  - on a 2700-question benchmark, the best LLMs on average outperformed the best participating chemists but gave overconfident predictions [REF-037];
  - LLMs differ systematically from expert majority judgement on synthesis-route quality [REF-038].
- **Agent architectures with HITL checkpoints:** a recent preprint describes drug-discovery agents with governed tool use and HITL checkpoints "at high-uncertainty decision boundaries" [REF-039]. The abstract does not describe how checkpoints are triggered, budgeted, or evaluated.

**Assessment:** REF-037 supports DR-005: LLM self-reported confidence should not serve as scientific uncertainty. HITL checkpoints in agent pipelines are emerging, so any "agentic" framing of escalation must be compared with that line of work rather than presented as new.

## 7. How prior work evaluates expert benefit (Topic H)

| Study | Feedback source | Ground truth for success | Evaluation risk relevant to this project |
|---|---|---|---|
| REF-001 | Simulated chemist; one real chemist (co-author) | In-silico oracles (modified QED; DRD2 activity model), also for the real-human run | The success metric is a model, not experiment; simulator and evaluator are related |
| REF-002 | Noisy simulated experts; three real chemists (co-authors) | In-silico DRD2 classifier | Same as above. Real feedback was small-scale and affected by prompt misreading |
| REF-007 (arXiv v1 only; published version not assessed) | One real domain expert (v1) | Retrospective database labels (peptides) | Retrospective labels are available for all candidates; there is no per-candidate review cost |
| REF-008 | Real regulatory expert reviews | Overturn rates of default predictions | Measures decision change, not demonstrated correctness |
| REF-009 | Standardised expert arguments | Correct resolution on pharma-donated data | Outcome-checked, but in the regulatory mutagenicity domain |
| REF-010 | 35 real chemists, pairwise | Agreement and consistency statistics; correlation with descriptors | Preferences are not validated against experimental outcomes |
| REF-038 | 17 real chemists | Expert majority vote | Majority opinion, not experimental route success |
| REF-043 | 50 synthetic fraud analysts with work-capacity constraints | Fraud labels | Synthetic experts, validated against real experts only through consistency and inter-expert agreement metrics; fraud domain |

**Assessment:**
- No study in the Round 1 set evaluates, for small-molecule lead optimization, whether allocated expert review improved decisions as measured by **independently obtained outcome evidence** (evidence not constructed from the policy's own signals).
- The closest outcome-checked design is in regulatory toxicology [REF-009].
- **External validity.** The prior HITL molecular-design studies evaluate against in-silico oracles [REF-001, REF-002]. Defining oracle values as simulated ground truth is a legitimate design for studying acquisition strategies. Its limitation is external validity: success is measured against a model, not against experiment, and real-expert feedback was small-scale.
- **Conditional circularity.** Circularity would arise only if evaluation labels were constructed to favour the signals the policy uses, if information leaked between policy inputs and evaluation outcomes, or if policies were tuned against the evaluation outcomes. None of these is claimed for REF-001 or REF-002. They are risks to be designed against in this project (Issues #9–#10).
- This is input to Issues #9–#10, not a decision.

## 8. Closest-method comparison

Columns follow the Issue #2 proposal. "—" means not described in the material read. Cells for abstract-level references are limited to the abstract.

| Ref | Domain | Feedback type | Decision objective | Query / allocation rule | Review cost modelled | Chemistry evidence used | Escalation (whether to involve the expert) | Ground truth | Evaluation population |
|---|---|---|---|---|---|---|---|---|---|
| REF-001 | De novo small molecules | Binary or continuous chemist scores | Learn MPO scoring / reward | Thompson sampling, uncertainty, exploitation, random | No | MPO properties (e.g., QED components), DRD2 model | No (fixed query batches) | In-silico oracles | Generated molecules |
| REF-002 | De novo small molecules | Slider ratings of predicted activity | Improve predictor in the promising region | EPIG targeted at top-k predicted; uncertainty; greedy; random | No (fixed batch) | DRD2 activity; penalised LogP | No | In-silico DRD2 classifier | Generated molecules |
| REF-007 (arXiv v1 only) | Therapeutic peptides (v1) | Approve/override experiment choice | Maximise hit rate under an experimental budget | Top-q uncertainty batch + top-h UCB batch, expert selects | Experimental budget only | Multi-property labels; no chemistry review signals | No (all recommendations reviewed each round) | Retrospective database labels | Fixed peptide pool |
| REF-008 | Regulatory mutagenicity (impurities) | Expert overturn of (Q)SAR calls | Correct regulatory call | Retrospective; proposes triage by chemical class + probability | — | Chemical class, structural analogues and mechanism (expert side), model confidence, out-of-domain status | Proposed, not implemented | Overturn rates | 1002 impurities |
| REF-010 | Small-molecule preference | Pairwise choice | Learn chemist intuition proxy | Active-learning pair selection | No | Descriptor-based features | No | Annotator agreement | Curated compound pairs |
| REF-018 | Generic classification | Labels | Minimise misclassification risk + labeling cost | Myopic VOI | **Yes** (label cost) | None | Implicit (label only if VOI > 0) | Labels | Voice messages |
| REF-028 | Generic supervised | Human predictions | Minimise team error at a fixed triage level | Threshold on model-vs-human error difference | Via triage level | None | **Yes** | Labels | Synthetic and real tasks |
| REF-029 | Fraud detection | Expert decisions | Minimise asymmetric error cost | Constraint programming under capacity | **Yes** (capacity) | None | **Yes** | Labels | Synthetic analysts |
| REF-040 | Drug-discovery experiment selection (single-property) | None (Bayesian prior over molecule performance) | Maximise expected quality of the best compound found | Knowledge gradient with correlated prior | Number of tests | Correlation structure between related molecules | Not applicable (selects experiments, not reviews) | — (abstract only) | 87,120 alternatives |
| REF-041 | Tabular benchmarks (COMPAS, ACSIncome) | Expert decisions | Bayes-optimal deferral under constraints | Post-processing with constraints incl. expert-intervention budget | **Yes** (intervention budget) | None | **Yes** | Labels | Benchmark datasets |
| REF-031 | Generic advice-taking | Accept/solve decision | Maximise team expected utility | Train AI for team utility | **Yes** (verification cost) | None | Human decides | Labels | High-stakes datasets |
| REF-022 | BO (battery design) | Accept/reject advice | Optimise with costly, unreliable experts | Handover with adaptive trust | Expert-label count | — | Declining expert involvement | Objective values | BO campaign |
| REF-039 | Drug-discovery agents (preprint) | HITL checkpoints | Governed agent workflow | — | — | Toxicity filters, pipeline stages | Checkpoints at "high-uncertainty decision boundaries" | — | Benchmark + case studies |
| **This project (PROPOSED)** | Small-molecule lead optimization | Structured chemistry feedback | Improve multi-objective lead decisions | Escalation, then prioritization | To be defined (#9–#10) | SAR, ADMET conflict, liabilities, synthesis, scaffold novelty, AD | Yes (separate stage) | To be defined (#9–#10); should be independently obtained | To be defined (#10) |

## 9. Synthesis for positioning

1. **Not new:**
   - HITL molecular design [REF-001, REF-002];
   - goal-directed expert querying [REF-001, REF-002, REF-017];
   - budgeted human–algorithm collaboration in drug discovery (arXiv v1 of REF-007);
   - value of information net of labeling cost [REF-018], and decision-oriented selection of drug-discovery experiments [REF-040];
   - capacity- and budget-constrained deferral [REF-029, REF-041, REF-044];
   - the idea of chemistry-aware triage of expert review, with retrospective support and a published suggestion in regulatory toxicology [REF-008] (an implemented, evaluated policy was not found in that source);
   - structured, chemistry-specific expert feedback [REF-009, REF-012];
   - tool-using chemistry agents [REF-003, REF-004].
2. **Not found in Round 1** (an absence in the searched set, with the limits in [`literature-search.md`](literature-search.md) §8–9): a small-molecule lead-optimization study that combines
   - an explicit per-candidate escalation decision under fixed medicinal-chemist capacity,
   - prioritization using lead-optimization-specific chemistry signals and decision consequence,
   - structured feedback categories, and
   - evaluation against independently obtained outcome evidence, not constructed from the policy's own signals.
3. **Candidate baselines (recommendation for Issue #10, not a protocol requirement or a literature finding).** Strong methods that a study in this area could be compared against include goal-directed EPIG [REF-002, REF-017], uncertainty sampling [REF-021], UCB-style recommendation with expert selection (arXiv v1 of REF-007), value of information net of cost [REF-018], and a deferral/triage rule based on estimated model-vs-human error [REF-028]. Which baselines, evaluation populations, and budgets are used is an Issue #10 decision.
4. **Evaluation is the hardest open problem.** Prior HITL molecular-design studies evaluated against in-silico oracles [REF-001, REF-002], which limits external validity, and chemists' judgements show documented variability and low consensus [REF-010, REF-014, REF-015]. Circularity is a conditional design risk, not something found in those studies. The positioning depends as much on an independent evaluation design (Issues #9–#10) as on the policy itself.
