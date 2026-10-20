# Verified References

This file is the authoritative literature registry for project claims. References are assigned stable IDs and should be cited from other project documents using those IDs. IDs are never reused or renumbered.

- **Initial set (REF-001 to REF-006):** verified 2026-10-20; bibliographic metadata re-verified and corrected 2026-10-20 under Issue #2.
- **Issue #2 Round 1 additions (REF-007 to REF-039):** verified 2026-10-20. Search procedure: [`literature-search.md`](literature-search.md).
- **Issue #2 Round 1b corrections and additions (REF-040 to REF-044):** 2026-10-20, following the independent review (see [`literature-search.md`](literature-search.md) §6). Venue and peer-review status of arXiv-sourced entries re-checked; REF-029 corrected.

## Entry fields

- **Title** is the exact publication title as recorded by Crossref or the source.
- **Access level** records what was actually read:
  - **Full text** — the relevant sections were read directly.
  - **Full text (tool-assisted)** — full text was queried through an automated reader with targeted questions; key details should be spot-checked by a human reviewer before publication use.
  - **Abstract** — only the abstract and bibliographic metadata were read. Claims citing the entry must not go beyond the abstract.
- **Peer review** is recorded where it is not an ordinary journal or archival-proceedings article. Preprints and workshop papers are flagged as such.
- **Venue source** records how a conference venue was established when it was not taken from a DOI record.
- **Limitations** — what the source does *not* support for this project.

Bibliographic metadata were checked against Crossref (DOIs) or the arXiv/proceedings record (non-DOI items).

---

## A. Human-in-the-loop molecular design and chemist preference elicitation

## REF-001 — Human-in-the-loop assisted de novo molecular design

- **Authors:** Iiris Sundin, Alexey Voronov, Haoping Xiao, Kostas Papadopoulos, Esben Jannik Bjerrum, Markus Heinonen, Atanas Patronov, Samuel Kaski, Ola Engkvist
- **Title:** Human-in-the-loop assisted de novo molecular design
- **Year:** 2022
- **Venue:** Journal of Cheminformatics, 14, 86
- **DOI:** 10.1186/s13321-022-00667-8 (PMCID PMC9795720)
- **Access level:** Full text (tool-assisted)
- **Status:** VERIFIED
- **Supports:** Human feedback used to adapt a multi-parameter optimization (MPO) scoring function (desirability bounds from binary feedback; a Gaussian-process scoring component from continuous feedback). Query selection compared random, uncertainty, exploitation, and Thompson sampling; Thompson sampling trades off exploration and exploitation because the learned model is used as a reward function.
- **Limitations:** Simulated-chemist experiments use oracles (modified QED; a DRD2 activity model). The real-human demonstration used one medicinal chemist (a co-author), and success was scored by the in-silico oracle rather than by experimental outcomes. No mechanism decides *whether* the human is consulted, and review cost is not modelled.

## REF-002 — Human-in-the-loop active learning for goal-oriented molecule generation

- **Authors:** Yasmine Nahal, Janosch Menke, Julien Martinelli, Markus Heinonen, Mikhail Kabeshov, Jon Paul Janet, Eva Nittinger, Ola Engkvist, Samuel Kaski
- **Title:** Human-in-the-loop active learning for goal-oriented molecule generation
- **Year:** 2024
- **Venue:** Journal of Cheminformatics, 16, 138
- **DOI:** 10.1186/s13321-024-00924-y (PMCID PMC11629536)
- **Access level:** Full text (tool-assisted)
- **Status:** VERIFIED
- **Supports:** HITL active learning that refines a property predictor guiding generation. EPIG is targeted at the top-k (k = 1000) molecules by predicted score, making acquisition goal-directed rather than uncertainty-only. Uses noisy simulated experts and three real chemists, with a fixed per-iteration query batch.
- **Limitations:** Ground truth for DRD2 is an in-silico classifier, not experimental measurement. The three chemists were co-authors, and two misread the question prompt. There is no escalation/gating mechanism (every cycle queries a fixed batch), and per-molecule review cost is not modelled.

## REF-007 — Collaborative intelligence in sequential experiments (HITL drug discovery)

- **Authors:** Jinghai He, Cheng Hua, Yingfei Wang, Zeyu Zheng
- **Title:** Collaborative Intelligence in Sequential Experiments: A Human-in-the-Loop Framework for Drug Discovery
- **Year:** 2026 (issue); preprint 2024
- **Venue:** Information Systems Research, 37(3), 1390–1415
- **DOI:** 10.1287/isre.2024.1154; preprint arXiv:2405.03942 (v1, 7 May 2024; the only arXiv version)
- **Access level:** Full text of arXiv v1 (pp. 1–24). **Published version: abstract only** (via Crossref/OpenAlex). The published methods and evaluation were **not read** and may differ from v1.
- **Status:** VERIFIED
- **Supports (arXiv v1 unless stated):** Closest identified human–algorithm collaboration framework for drug-discovery experiment selection under a fixed experimental budget. The algorithm recommends two batches per round (top-q by summed model uncertainty; top-h by a UCB-type search score), and an expert approves or overrides to choose the molecules tested. The published abstract's final ("For practice and policy") sentence states: "use AI to route scarce expert attention to the most informative experiments".
- **Limitations (v1 only):** v1 studies therapeutic peptides (SATPdb) with ESM2 embeddings, not small-molecule lead optimization. v1 uses one domain expert, and database labels serve as retrospective ground truth. The expert reviews a fixed recommendation set each round; there is no per-candidate escalation decision. Multiple properties are aggregated by summation, and no chemistry-specific review signals are used. **Statements about the number of experts, evaluation design, or mechanisms must not be assumed to hold for the published version.**

