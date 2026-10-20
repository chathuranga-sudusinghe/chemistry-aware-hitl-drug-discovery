# Compute Strategy

## Status

**ACCEPTED high-level strategy; exact workloads remain approval-gated.**

## Local-first development

The owner's current workstation provides:

- Intel Core Ultra 9 275HX CPU;
- approximately 64 GB system memory;
- NVIDIA GeForce RTX 5060 Laptop GPU;
- 8 GB dedicated GPU VRAM;
- NVMe storage.

The local machine is the default environment for research development, data engineering after approval, classical baselines, moderate 2D graph models, uncertainty-method development, agent/RAG development, tests, and local application engineering.

## Cloud-burst principle

AWS may be used when an approved experiment is impractical locally, for example:

- larger 3D/equivariant graph models;
- protein-ligand models exceeding local VRAM;
- large deep ensembles;
- parallel repeated-seed experiments;
- extensive approved hyperparameter searches;
- future model serving or product deployment.

## Reproducibility

Local and cloud runs should use the same configuration and experiment interface where practical. Evidence-producing runs should record:

- Git commit SHA;
- dataset/version/split identity;
- configuration;
- seeds;
- package/Python versions;
- CPU/GPU environment;
- runtime;
- output/artifact locations.

## Cost and authorization

AWS/GPU execution is never implied by an experiment plan. Before cloud execution, the owner must approve the instance/workload, expected runtime, storage/network impact, and cost-sensitive implications.

Do not leave cloud resources running after an approved workload completes.
