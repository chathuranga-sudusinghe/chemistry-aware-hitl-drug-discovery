# Literature Search Protocol and Log

## Status

**Round 1 and Round 1b (corrections after independent review) complete (2026-10-20), Issue #2. The overall search is NOT complete: the saturation stopping rule has not been met (see §8–§9).** This is a **structured, documented narrative review**, not a PRISMA systematic review. It is designed to be auditable and extendable, not exhaustive.

## 1. Purpose

Identify the prior work closest to the project's proposed contribution:

- chemistry-aware allocation of limited expert review;
- escalation (whether to review) separated from prioritization (what to review first);
- how prior studies evaluated expert benefit.

The results inform the novelty labels in [`novelty.md`](novelty.md) and the gap statement in [`research-gap.md`](research-gap.md).

## 2. Sources

| Source | Use |
|---|---|
| OpenAlex API | Keyword search; forward citation tracing (`cites:` filter); abstracts |
| Crossref API | Bibliographic verification of DOIs |
| arXiv abstract pages | Author lists, versions, venue comments for preprints/conference papers |
| Europe PMC (REST, full-text XML) | Open-access full text and abstracts |
| PubMed Central (via automated reader) | Targeted full-text questions for REF-001 and REF-002 |
| Publisher / proceedings pages | IJCAI 2007 proceedings; the published TMLR PDF of REF-029 (first page); journal landing pages for the re-screened items in §7 |
| Europe PMC (abstracts) | REF-042 abstract |

**Not used:**

- Google Scholar (not reproducibly queryable);
- DBLP and the Semantic Scholar API (automated access was blocked or rate-limited on the search date);
- the INFORMS, Springer, OpenReview, PMLR, and NeurIPS proceedings pages (automated access was blocked or failed in Round 1b). This is why the published version of REF-007 was not read, the REF-011 LNCS volume number was not verified, and the venues of REF-017 and REF-022 rest on author-stated arXiv comments;
- direct PubMed pages (blocked automated access).

## 3. Topic areas