## REF-010 — Extracting medicinal chemistry intuition via preference machine learning

- **Authors:** Oh-Hyeon Choung, Riccardo Vianello, Marwin Segler, Nikolaus Stiefl, José Jiménez-Luna
- **Title:** Extracting medicinal chemistry intuition via preference machine learning
- **Year:** 2023
- **Venue:** Nature Communications, 14, 6651
- **DOI:** 10.1038/s41467-023-42242-1 (PMCID PMC10618272)
- **Access level:** Full text (targeted passages read from Europe PMC full-text XML)
- **Status:** VERIFIED
- **Supports:** Learning-to-rank from more than 5000 pairwise annotations by 35 Novartis chemists, with pair selection driven by active learning. Preliminary rounds report moderate inter-rater agreement (Fleiss' κ = 0.40 and 0.32) and fair intra-rater consistency (Cohen's κ = 0.60 and 0.59). The learned score is most correlated with QED.
- **Limitations:** Preferences were elicited without project context. The authors call the question an "oversimplification" and note that real decisions would include ADMET/activity data. Learned preferences are not shown to predict experimental outcomes. The result is a preference proxy, not a review-allocation policy.

## REF-011 — Interpretable models of chemist preferences

- **Authors:** Yasmine Nahal, Markus Heinonen, Mikhail Kabeshov, Jon Paul Janet, Eva Nittinger, Ola Engkvist, Samuel Kaski
- **Title:** Towards Interpretable Models of Chemist Preferences for Human-in-the-Loop Assisted Drug Discovery
- **Year:** 2024 (online); 2025 (print volume)
- **Venue:** AI in Drug Discovery, Lecture Notes in Computer Science, pp. 58–70. **LNCS volume number not verified:** the Crossref record omits it and the publisher page blocked automated access.
- **DOI:** 10.1007/978-3-031-72381-0_6
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** Decomposing binary like/dislike chemist feedback into interpretable preference models. Motivates handling subjective bias, noise, and inconsistency, and weighting experts by property-specific knowledge.
- **Limitations:** Abstract-level only, so no quantitative claims are taken from it. It addresses preference modelling, not review allocation.

## REF-012 — Metis: interface for chemistry-specific expert feedback

- **Authors:** Janosch Menke, Yasmine Nahal, Esben Jannik Bjerrum, Mikhail Kabeshov, Samuel Kaski, Ola Engkvist
- **Title:** Metis: a python-based user interface to collect expert feedback for generative chemistry models
- **Year:** 2024
- **Venue:** Journal of Cheminformatics, 16, 100
- **DOI:** 10.1186/s13321-024-00892-3
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** Prior tooling for collecting detailed, chemistry-specific feedback (desired/undesired substructures and properties) beyond binary like/dislike, integrated with REINVENT.
- **Limitations:** A data-collection tool. The abstract reports no evaluation of decision quality or review allocation.

## REF-013 — FSscore: personalized synthetic feasibility from expert feedback

- **Authors:** Rebecca M. Neeser, Bruno Correia, Philippe Schwaller
- **Title:** FSscore: A Personalized Machine Learning-Based Synthetic Feasibility Score
- **Year:** 2024
- **Venue:** Chemistry–Methods, 4(11), e202400024
- **DOI:** 10.1002/cmtd.202400024
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** Synthetic-feasibility ranking refined by expert human feedback for specific chemical spaces, as an example of HITL refinement of a chemistry-specific scoring component.
- **Limitations:** Abstract-level only. A synthesizability score, not route validation or review allocation.

## REF-022 — Bayesian optimisation in collaboration with human experts

- **Authors:** Wenjie Xu, Masaki Adachi, Colin N. Jones, Michael A. Osborne
- **Title:** Principled Bayesian Optimisation in Collaboration with Human Experts
- **Year:** 2024
- **Venue:** NeurIPS 2024
- **Venue source:** arXiv comment "Accepted to NeurIPS 2024 as a spotlight" (author-stated). The proceedings record was not independently checked.
- **Identifier:** arXiv:2410.10452
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** Expert accept/reject advice in BO, treated as costly and possibly unreliable. A "handover" guarantee bounds cumulative expert labels (expert effort declines asymptotically), and a "no-harm" guarantee with data-driven trust adjustment covers adversarial advice. Applied with human experts in battery design.
- **Limitations:** Not chemistry-specific to drug discovery. Expert involvement is reduced over time rather than allocated per candidate by consequence.

## REF-023 — Intermittent, asynchronous expert feedback for Bayesian optimization

