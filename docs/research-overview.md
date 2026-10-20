# Research Overview

## Status

**Research foundation — pre-protocol.**

## Working title

**Chemistry-Aware Human-in-the-Loop Agentic AI for Review-Budget-Constrained Multi-Objective Lead Optimization**

## Core problem

AI-assisted molecular design can generate and score many candidate molecules, but predictive models can be overconfident outside their reliable chemical domain and drug-discovery decisions are inherently multi-objective. Human medicinal-chemistry expertise is valuable but limited.

The project therefore studies a decision problem:

> Under a constrained medicinal-chemist review budget, which molecular candidates should be escalated for expert review, and in what order, so that expert intervention produces the greatest improvement in scientifically meaningful lead-optimization decisions?

## Scientific core

The intended chemistry depth includes, where supported by the selected target and data:

- molecular structure and functional-group context;
- physicochemical properties;
- Structure-Activity Relationship (SAR) and analogue reasoning;
- potency/selectivity evidence;
- ADMET trade-offs;
- structural liabilities and reactivity/stability concerns;
- synthetic accessibility/feasibility;
- scaffold novelty;
- applicability domain and chemical-space coverage;
- protein-ligand evidence for a structure-enabled target.

## AI/ML layers

The current **PROPOSED** system decomposition is:

1. chemistry/property prediction models;
2. uncertainty and applicability-domain estimation;
3. chemistry-aware expert-escalation and review-prioritization policy;
4. LLM-based agent orchestration and RAG-based evidence support;
5. structured human feedback.

The LLM is not assumed to be the primary chemistry predictor.

## Research-first boundary

The project must be publishable as research independently of any final software product. A later application may operationalize the validated methodology, but application engineering is a translation step rather than the current research contribution.

## Open decisions

- therapeutic area and protein target;
- lead discovery versus lead optimization boundary;
- datasets and endpoint definitions;
- molecular/protein representations;
- predictive model families;
- uncertainty methods;
- expert-review utility formulation;
- human-feedback protocol;
- final baselines, metrics, and statistical analysis;
- test-set sealing strategy.
