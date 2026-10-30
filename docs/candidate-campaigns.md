# Candidate Experimental Campaigns

## Status

**PROPOSED / OPEN — documentation-level comparison only.** This document does not accept a target, dataset, endpoint, split, or evaluation design. It was prepared under Issue #3 (`Refs #3`) and records the dataset-first rationale proposed in DR-008.

The comparison is **incomplete for final target acceptance**: several Issue #3 criteria remain `[UNV]` (section 4).

Dataset cards, README files, blog posts, and published row-count metadata were read. No data file was downloaded, no molecular record was analysed, and no model was run (AGENTS.md §4). Access dates fall between 2026-10-25 and 2026-10-30; per-item dates were not recorded, so re-check every source before use. No local data files exist, so no filenames or checksums are recorded (AGENTS.md §6).

Claims that depend on journal publications (the ASAP organizer paper and the Papyrus paper) are **not** made here, because those papers are not in the reference registry (`docs/references.md`). They appear only as identifier pointers.

## Evidence labels

- **[DOC]** — stated in a source page that was read (section 8). Not audited against the underlying records.
- **[REV]** — reported in an independent Codex review and not independently verified.
- **[UNV]** — unknown or not verified.
- **[INF]** — assessment or inference. It is not a finding in any source.

## 1. Purpose

Issue #3 asks for candidate targets to be compared on public-data availability, SAR richness, assay quality, structural evidence, ADMET relevance, publication saturation, licensing, and computational feasibility.