- **Authors:** Agustinus Kristiadi, Felix Strieth-Kalthoff, Sriram Ganapathi Subramanian, Vincent Fortuin, Pascal Poupart, Geoff Pleiss
- **Title:** How Useful is Intermittent, Asynchronous Expert Feedback for Bayesian Optimization?
- **Year:** 2024
- **Venue:** AABI 2024 (workshop)
- **Venue source:** arXiv comment "AABI 2024" (author-stated). No published proceedings version found in OpenAlex.
- **Identifier:** arXiv:2406.06459 (v1, 10 Jun 2024; the only version)
- **Access level:** Abstract
- **Peer review:** Workshop paper / preprint; publication status beyond the workshop not established
- **Status:** VERIFIED
- **Supports:** A small amount of randomly arriving, non-blocking expert feedback, modelled as Bayesian preferences, can improve or constrain BO on toy and chemistry datasets.
- **Limitations:** Workshop-level evidence. Feedback timing is random rather than allocated.

---

## B. Chemist judgement, consistency, and multi-parameter decisions

## REF-014 — Consistency of medicinal chemists in reviewing compound sets

- **Authors:** Michael S. Lajiness, Gerald M. Maggiora, Veerabahu Shanmugasundaram
- **Title:** Assessment of the Consistency of Medicinal Chemists in Reviewing Sets of Compounds
- **Year:** 2004
- **Venue:** Journal of Medicinal Chemistry, 47(20), 4891–4896
- **DOI:** 10.1021/jm049740z
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** 13 medicinal chemists reviewing ~2000-compound lists (with a hidden 250-compound subset previously rejected by a senior chemist) were "not very consistent" in which compounds they rejected.
- **Limitations:** Compound-acquisition review (2002 Pharmacia programme), not lead optimization. Rejection decisions were not compared against experimental outcomes. Documents inconsistency, not error against independent outcomes.

## REF-015 — Human bias in compound prioritization

- **Authors:** Peter S. Kutchukian, Nadya Y. Vasilyeva, Jordan Xu, Mika K. Lindvall, Michael P. Dillon, Meir Glick, John D. Coley, Natasja Brooijmans
- **Title:** Inside the Mind of a Medicinal Chemist: The Role of Human Bias in Compound Prioritization during Drug Discovery
- **Year:** 2012
- **Venue:** PLoS ONE, 7(11), e48476
- **DOI:** 10.1371/journal.pone.0048476
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** In fragment selection (~4000 fragments), chemists typically used only 1–2 parameters, showed low consensus, agreed mainly on undesirable fragments, and were often unaware of the parameters driving their choices.
- **Limitations:** Fragment selection task. No link to downstream experimental success. Documents preference behaviour and low consensus, not error against independent outcomes.

## REF-016 — Multi-parameter optimization in drug discovery

- **Authors:** Matthew D. Segall
- **Title:** Multi-Parameter Optimization: Identifying High Quality Compounds with a Balance of Properties
- **Year:** 2012
- **Venue:** Current Pharmaceutical Design, 18(9), 1292–1310
- **DOI:** 10.2174/138161212799436430
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** A review of MPO approaches (rules of thumb, desirability functions, Pareto optimization, and probabilistic approaches that account for predictive error and experimental variability).
- **Limitations:** A review, not an evaluation of human-review allocation.

## REF-008 — Impact of expert review on ICH M7 (Q)SAR predictions

- **Authors:** P. Suresh Jayasekara, Sophie K. Skanchy, Marlene T. Kim, Govindaraj Kumaran, Benon E. Mugabe, Lauren E. Woodard, Jian Yang, Andrew J. Zych, Naomi L. Kruhlak
- **Title:** Assessing the impact of expert knowledge on ICH M7 (Q)SAR predictions. Is expert review still needed?
- **Year:** 2021
- **Venue:** Regulatory Toxicology and Pharmacology, 125, 105006
- **DOI:** 10.1016/j.yrtph.2021.105006
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** A retrospective analysis of 1002 drug impurities in which expert review overturned 26% of default (Q)SAR mutagenicity predictions and resolved 91% of equivocal and 75% of out-of-domain calls. Overturns concentrated in specific chemical classes (e.g., primary aromatic amines, aldehydes, Michael acceptors) and in low-confidence predictions. The authors suggest that triaging predictions by chemical class and probability can improve review efficiency.
- **Limitations:** Regulatory mutagenicity of impurities, not lead optimization. The abstract reports overturn rates, not whether overturns were experimentally correct. The analysis is retrospective and does not implement or evaluate a triage policy; the triage approach is a suggestion.

## REF-009 — Common arguments in ICH M7 expert review

- **Authors:** Alex N. Cayley, Robert S. Foster, Alessandro Brigo, Wolfgang Muster, Alyssa Musso, Michelle O. Kenyon, Patricia Parris, Angela T. White, Mirit Cohen-Ohana, Raphael Nudelman, Susanne Glowienke
- **Title:** Assessing the utility of common arguments used in expert review of in silico predictions as part of ICH M7 assessments
- **Year:** 2023
- **Venue:** Regulatory Toxicology and Pharmacology, 144, 105490
- **DOI:** 10.1016/j.yrtph.2023.105490
- **Access level:** Abstract (via Europe PMC)
- **Status:** VERIFIED
- **Supports:** Standardised expert-review arguments were assigned to recurring prediction scenarios and their likelihood of reaching the correct resolution was assessed on pharma-donated data. A small set of arguments resolved many scenarios. This is an example of structured, category-based expert reasoning evaluated against outcomes.
- **Limitations:** Regulatory mutagenicity domain and vendor-specific (Derek Nexus/Sarah Nexus) setting. Quantitative details were not read.