| ID | Topic |
|---|---|
| A | HITL / interactive molecular design; eliciting chemists' preferences |
| B | Active learning and BO acquisition in chemistry, incl. goal-directed and cost-aware acquisition |
| C | Value of information and decision-theoretic query selection; decision-focused learning |
| D | Learning to defer, selective classification, human–AI complementarity, triage |
| E | Uncertainty and applicability domain under distribution shift (light coverage; detail deferred to Issue #8) |
| F | Medicinal-chemistry decision support: MPO, chemist intuition, inter-chemist agreement |
| G | LLM agents in drug discovery and evidence of their added value |
| H | How HITL studies are evaluated: simulated oracles, retrospective data, real experts |

## 4. Eligibility

**Include:**

- methods that select, allocate, or route expert/oracle/query effort, or that defer decisions, in molecular/chemical or general ML settings;
- empirical evidence on the reliability or consistency of chemist judgement;
- uncertainty/selective-prediction work in chemistry that informs when predictions should not be trusted;
- LLM-agent work in chemistry/drug discovery that involves human oversight or evaluates agents against experts.

**Exclude:**

- molecular property-prediction benchmarks with no uncertainty, deferral, or human component;
- generative-model papers with no human/query component;
- non-English papers;
- conceptual/position pieces that present neither a method nor an evaluation, unless they are field reviews used only as pointers;
- items for which bibliographic metadata could not be verified.

## 5. Screening procedure

1. Run each keyword query in OpenAlex (relevance-ranked). Screen the **top N** titles (N recorded per query).
2. Screen abstracts for title-relevant hits.
3. For the closest comparators, read the full text (direct reading or targeted automated extraction; access level recorded per reference).
4. Trace citations forward from the closest works (REF-001, REF-002, REF-008), and backward through the reference lists of REF-007 and REF-010.
5. Verify the metadata of every included item against Crossref or arXiv/proceedings.

**Caveat on hit counts:** OpenAlex full-text relevance search matches any query term, so the "total hits" column is a loose upper bound and not a measure of relevant literature. Screening depth is the meaningful number.

## 6. Search log (2026-10-20)

| # | Source | Query / action | Total hits | Screened | Topic | Included from this query |
|---|---|---|---|---|---|---|
| 1 | OpenAlex forward | works citing REF-002 (W4405183594) | 32 | 32 | A, B, G | REF-007 (also found in #2), REF-021, REF-038 |
| 2 | OpenAlex forward | works citing REF-001 (W4313339550) | 39 | 39 | A | REF-007, REF-011, REF-012 |
| 3 | OpenAlex | human-in-the-loop molecular design medicinal chemist feedback | 1286 | 12 | A | (REF-001, REF-011 already found) |
| 4 | OpenAlex | medicinal chemist preference learning molecules | 2154 | 12 | A, F | REF-010, REF-015 |
| 5 | OpenAlex | medicinal chemistry intuition machine learning pairwise preferences | 118 | 12 | A, F | REF-013 |
| 6 | OpenAlex | medicinal chemists agreement compound selection consistency | 1105 | 12 | F | REF-037 |
| 7 | OpenAlex | expert review allocation budget human-in-the-loop drug discovery | 2211 | 12 | A, G | none (see exclusions) |
| 8 | OpenAlex | when to involve human expert drug discovery machine learning deferral | 2870 | 12 | D | REF-033 |
| 9 | OpenAlex | assessment of the consistency of medicinal chemists in reviewing sets of compounds | 2529 | 8 | F | REF-014 |
| 10 | OpenAlex | learning to defer to an expert | 82322 | 8 | D | REF-025, REF-029, REF-030 |
| 11 | OpenAlex | consistent estimators for learning to defer | 14231 | 8 | D | — |
| 12 | OpenAlex | selective classification for deep neural networks | 208488 | 8 | D | REF-026 |
| 13 | OpenAlex | algorithmic automation problem prediction triage human | 8159 | 8 | D | REF-027 |
| 14 | OpenAlex | differentiable learning under triage | 25588 | 8 | D | REF-028 |
| 15 | OpenAlex | is the most accurate AI the best teammate | 5263 | 8 | D | REF-031 |
| 16 | OpenAlex | human-AI complementarity | 62305 | 8 | D | REF-032 |
| 17 | OpenAlex | prediction-oriented Bayesian active learning expected predictive information gain | 25569 | 8 | B | REF-017 |
| 18 | OpenAlex | decision-theoretic active learning value of information | 1149302 | 8 | C | REF-018, REF-019 |
| 19 | OpenAlex | knowledge gradient optimal learning | 479107 | 8 | C | none (follow-up) |
| 20 | OpenAlex | cost-sensitive active learning annotation cost | 54394 | 8 | C | none |
| 21 | OpenAlex | active learning drug discovery review | 236427 | 8 | B | (pointer only) |
| 22 | OpenAlex | active learning compound selection lead optimization | 117538 | 8 | B | none |
| 23 | OpenAlex | Bayesian optimization human expert feedback chemistry | 6269 | 8 | A, B | REF-022, REF-023 |
| 24 | OpenAlex | decision-focused learning predict-then-optimize | 1093412 | 8 | C | none (follow-up) |
| 25 | OpenAlex | large language model agents drug discovery benchmark evaluation | 19201 | 8 | G | none |
| 26 | OpenAlex | LLM agent medicinal chemistry lead optimization | 720 | 8 | G | REF-036, REF-039 |
| 27 | OpenAlex | multi-agent large language model drug discovery autonomous | 16677 | 8 | G | none |
| 28 | OpenAlex | multi-parameter optimization drug discovery desirability functions | 28506 | 8 | F | REF-016 |
| 29 | OpenAlex | uncertainty quantification molecular property prediction distribution shift evaluation | 60957 | 8 | E | REF-034, REF-035 |
| 30 | OpenAlex | conformal prediction molecular property distribution shift exchangeability | 19098 | 8 | E | none (mostly 2026 preprints; follow-up for Issue #8) |
| 31 | OpenAlex | applicability domain QSAR review | 11816 | 8 | E | none (deferred to Issue #8) |
| 32 | OpenAlex | simulated oracle human feedback evaluation molecular generation real chemists | 78 | 8 | H | (REF-001, REF-002 already found) |
| 33 | OpenAlex | predict responsibly improving fairness and accuracy by learning to defer | 1331 | 5 | D | REF-024 |
| 34 | OpenAlex | active-learning strategies in computer-assisted drug discovery | 49092 | 5 | B | REF-020 |
| 35 | OpenAlex | expert review triage QSAR predictions medicinal chemist | 98 | 10 | D, F, H | REF-008 |
| 36 | OpenAlex | value of information compound selection drug discovery | 178027 | 10 | C | none |
| 37 | OpenAlex | learning to defer chemistry molecular property | 3549 | 10 | D | none |
| 38 | OpenAlex | human-AI collaboration compound prioritization medicinal chemistry decision | 1579 | 10 | A, F | none |
| 39 | OpenAlex | structured expert feedback rationale molecules generative design | 2068 | 10 | A | none |
| 40 | OpenAlex | expected value of information experiment selection lead optimization | 582612 | 10 | C | none |
| 41 | OpenAlex forward | works citing REF-008 (W3181556332) | 24 | 15 | D, H | REF-009 |
| 42 | Backward | reference list of REF-010 (refs 1–20) | — | 20 | F | (REF-014, REF-015 confirmed) |
| 43 | Backward | related-work section of REF-007 (arXiv v1 §2) | — | full section | D | represented by REF-028; others queued below |

### Round 1b (after independent review, 2026-10-20)

These items were **not found by keyword search**. Items 45–49 were suggested by the independent review and then verified by the implementer against Crossref, OpenAlex, Europe PMC, or arXiv. Items 44 and 50 are verification actions.

| # | Source | Action | Result |
|---|---|---|---|
| 44 | Crossref, OpenAlex, arXiv comments | Re-check the publication status of all arXiv-sourced entries (REF-017, 022–029, 039) | REF-029 is published in TMLR (07/2024), so the earlier status was wrong. No published version found for REF-027, REF-039, REF-044. REF-023 is workshop-only. Venues of REF-017 and REF-022 rest on author-stated arXiv comments |
| 45 | Reviewer-suggested; Crossref + OpenAlex abstract | Negoescu, Frazier, Powell (2011), INFORMS J. Comput. | Included as REF-040 (moved up from the Round 2 queue) |
| 46 | Reviewer-suggested; Crossref + OpenAlex abstract | Charusaie & Samadi (2024), NeurIPS 37 | Included as REF-041 |
| 47 | Reviewer-suggested; Crossref + Europe PMC abstract | Stroganov et al. (2020), J. Comput.-Aided Mol. Des. | Included as REF-042 |
| 48 | Reviewer-suggested; Crossref + OpenAlex abstract | Alves et al. (2025), Sci. Data | Included as REF-043 |
| 49 | Reviewer-suggested; arXiv abstract page | Reid, Sühr, Vernade, Samadi (2024), arXiv:2409.20489 | Included as REF-044 (preprint) |
| 50 | Publisher pages (full abstract and article-type check) | Re-screen of three previously excluded journal articles | See §7 |

## 7. Screened and excluded or deferred items

**Re-screening note (Round 1b).** In Round 1, three journal articles were excluded on the basis of partial (truncated) abstracts. They were re-screened in Round 1b using the full abstract on the publisher's page. All three are conceptual frameworks without empirical evaluation. The exclusions stand, but the stage structure of item 1 resembles the proposed escalation/prioritization staging, so it is recorded here for owner awareness.

| # | Item | Identifier | Screening level | Decision | Specific reason |
|---|---|---|---|---|---|
| 1 | Osei, Janssens, Asare, El-Sayed (2024). "Learning the Next Experiment: A Decision Architecture for Closed-Loop Drug Discovery under Cost, Uncertainty, and Scientific Value". *Pharmacophore* 15(5), 100–110 | doi:10.51847/m8ltgdhsie | Full abstract and article-type check on the publisher page | **Excluded** (conceptual framework) | Proposes a staged architecture (admissibility check, multi-dimensional value assessment, constrained portfolio, authorised execution) and an evidence ledger. The page itself states that there is no empirical evaluation or prospective validation and that it is "not a deployment-ready decision tool". Does not address medicinal-chemist review allocation or escalation explicitly. Possible conceptual precedent for staged experiment selection; **not** used as evidence in other documents |
| 2 | Chen, Sato, Harris (2025). "Human-in-the-Loop Computational Phytopharmacology: Expert Curation, Model Oversight, Mechanistic Reasoning, and Translational Decision Confidence". *Int. J. Pharm. Phytopharmacol. Res.* 15(6), 1–10 | doi:10.51847/qfrht9l78x | Full abstract and article-type check | **Excluded** (conceptual framework; out of domain) | States that the framework is conceptual; no algorithm or evaluation; natural-product (phytopharmacology) domain |
| 3 | Nzouankeu, Mwangi, Abega, Dupont (2024). "Designing Molecules under the Full Weight of Potency, Selectivity, Synthesizability, Safety, and Pharmaceutical Developability". *Pharmacophore* 15(5), 37–47 | doi:10.51847/bhejqkbzml | Full abstract and article-type check | **Excluded** (conceptual perspective) | States that the contribution is "conceptual and methodological rather than empirically validated"; no human-review allocation |
| 4 | Shi et al. (2026). "A Survey of Human-AI Collaboration for Scientific Discovery" | doi:10.20944/preprints202601.0405.v2 (preprint; several versions) | Full abstract (Crossref) | **Deferred** (not excluded) | A preprint systematic review across scientific discovery, not chemistry-specific. Peer-review status is not an exclusion criterion, and other preprints are included. Deferred to Round 2 as a possible field pointer |
| 5 | Review articles on AI in drug discovery with no HITL, deferral, or query-allocation content | various | Titles and abstracts | **Excluded** (eligibility §4) | No method or evaluation relevant to review allocation. Not individually listed |

## 8. Saturation assessment

- **Topics A, D, and F (most relevant to N1–N4):** Round 1 reached the major lines of work, and forward tracing from REF-001/REF-002 converged on a small set of HITL drug-discovery papers (REF-007, REF-011, REF-012). Saturation is **not** claimed. The items in §9 remain.
- **Topics B, C, E, G:** representative coverage only. E is deliberately light (Issue #8).
- **Topic H:** evaluation designs were extracted from REF-001, REF-002, REF-007, REF-008, REF-009, REF-010, and REF-043.
- **Round 1b** added five references suggested by the independent review. That these were not found by the Round 1 keyword searches is itself evidence that Round 1 coverage of topics C and D was incomplete.

## 9. Identified but not yet screened (Round 2 queue)

These were seen in reference lists or result pages but not yet verified. **They must not be cited until verified.**

- Human–AI routing and triage work cited in REF-007 §2.2 (e.g., works by De et al. 2021, Wilder et al., Fügener et al. 2022, Gao et al. 2021 on routing under bandit feedback).
- Further optimal-learning and knowledge-gradient follow-ups to REF-040.
- The published journal version of REF-007 (methods and evaluation), the LNCS volume number of REF-011, and proceedings records for REF-017 and REF-022, all blocked to automated access in Round 1b. These may be resolved with owner-supplied PDFs or manual lookup.
- The human–AI collaboration survey deferred in §7 (item 4), and a full-text read of REF-042.
- Cheshire 2011 ("How well do medicinal chemists learn from experience?"), Takaoka et al. 2003, and Sheridan et al. 2014 (crowdsourced molecular complexity), from REF-010's reference list.
- Conformal prediction under covariate/label shift for molecular properties (multiple 2023–2026 preprints) — for Issue #8.
- Decision-focused learning and constrained/cost-aware Bayesian optimization.
- A structured search in ChemRxiv and the bioRxiv/medRxiv preprint servers, which was not performed in Round 1.

## 10. Reproducibility notes

- Queries were issued with a helper script against `api.openalex.org/works?search=…`. The date and query are recorded above.
- OpenAlex rankings and counts change over time, so rerunning a query will not reproduce identical results.
- Full-text extraction for REF-001 and REF-002 used an automated reader answering targeted questions (access level: "Full text (tool-assisted)"). Those details should be spot-checked by a human before publication use.
- Round 1b status checks used OpenAlex location records and arXiv comments. These are indications of venue, not authoritative proceedings records, and the registry states which entries rest on them.
- OpenAlex abstracts can be truncated. Screening decisions should be based on the full abstract from the publisher or Crossref where available.