This document compares **experimental campaigns** rather than targets in the abstract (DR-008). A target can have many public records and still lack a coherent assay, a reconstructable decision-time order, or a defensible evaluation. The target is chosen after the campaign comparison, and the owner must still accept it (Issue #3 acceptance criterion).

## 2. Comparison criteria

From Issue #3: public-data availability, SAR richness, assay quality, structural evidence, ADMET relevance, publication saturation, licensing, computational feasibility.

**Proposed additions (PROPOSED):**

- decision-time chronology and what could have been known when;
- label and molecular-identity quality (stereochemistry, duplicates, revisions);
- availability of external evidence for candidates;
- public exposure and potential duplication through later deposits;
- biological system and fit to the chemistry scope;
- effective sample size after exclusions (unaudited).

## 3. Candidate records

### 3.1 COVID Moonshot

- **Sources:** `postera-ai/COVID_moonshot_submissions` and `asapdiscovery/COVID_moonshot_data_clean` (README files).
- **[DOC]** The original repository holds design submissions and initial experimental data. Its master file has status and date columns `ORDERED`, `ORDER_DATE`, `MAKER`, `MADE`, `SHIPMENT_DATE`, and `ASSAYED`. No assay dates and no compound or measurement counts are stated.
- **[DOC]** Two assay formats appear in the original columns: RapidFire (`r_*`) and fluorescence (`f_*`). It also has a trypsin counter-assay (`trypsin_IC50`), relative solubility by nephelometry at two concentrations, an STD-NMR ratio, a `series` column, and contributor `rationale` text.
- **[DOC]** Identity: the registration SMILES "may not correspond to the actual SMILES of the compound". A separate `suspected_SMILES` column exists. Many enantiopure compounds came from chiral separation with unknown absolute stereochemistry.
- **[DOC]** The curated repository reports IC50 values from the fluorescence assay, with `IC50_(µM)`, 95% confidence bounds, Hill slope, curve class, and a `Semiquant` field (Strong, Weak, or Quant). Two files are listed: all noncovalent data and an achiral-plus-enantiopure subset.
- **[DOC]** The curated README states "as of October 10, 2023", while the filenames carry `2023_10_18`. The filenames contain the word "dates", but the README's column list shows no date column. **[UNV]** whether the files hold date columns.
- **[DOC]** Licence: data CC0-1.0; software and documentation MIT (original repository). **[UNV]** the curated repository's licence.
- **[DOC]** The original repository describes itself as "still under active curation".
- **[INF]** `ORDER_DATE` could serve as a proxy for the "which designs to order" decision but is not an assay date. Any lag rule from `SHIPMENT_DATE` is an assumption.
- **[UNV]** The sources show outcome data only for compounds that were made and assayed. The selection mechanism that determined which designs were ordered is not documented in the pages read.

### 3.2 ASAP–Polaris–OpenADMET

- **Sources:** Polaris potency and ADMET dataset cards; Zenodo record 15582067.
- **[DOC]** Potency card: 1,328 datapoints (unique-molecule count not stated); pIC50 for SARS-CoV-2 and MERS-CoV main protease; columns Molecule Name, CXSMILES, the two pIC50 columns, and `Set` (train or test). The card documents no date, series, or qualifier columns. The split method is not stated on the card. The data are sparse.
- **[DOC]** Enantiomers share one structure string and were treated as duplicates within the challenge. Five enantiomer cases were filtered from the test set (indices listed on the card).
- **[DOC]** ADMET card: 560 datapoints across five endpoints (MLM, HLM, KSOL, LogD, MDR1-MDCKII). The card documents no date or qualifier columns. The clearance lower reporting bound changed ("could not confidently quote Clint values for measurements < 10"), earlier calculations were not updated, and some test values were removed.
- **[DOC]** Zenodo record: `Potency.csv`, `ADMET.csv`, and `structures.tar.gz` (727.7 MB, **not downloaded**). Potency assays by the Weizmann Institute, ADMET by Bienta, crystallography by Oxford and Diamond Light Source; protocols are linked on protocols.io. Published 2025-06-03.
- **[DOC]** Licence labels disagree: Polaris cards CC0-1.0; Zenodo record CC BY 4.0; OpenADMET dataset catalogue "MIT".
- **[UNV]** How the challenge split was constructed. It is not documented on the cards or the Zenodo record. The challenge's organizer paper (doi: https://doi.org/10.1021/acs.jcim.5c02106) is not registered or relied on here.
- **[INF]** The cards document no date columns and the released files were not inspected, so recovery of decision-time information from them cannot be assumed.

### 3.3 OpenADMET–ExpansionRx

- **Sources:** the OpenADMET challenge-ended post; the Hugging Face dataset README and published row-count metadata.
- **[DOC]** "Over 7000 molecules" (post). The design is a time split: predict late-stage molecules from earlier-stage data of the same campaigns. The test set was divided into a validation half (live leaderboard) and a hidden half. The README describes "a recently prosecuted series of drug discovery campaigns" by Expansion Therapeutics on RNA-mediated diseases, contributed in kind. Labels were released on Hugging Face.
- **[DOC]** README endpoints: LogD; kinetic solubility (µM); mouse and human liver microsomal CLint (mL/min/kg); Caco-2 efflux ratio; Caco-2 Papp A to B; mouse plasma, brain, and gastrocnemius-muscle protein binding (% unbound). The raw version adds a rat liver microsomal CLint endpoint that was not part of the challenge and keeps out-of-range modifiers; the default "ML-ready" version keeps in-range measurements only.
- **[DOC]** Published metadata: default configuration 5,326 train and 2,282 test rows (7,608 in total); raw configuration 7,618 rows. These are row counts, not unique molecules (**[UNV]**).
- **[DOC]** Licence: CC BY 4.0 on the README. The OpenADMET catalogue lists CC BY 4.0 for the full release, no label for the training and blinded-test entries, and CC0-1.0 for the teaser entry.
- **[INF]** No potency endpoint, and external evidence for proprietary-programme compounds is probably sparse.

### 3.4 OpenADMET PXR induction

- **Sources:** the Hugging Face dataset card; the OpenADMET "liftoff" post; the semi-pure SAR report; the structure-track post; the OpenADMET policy post.
- **[DOC]** Configuration sizes on the card: default 4.65k rows (train 4.14k, test 513); `counter_assay` 2.86k; `crudes_htchem` 456; `phase_1_unblinded` 253; `phase_2_unblinded` 260; `semi_pure_htchem` 96; `single_concentration` 21k; `structure` 184. Columns include pEC50 and Emax estimates with standard errors and confidence intervals, plus `OCNT Batch`, `OCNT_ID`, and `source`. No date columns. Licence CC BY 4.0 on the card and Apache 2.0 in the OpenADMET catalogue.
- **[DOC]** The test set was built around 63 hit compounds (EC50 of 1 µM or lower) with at least 10 commercially available, chemically similar compounds each, run with full dose-response. After repeat measurements the final dataset lists 46 highly potent compounds. Phase 1 ran April 1 to May 25 and Phase 2 May 26 to July 1. The counter-assay was not scored but is recommended for use. The post does not state the purity of the test compounds.
- **[DOC]** The 96-compound semi-pure plate was only partly purified and assayed as made, so the amount in each well is uncertain. Ten structures were revised from registration, and twelve compounds recovered under 20% of theory. The authors advise re-testing low-recovery compounds on purified material. **[UNV]** whether this applies to the 513 test compounds.
- **[DOC]** The organizers describe the 184 X-ray structures as the largest publicly available PXR complex dataset to date.
- **[DOC]** OpenADMET's policy commits to depositing datasets in public repositories such as ChEMBL and the PDB.
- **[UNV]** The timing of counter-assay data relative to the primary assay for the test compounds.
- **[INF]** PXR induction is described by the organizers as a liability in drug discovery. Using it would change the chemistry scope, which is an Issue #4 question and is not decided here.

### 3.5 OpenADMET CYP inhibition

- **Sources:** the Hugging Face dataset README; the OpenADMET midpoint post.
- **[DOC]** The challenge closes on 2026-11-03 at 23:59 UTC.
- **[DOC]** README: direct-inhibition training set of 4,905 compounds (pIC50 with confidence interval and standard deviation for CYP1A2, CYP2C9, CYP2D6, CYP3A4) and a 750-compound blinded test set; a time-dependent-inhibition (TDI) training set of 6,145 compounds; a single-concentration set of 17,504 measurements. Licence Apache 2.0.
- **[UNV]** Emax training set size: the published metadata reports 6,145 rows, while the current README states 6,146 compounds. The discrepancy is unresolved.
- **[DOC]** The README records that finalised ground truth refreshed the direct-inhibition and TDI data on 2026-08-06, so the revision used must be pinned.
- **[DOC]** The structure track has 20 test compounds with SMILES only. The midpoint post describes new CYP3A4 cryo-EM structures. The README states that the ground-truth complex structures used for scoring are not disclosed yet.
- **[INF]** Final labels and documentation may not be stable until after closure.

### 3.6 Evidence and supporting resources

- **ChEMBL:** **[DOC]** distributed under CC BY-SA 3.0 Unported (ChEMBL documentation).
- **BindingDB:** **[DOC]** the information page states CC BY 3.0 for staff-curated data and CC BY-SA 3.0 for data imported from ChEMBL, and gives no licence for its other sources. **[REV]** a published update reports CC BY 4.0 for the curated data; not verified.
- **PubChem:** rights are depositor-specific. **[UNV]**.
- **Public exposure:** **[DOC]** OpenADMET commits to public deposits of campaign data. **[INF]** Later database records may therefore reproduce a campaign's own labels. Actual overlap is **[UNV]**.
- **MoleculeACE:** **[DOC]** README: 30 bioactivity datasets, one per target, as a tool for evaluating models on activity-cliff compounds; repository licence MIT. It is a benchmark, not a coherent experimental campaign.
- **Papyrus:** **[UNV]** stereochemistry handling, duplicate handling, and licence must be checked against its publication (doi: https://doi.org/10.1186/s13321-022-00672-x), which is not registered here. See Round 2.

## 4. Comparison summary

| Criterion | Moonshot | ASAP | ExpansionRx | PXR | CYP |
|---|---|---|---|---|---|
| Endpoint | IC50, two assay formats (fluorescence in the curated set) [DOC] | pIC50 (two Mpro targets) plus five ADMET [DOC] | Nine ADMET endpoints [DOC] | pEC50 and Emax [DOC] | Direct-inhibition pIC50 (four isoforms) and TDI [DOC] |
| Documented size | Not stated [UNV] | 1,328 / 560 datapoints [DOC] | Over 7,000 molecules; 7,608 default rows [DOC] | 4.14k train, 513 test [DOC] | 4,905 + 750 direct; 6,145 TDI train [DOC] |
| Chronology information | Order and shipment fields documented; no assay-date field documented in the README [DOC]; file contents not inspected | No date columns documented on cards; files not inspected [DOC] | Designed time split; per-compound dates [UNV] | Phase dates only; no date columns on card [DOC] | [UNV] |
| Documented assay provenance and consistency | Two formats [DOC] | Potency from one lab, ADMET from another [DOC] | Multiple campaigns from one sponsor; cross-campaign consistency [UNV] | In-house reporter assay (semi-pure report) [DOC] | [UNV] |
| Identity and stereochemistry | Unknown absolute stereochemistry for many [DOC] | Enantiomer duplicates [DOC] | [UNV] | Structure revisions in the semi-pure plate [DOC] | [UNV] |
| Censoring, qualifiers, uncertainty reporting | `Semiquant` field (curated) [DOC] | No qualifier columns on cards; clearance bound change [DOC] | Out-of-range modifiers in raw version [DOC] | Censoring not documented [UNV]; standard errors and confidence intervals reported [DOC] | Confidence intervals and standard deviations reported [DOC]; censoring [UNV] |
| Structural evidence | Structures folder [DOC] | Crystallography in Zenodo record, not downloaded [DOC] | None documented | 184 X-ray structures [DOC] | 20 structure-track compounds; ground truth not yet disclosed [DOC] |
| SAR richness and series organisation | `series` column [DOC] | [UNV] | [UNV] | Analogue expansion around 63 hits [DOC] | [UNV] |
| Publication saturation | Mpro heavily studied; not assessed [INF] | Mpro heavily studied; not assessed [INF] | [UNV] | [UNV] | [UNV] |
| External evidence for candidates | Public Mpro literature likely rich [INF] | Public Mpro literature likely rich [INF] | Probably sparse [INF] | Probably sparse for novel analogues [INF] | [UNV] |
| Public exposure and potential duplication | CC0 public data [DOC]; duplication [UNV] | CC0 and CC BY public data [DOC]; duplication [UNV] | Deposit commitment [DOC]; duplication [UNV] | Deposit commitment [DOC]; duplication [UNV] | [UNV] |
| Computational feasibility | [UNV] | [UNV] | [UNV] | [UNV] | [UNV] |
| Biological system and scope fit | SARS-CoV-2 main protease inhibitors [DOC] | SARS-CoV-2 and MERS-CoV main proteases [DOC] | ADMET properties; no target endpoint [DOC] | Induction liability (anti-target) [INF] | Inhibition of drug-metabolising enzymes [DOC] |
| Licence | CC0 data; MIT software [DOC] | Three conflicting labels [DOC] | CC BY 4.0; some entries unlabelled [DOC] | CC BY 4.0 vs Apache 2.0 [DOC] | Apache 2.0 [DOC] |

No model, compute, or benchmark assessment has been made, so computational feasibility is unassessed for every candidate. Several Issue #3 criteria are `[UNV]`, so this comparison is incomplete for target acceptance.

## 5. Current PROPOSED ordering (not a decision)

1. **Joint primary candidates, audit pending:** Moonshot and ASAP–Polaris–OpenADMET, assessed under identical gates. Their documented asymmetry: Moonshot documents order and shipment dates and a series column; ASAP documents no dates, but its potency and ADMET come from one programme (overlap between the two is `[UNV]`). No source establishes a universal winner.
2. **Secondary candidate:** OpenADMET–ExpansionRx, trained separately. What it would replicate is OPEN; the proposal is limited to the error-prioritization component.
3. **Conditional or later:** PXR, only if an anti-target scope is accepted (Issue #4); CYP, only after its challenge closes and its labels and documentation are verified.

**Conditions:** no accepted target or dataset; no pooling of datasets into one training table; a separate model per dataset; chronology reconstructed from order, shipment, or release dates is an assumed-availability analysis unless dated provenance is verified. Record-level checks follow the sequence in DR-008 and require explicit owner approval and pre-set gates (Issue #6).

## 6. Open verification items

1. **Moonshot:** the number of compounds with each assay's IC50; whether the curated files contain date columns; coverage of order and shipment dates; the size of the stereochemistry-resolved subset; the curated repository's licence.
2. **ASAP:** unique-molecule counts; the paired potency–ADMET overlap; the split method; resolution of the three licence labels.
3. **Overlap:** whether Moonshot and ASAP share compounds or measurements.
4. **ExpansionRx:** unique-molecule and per-endpoint counts; per-compound dates; the licence of every artifact.
5. **PXR:** the purity status of the 513 test compounds; whether `source` or `OCNT Batch` orders analogues after the training compounds; the timing of counter-assay data for test compounds.
6. **CYP:** final labels and documentation after 2026-11-03; the revision to pin.
7. **PubChem and Papyrus:** rights and handling, once their publications are registered.
8. **All:** exact artifact revisions and checksums, if and when downloads are approved.

Gate thresholds belong to Issue #6 and are not set here.

## 7. Not decided and out of scope

- The target, dataset, endpoint, and anti-target scope question (Issues #3, #4).
- The reviewer action and the independent outcome that would show review helped (Issues #5, #9, #10).
- Evidence-tier definitions, the ranking objective, leakage controls, splits, and the identity policy (Issues #6, #8 to #10).
- Model families and features (Issue #7).
- Publication-derived claims (the ASAP organizer paper, the Papyrus paper, and literature on lead-optimization benchmarks and assay-origin effects) are **deliberately excluded** until they are registered. That needs a Round 2 literature issue, which does not yet exist.

## 8. Sources read

- Moonshot: https://github.com/postera-ai/COVID_moonshot_submissions and https://github.com/asapdiscovery/COVID_moonshot_data_clean
- ASAP potency card: https://polarishub.io/datasets/asap-discovery/antiviral-potency-2025-unblinded
- ASAP ADMET card: https://polarishub.io/datasets/asap-discovery/antiviral-admet-2025-unblinded
- ASAP Zenodo record: https://zenodo.org/records/15582067
- ExpansionRx post: https://openadmet.ghost.io/the-openadmet-expansionrx-blind-challenge-has-come-to-an-end/
- ExpansionRx README: https://huggingface.co/datasets/openadmet/openadmet-expansionrx-challenge-data/raw/main/README.md
- ExpansionRx row-count metadata: https://datasets-server.huggingface.co/info?dataset=openadmet%2Fopenadmet-expansionrx-challenge-data
- PXR dataset: https://huggingface.co/datasets/openadmet/pxr-challenge-train-test
- PXR posts: https://openadmet.ghost.io/predicting-pxr-induction-we-have-liftoff/, https://patwalters.github.io/viewers/pxr_sar_report.html, and https://openadmet.ghost.io/fantastic-poses-and-can-we-even-find-them-what-we-learned-about-pxr-structure-prediction-in-our-recent-challenge/ (structure track)
- CYP README: https://huggingface.co/datasets/openadmet/cyp-challenge-train-test/raw/main/README.md
- CYP row-count metadata: https://datasets-server.huggingface.co/info?dataset=openadmet%2Fcyp-challenge-train-test
- CYP midpoint post: https://openadmet.ghost.io/halfway-through-the-openadmet-cyp-challenge/
- OpenADMET policy: https://openadmet.ghost.io/practicing-what-we-preach-why-open-science-needs-clear-rules/
- OpenADMET catalogue: https://www.openadmet.org/datasetsmodels/
- ChEMBL documentation: https://chembl.gitbook.io/chembl-interface-documentation/about
- BindingDB information page: https://www.bindingdb.org/rwd/bind/info.jsp
- MoleculeACE README: https://github.com/molML/MoleculeACE/blob/main/README.md