## REF-042 — The role of human in the loop: lessons from D3R Challenge 4

- **Authors:** Oleg V. Stroganov, Fedor N. Novikov, Michael G. Medvedev, Artem O. Dmitrienko, Igor Gerasimov, Igor V. Svitanko, Ghermes G. Chilov
- **Title:** The role of human in the loop: lessons from D3R challenge 4
- **Year:** 2020
- **Venue:** Journal of Computer-Aided Molecular Design, 34(2), 121–130
- **DOI:** 10.1007/s10822-020-00291-4 (PMID 31965405)
- **Access level:** Abstract (via Europe PMC)
- **Status:** VERIFIED
- **Supports:** In D3R Grand Challenge 4 (protein–ligand complex structure prediction and binding-affinity prediction), human decisions showed biases (a tendency to focus on easily identifiable interactions such as hydrogen bonds and to neglect distributed electrostatic and solvation effects). Human experts could compete with blind algorithms in some areas, but underutilisation of information led to significantly worse performance in data-rich tasks such as binding-affinity prediction.
- **Limitations:** Structure/affinity prediction challenge participants, not lead-optimization decision review. It characterises human contribution relative to algorithms and does not evaluate a capacity-constrained review policy. Full text was not read.

---

## C. Active learning, value of information, and query cost

## REF-017 — Prediction-oriented Bayesian active learning (EPIG)

- **Authors:** Freddie Bickford Smith, Andreas Kirsch, Sebastian Farquhar, Yarin Gal, Adam Foster, Tom Rainforth
- **Title:** Prediction-Oriented Bayesian Active Learning
- **Year:** 2023
- **Venue:** AISTATS 2023
- **Venue source:** arXiv comment "Published at AISTATS 2023" (author-stated). The proceedings record was not independently checked.
- **Identifier:** arXiv:2304.08151
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** EPIG measures information gain in prediction space with respect to a target input distribution, addressing the tendency of BALD to prioritise data of limited relevance.
- **Limitations:** A general ML acquisition function, with no review cost or decision consequences.

## REF-018 — Selective supervision: decision-theoretic active learning

- **Authors:** Ashish Kapoor, Eric Horvitz, Sumit Basu
- **Title:** Selective Supervision: Guiding Supervised Learning with Decision-Theoretic Active Learning
- **Year:** 2007
- **Venue:** Proceedings of IJCAI 2007, pp. 877–882
- **URL:** https://www.ijcai.org/Proceedings/07/Papers/141.pdf
- **Access level:** Full text (pp. 877–878 read directly)
- **Status:** VERIFIED
- **Supports:** Defines the value of information of labeling a point as the expected reduction in total misclassification risk (with class-dependent misclassification costs) minus the cost of obtaining the label, and uses it to "triage" human labeling effort.
- **Limitations:** Myopic (one label at a time), classifier-training objective, voice-message domain. It is not about expert correction of decisions.

## REF-019 — Combining crowd and expert labels with decision-theoretic active learning

- **Authors:** An Nguyen, Byron Wallace, Matthew Lease
- **Title:** Combining Crowd and Expert Labels Using Decision Theoretic Active Learning
- **Year:** 2015
- **Venue:** Proceedings of the AAAI Conference on Human Computation and Crowdsourcing (HCOMP), 3, 120–129
- **DOI:** 10.1609/hcomp.v3i1.13225
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** Finite-pool, budget-limited exhaustive classification that allocates items across machine, crowd, and expert tiers using decision-theoretic active learning (biomedical citation screening).
- **Limitations:** Not chemistry. Labels, not decision corrections.

## REF-020 — Active-learning strategies in computer-assisted drug discovery

- **Authors:** Daniel Reker, Gisbert Schneider
- **Title:** Active-learning strategies in computer-assisted drug discovery
- **Year:** 2015
- **Venue:** Drug Discovery Today, 20(4), 458–465
- **DOI:** 10.1016/j.drudis.2014.12.004
- **Access level:** Metadata only (abstract not available in the indexes queried)
- **Status:** VERIFIED (metadata)
- **Supports:** Existence of an established review of active learning in drug discovery, cited only as a pointer to that literature.
- **Limitations:** Content not read. Must not be cited for specific claims until read.

## REF-021 — Query strategies in drug-discovery active learning

- **Authors:** Huw J. Williams, Stephen D. Pickett, Andrew Baxter, David S. Palmer
- **Title:** Query Matters: How Selection Strategies Influence Active Learning in Drug Discovery
- **Year:** 2026
- **Venue:** Journal of Chemical Information and Modeling, 66(6), 3288–3301
- **DOI:** 10.1021/acs.jcim.5c02504
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** In a simulated DMTA cycle using docking scores as an assay proxy (BRD4 BD1, isoxazole-derived scaffold), uncertainty-based sampling outperformed greedy and hybrid strategies in hit discovery and generalisation; strategies with random components corrected bias faster.
- **Limitations:** Docking scores are a proxy, not experimental affinity. No human reviewer is involved.

## REF-040 — Knowledge-gradient algorithm for sequencing experiments in drug discovery

- **Authors:** Diana M. Negoescu, Peter I. Frazier, Warren B. Powell
- **Title:** The Knowledge-Gradient Algorithm for Sequencing Experiments in Drug Discovery
- **Year:** 2011
- **Venue:** INFORMS Journal on Computing, 23(3), 346–363
- **DOI:** 10.1287/ijoc.1100.0417
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** Decision-oriented experiment selection in drug discovery: choosing which molecules to test to maximise the expected quality of the best compound discovered, formulated as ranking-and-selection with a Bayesian prior that uses correlations between molecules. Demonstrated on a problem with 87,120 alternatives, starting from a base compound.
- **Limitations:** Selects *experiments*, not medicinal-chemist review. Single-property best-compound objective. Abstract-level only. Cited in REF-007 as a seminal work.

---

## D. Deferral, selective prediction, triage, and human–AI complementarity

## REF-024 — Learning to defer

- **Authors:** David Madras, Toniann Pitassi, Richard Zemel
- **Title:** Predict Responsibly: Improving Fairness and Accuracy by Learning to Defer
- **Year:** 2018
- **Venue:** NeurIPS 2018
- **Venue source:** arXiv comment "Accepted as a conference paper at Neural Information Processing Systems 2018", also listed as a NeurIPS location in OpenAlex.
- **Identifier:** arXiv:1711.06664
- **Access level:** Metadata and arXiv record
- **Status:** VERIFIED (metadata)
- **Supports:** Origin of the learning-to-defer framing, cited for provenance only.
- **Limitations:** Content not read beyond the record. Do not cite for specific claims.

## REF-025 — Consistent estimators for learning to defer

- **Authors:** Hussein Mozannar, David Sontag
- **Title:** Consistent Estimators for Learning to Defer to an Expert
- **Year:** 2020
- **Venue:** ICML 2020
- **Venue source:** arXiv comment "ICML 2020", also listed as an ICML location in OpenAlex.
- **Identifier:** arXiv:2006.01862
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** Jointly learning a classifier and a rejector that defers to a downstream expert, using samples of expert decisions and a consistent cost-sensitive surrogate loss.
- **Limitations:** Generic supervised classification. No capacity constraint in the abstract.

## REF-026 — Selective classification for deep neural networks

- **Authors:** Yonatan Geifman, Ran El-Yaniv
- **Title:** Selective Classification for Deep Neural Networks
- **Year:** 2017
- **Venue:** NeurIPS 2017
- **Venue source:** listed as a NeurIPS proceedings record in OpenAlex; the arXiv page lists no comment or journal reference.
- **Identifier:** arXiv:1705.08500
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** Rejection of instances to guarantee a user-specified risk level, trading risk against coverage.
- **Limitations:** Image classification. Abstention is not routed to an expert.

## REF-027 — The algorithmic automation problem

- **Authors:** Maithra Raghu, Katy Blumer, Greg Corrado, Jon Kleinberg, Ziad Obermeyer, Sendhil Mullainathan
- **Title:** The Algorithmic Automation Problem: Prediction, Triage, and Human Effort
- **Year:** 2019
- **Identifier:** arXiv:1903.12220
- **Access level:** Abstract
- **Peer review:** NOT PEER-REVIEWED as far as established: arXiv lists no journal reference, and no published version was found in OpenAlex (2026-10-20)
- **Status:** VERIFIED
- **Supports:** Automation includes deciding which instances go to the algorithm. Effective triage requires instance-level estimates of both algorithmic and human error (medical applications).
- **Limitations:** Preprint. Medical rather than chemistry tasks.

## REF-028 — Differentiable learning under triage

- **Authors:** Nastaran Okati, Abir De, Manuel Gomez-Rodriguez
- **Title:** Differentiable Learning Under Triage
- **Year:** 2021
- **Venue:** NeurIPS 2021
- **Venue source:** listed as a NeurIPS location in OpenAlex; the arXiv page lists no journal reference.
- **Identifier:** arXiv:2103.08902 (revised version fixes a baseline implementation bug)
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** For a given model and triage level, the optimal triage policy is a deterministic threshold on the per-instance difference between model and human error. Models trained for full automation can be suboptimal under triage. Includes a scientific-discovery application.
- **Limitations:** Assumes human error is estimable per instance. Supervised-learning setting.

## REF-029 — Cost-sensitive deferral under expert capacity constraints (DeCCaF)

- **Authors:** Jean V. Alves, Diogo Leitão, Sérgio Jesus, Marco O. P. Sampaio, Javier Liébana, Pedro Saleiro, Mário A. T. Figueiredo, Pedro Bizarro
- **Title:** Cost-Sensitive Learning to Defer to Multiple Experts with Workload Constraints
- **Year:** 2024
- **Venue:** Transactions on Machine Learning Research (07/2024)
- **Venue source:** the published PDF's header reads "Published in Transactions on Machine Learning Research (07/2024)" and links its OpenReview review; the TMLR and OpenReview pages themselves were not retrievable. The earlier entry (NOT PEER-REVIEWED) was an error from relying on arXiv metadata alone.
- **Identifier:** arXiv:2403.06906 (v3, 19 Aug 2024)
- **Access level:** Abstract and first page of the published PDF
- **Status:** VERIFIED
- **Supports:** Deferral that models the probability of human error, minimises asymmetric error cost globally with constraint programming, and respects individual expert work-capacity limits. Tested with teams of 9 synthetic fraud analysts.
- **Limitations:** Synthetic experts in fraud detection; no human chemistry validation.

## REF-030 — Learning to defer with limited expert predictions

- **Authors:** Patrick Hemmer, Lukas Thede, Michael Vössing, Johannes Jakubik, Niklas Kühl
- **Title:** Learning to Defer with Limited Expert Predictions
- **Year:** 2023
- **Venue:** Proceedings of the AAAI Conference on Artificial Intelligence, 37(5), 6002–6011
- **DOI:** 10.1609/aaai.v37i5.25742
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** Learning-to-defer methods need many expert predictions to learn where the expert is better. The paper reduces this requirement by training an expertise predictor, using synthetic experts and real radiologists.
- **Limitations:** Not chemistry. Requires some expert predictions alongside ground truth.

## REF-031 — Optimizing AI for teamwork

- **Authors:** Gagan Bansal, Besmira Nushi, Ece Kamar, Eric Horvitz, Daniel S. Weld
- **Title:** Is the Most Accurate AI the Best Teammate? Optimizing AI for Teamwork
- **Year:** 2021
- **Venue:** Proceedings of the AAAI Conference on Artificial Intelligence, 35(13), 11405–11414
- **DOI:** 10.1609/aaai.v35i13.17359
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** Team expected utility expressed in terms of final-decision quality, the human's cost of verifying, individual human/machine accuracies, and the cost of mistakes. The most accurate AI is not necessarily the best teammate.
- **Limitations:** Accept-or-solve-yourself setting. Not chemistry.

## REF-032 — Bayesian modelling of human–AI complementarity

- **Authors:** Mark Steyvers, Heliodoro Tejeda, Gavin Kerrigan, Padhraic Smyth
- **Title:** Bayesian modeling of human–AI complementarity
- **Year:** 2022
- **Venue:** Proceedings of the National Academy of Sciences, 119(11), e2111547119
- **DOI:** 10.1073/pnas.2111547119
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** Factors that determine whether hybrid human–machine combinations outperform either alone, accounting for how human and machine confidence are expressed.
- **Limitations:** Not chemistry. Abstract-level only.

## REF-033 — Machine learning with a reject option (survey)

- **Authors:** Kilian Hendrickx, Lorenzo Perini, Dries Van der Plas, Wannes Meert, Jesse Davis
- **Title:** Machine learning with a reject option: a survey
- **Year:** 2024
- **Venue:** Machine Learning, 113(5), 3073–3110
- **DOI:** 10.1007/s10994-024-06534-x
- **Access level:** Metadata only (abstract not available in the indexes queried)
- **Status:** VERIFIED (metadata)
- **Supports:** A survey pointer for the reject-option literature.
- **Limitations:** Content not read. Must not be cited for specific claims until read.

## REF-041 — Post-processing framework for multi-objective learn-to-defer

- **Authors:** Mohammad-Amin Charusaie, Samira Samadi
- **Title:** A Unifying Post-Processing Framework for Multi-Objective Learn-to-Defer Problems
- **Year:** 2024
- **Venue:** Advances in Neural Information Processing Systems 37 (NeurIPS 2024), pp. 23705–23755
- **DOI:** 10.52202/079017-0748 (also arXiv:2407.12710)
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** The Bayes-optimal solution for learn-to-defer systems under constraints (the abstract lists algorithmic fairness, expert intervention budget, and deferral of anomalies), derived with a d-dimensional generalisation of the Neyman–Pearson lemma, with an estimation algorithm applied to COMPAS and ACSIncome.
- **Limitations:** General tabular datasets, not chemistry. The "multiple objectives" are system constraints, not medicinal-chemistry endpoints. Abstract-level only.

## REF-043 — Benchmarking framework and dataset for learning to defer

- **Authors:** Jean V. Alves, Diogo Leitão, Sérgio Jesus, Marco O. P. Sampaio, Javier Liébana, Pedro Saleiro, Mário A. T. Figueiredo, Pedro Bizarro
- **Title:** A benchmarking framework and dataset for learning to defer in human-AI decision-making
- **Year:** 2025
- **Venue:** Scientific Data, 12, 506
- **DOI:** 10.1038/s41597-025-04664-y
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** OpenL2D generates synthetic experts with adjustable decision processes and work-capacity constraints; applied to a public fraud dataset to build FiFAR (predictions from 50 fraud analysts on 30K instances). The authors report that the synthetic experts resemble real experts in consistency and inter-expert agreement, and that learning-to-defer algorithm rankings vary significantly with the available experts.
- **Limitations:** Fraud domain with synthetic experts. No human chemistry validation. Abstract-level only.

## REF-044 — Online decision deferral under budget constraints

- **Authors:** Mirabel Reid, Tom Sühr, Claire Vernade, Samira Samadi
- **Title:** Online Decision Deferral under Budget Constraints
- **Year:** 2024
- **Identifier:** arXiv:2409.20489 (v1, 30 Sep 2024; the only version)
- **Access level:** arXiv abstract page (summary read)
- **Peer review:** NOT PEER-REVIEWED as far as established: arXiv lists no journal reference and no published version was checked
- **Status:** VERIFIED
- **Supports:** Deciding when an ML model should act versus defer to a scarce human expert, modelled as a contextual bandit with budget limits, shifting task distributions, and several kinds of partial feedback; the authors report theoretical guarantees and practical extensions on real-world datasets.
- **Limitations:** Preprint. Not chemistry. Treated as preliminary prior art.

---

## E. Uncertainty, conformal prediction, and selective prediction in chemistry

## REF-005 — Conformal prediction in drug discovery

- **Authors:** Jonathan Alvarsson, Staffan Arvidsson McShane, Ulf Norinder, Ola Spjuth
- **Title:** Predicting With Confidence: Using Conformal Prediction in Drug Discovery
- **Year:** 2021 (issue; published online 2020)
- **Venue:** Journal of Pharmaceutical Sciences, 110(1), 42–49
- **DOI:** 10.1016/j.xphs.2020.09.055
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** An introduction to conformal prediction for QSAR, giving object-specific prediction intervals/sets with error-rate guarantees and applicability-domain handling linked to the nonconformity function.
- **Limitations:** Project assessment, not stated in the abstract: conformal validity guarantees generally assume exchangeability between calibration and test data, so they should not be assumed to hold under the distribution shift typical of lead optimization or of temporal/scaffold splits. The paper does not address allocation of expert attention.

## REF-006 — Selective prediction / abstention in chemical toxicity

- **Authors:** Jeremy Feinstein, Ganesh Sivaraman, Kurt Picel, Brian Peters, Álvaro Vázquez-Mayagoitia, Arvind Ramanathan, Margaret MacDonell, Ian Foster, Eugene Yan
- **Title:** Uncertainty-Informed Deep Transfer Learning of Perfluoroalkyl and Polyfluoroalkyl Substance Toxicity
- **Year:** 2021
- **Venue:** Journal of Chemical Information and Modeling, 61(12), 5793–5803
- **DOI:** 10.1021/acs.jcim.1c01204
- **Access level:** Abstract
- **Status:** VERIFIED (year corrected from 2022 on 2026-10-20)
- **Supports:** Transfer-learned deep-ensemble toxicity models for PFAS, embedded in a SelectiveNet architecture that abstains in high-uncertainty regions using a calibrated cutoff.
- **Limitations:** Abstention is a predict/abstain decision for toxicity, not routing to a medicinal chemist. Not a lead-optimization setting.

## REF-034 — Evaluating scalable uncertainty estimation for molecular property prediction

- **Authors:** Gabriele Scalia, Colin A. Grambow, Barbara Pernici, Yi-Pei Li, William H. Green
- **Title:** Evaluating Scalable Uncertainty Estimation Methods for Deep Learning-Based Molecular Property Prediction
- **Year:** 2020
- **Venue:** Journal of Chemical Information and Modeling, 60(6), 2697–2717
- **DOI:** 10.1021/acs.jcim.9b00975
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** Compares MC-dropout, deep ensembles, and bootstrapping for graph-convolutional molecular property models. Ensembles and bootstrapping consistently outperformed MC-dropout, and out-of-domain uncertainty remains challenging.
- **Limitations:** Public benchmark datasets. No decision or review layer.

## REF-035 — Uncertainty quantification under data shifts for ADME prediction

- **Authors:** Raquel Parrondo-Pizarro, Jessica Lanini, Raquel Rodríguez-Pérez
- **Title:** Uncertainty Quantification in Molecular Machine Learning for Property Predictions under Data Shifts
- **Year:** 2026
- **Venue:** Journal of Chemical Information and Modeling, 66(2), 923–935
- **DOI:** 10.1021/acs.jcim.5c02381
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** No single UQ method consistently wins. Distance-based and model-based UQ metrics capture complementary aspects, and error models combining them gave higher-quality uncertainty estimates under various data shifts (ADME endpoints; in-house and public data).
- **Limitations:** In-house data are not public. No human-review layer.

---

## F. LLM agents and LLM–expert comparison in chemistry

## REF-003 — ChemCrow

- **Authors:** Andres M. Bran, Sam Cox, Oliver Schilter, Carlo Baldassari, Andrew D. White, Philippe Schwaller
- **Title:** Augmenting large language models with chemistry tools
- **Year:** 2024
- **Venue:** Nature Machine Intelligence, 6(5), 525–535
- **DOI:** 10.1038/s42256-024-00832-8
- **Access level:** Abstract
- **Status:** VERIFIED (author list corrected 2026-10-20)
- **Supports:** A GPT-4 agent with 18 expert-designed tools across synthesis, drug discovery, and materials design, evaluated by LLM and expert assessment.
- **Limitations:** Demonstrates capability, not reliability-calibrated decision support or review allocation.

## REF-004 — Coscientist

- **Authors:** Daniil A. Boiko, Robert MacKnight, Ben Kline, Gabe Gomes
- **Title:** Autonomous chemical research with large language models
- **Year:** 2023
- **Venue:** Nature, 624(7992), 570–578
- **DOI:** 10.1038/s41586-023-06792-0
- **Access level:** Abstract
- **Status:** VERIFIED (author list corrected 2026-10-20)
- **Supports:** A GPT-4-driven system that designs, plans, and performs experiments using search, code execution, and laboratory automation across six tasks.
- **Limitations:** Not drug-discovery lead optimization. No human-review allocation.

## REF-036 — Review of LLMs and autonomous agents in chemistry

- **Authors:** Mayk Caldas Ramos, Christopher J. Collison, Andrew D. White
- **Title:** A review of large language models and autonomous agents in chemistry
- **Year:** 2025
- **Venue:** Chemical Science, 16(6), 2514–2572
- **DOI:** 10.1039/d4sc03921a
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** A broad review of chemistry LLMs and agents. Key challenges are data quality, interpretability, and the need for standard benchmarks.
- **Limitations:** A review. Used as a field pointer only.

## REF-037 — ChemBench: LLMs versus chemists

- **Authors:** Adrian Mirza, Nawaf Alampara, Sreekanth Kunchapu, Martiño Ríos-García, Benedict Emoekabu, Aswanth Krishnan, Tanya Gupta, Mara Schilling-Wilhelmi, Macjonathan Okereke, Anagha Aneesh, Mehrdad Asgari, Juliane Eberhardt, Amir Mohammad Elahi, Hani M. Elbeheiry, María Victoria Gil, Christina Glaubitz, Maximilian Greiner, Caroline T. Holick, Tim Hoffmann, Abdelrahman Ibrahim, Lea C. Klepsch, Yannik Köster, Fabian Alexander Kreth, Jakob Meyer, Santiago Miret, Jan Matthias Peschel, Michael Ringleb, Nicole C. Roesner, Johanna Schreiber, Ulrich S. Schubert, Leanne M. Stafast, A. D. Dinga Wonanke, Michael Pieler, Philippe Schwaller, Kevin Maik Jablonka
- **Title:** A framework for evaluating the chemical knowledge and reasoning abilities of large language models against the expertise of chemists
- **Year:** 2025
- **Venue:** Nature Chemistry, 17(7), 1027–1034
- **DOI:** 10.1038/s41557-025-01815-x
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** On more than 2700 question–answer pairs, the best LLMs on average outperformed the best human chemists in the study, yet struggled with some basic tasks and gave overconfident predictions.
- **Limitations:** A question-answering benchmark, not lead-optimization decisions. Supports excluding LLM self-reported confidence as scientific uncertainty (DR-005).

## REF-038 — Agreement between LLMs and chemists on synthesis-plan quality

- **Authors:** Varvara Voinarovska, Rocío Mercado, Mikhail Kabeshov, Samuel Genheden
- **Title:** Do humans and large language models agree on the quality of synthesis plans?
- **Year:** 2026
- **Venue:** Digital Discovery, 5(9), 3648–3660
- **DOI:** 10.1039/d6dd00266h
- **Access level:** Abstract
- **Status:** VERIFIED
- **Supports:** 17 expert chemists graded 50 AiZynthFinder retrosynthetic routes. Experts tended to converge when given clear evaluation categories, and LLM agreement with the expert majority varied by model (some systematically optimistic or pessimistic).
- **Limitations:** Synthesis-route assessment only. Expert majority vote, not experimental route success, is the reference.

## REF-039 — Mozi: governed autonomy for drug-discovery LLM agents

- **Authors:** He Cao, Siyu Liu, Fan Zhang, Zijing Liu, Hao Li, Bin Feng, Shengyuan Bai, Leqing Chen, Kai Xie, Yu Li
- **Title:** Mozi: Governed Autonomy for Drug Discovery LLM Agents
- **Year:** 2026
- **Identifier:** arXiv:2603.03655 (v1, 4 Mar 2026; the only version)
- **Access level:** Abstract
- **Peer review:** NOT PEER-REVIEWED as far as established: arXiv lists no journal reference and no published version was found in OpenAlex (2026-10-20)
- **Status:** VERIFIED
- **Supports:** A drug-discovery agent architecture with governed tool use, stateful workflow stages from target identification to lead optimization, and "strategic human-in-the-loop (HITL) checkpoints" at high-uncertainty decision boundaries.
- **Limitations:** Preprint. The abstract does not specify how checkpoints are triggered, budgeted, or evaluated against expert outcomes.

---

## Reference policy

Before a new `REF-xxx` entry is marked VERIFIED:

1. confirm the title, authorship, year, venue, and DOI/authoritative URL against an authoritative record (Crossref, publisher, proceedings, or arXiv);
2. read enough of the source to support the exact claim being made, and record the **Access level**;
3. when only the abstract was read, limit claims citing the entry to what the abstract states;
4. mark entries whose content was not read as **VERIFIED (metadata)** and do not cite them for substantive claims;
5. determine publication status from an authoritative record, not from the absence of a journal reference on an arXiv page. Flag preprints and workshop papers as such. They may be cited as clearly labelled prior art or preliminary work, including to challenge a novelty hypothesis, but must not be the sole basis for upgrading a novelty label to SUPPORTED or for a claim that a method is effective in practice;
6. record limitations relevant to the project;
7. do not infer novelty merely because a specific phrase is absent from the title/abstract.

IDs are assigned in order of addition and are not renumbered; entries are grouped by topic for readability.
