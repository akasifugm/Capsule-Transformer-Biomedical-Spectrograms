# Capsule–Transformer Biomedical Spectrograms — Research Code Archive

This repository is a **curated, privacy-screened source-code and experiment-summary archive** associated with the manuscript *A Capsule–Transformer Framework for Subject-Wise Classification and Reliability Analysis of Biomedical Percussion and Palpation Spectrograms*.

## Scope and limitations

- The five notebooks in `notebooks/` preserve historical **code cells only**; outputs and execution histories have been removed. Local machine paths and subject labels were redacted. They are **not turnkey, independently verified reproduction scripts**. Some cells contain exploratory or superseded split definitions. Do not execute all cells sequentially and assume the resulting metrics match the paper.
- `configs/` contains the saved experiment configuration records (with machine-specific path fields removed) and a **pseudonymized** subject-partition listing. The anonymized IDs cannot be mapped back to original filenames from this repository alone. All four models used identical saved subject partitions (26/6/6 subjects).
- `results/` contains saved aggregate test metrics and training histories; it does not include per-image predictions or participant-derived images.
- Training budgets, learning rates, and early stopping differed between models. This archive does **not** establish equal hyperparameter-search budgets.
- The image integrity notebook was an exploratory, post hoc diagnostic. Its repeated 20 subject-wise splits are **not** repeated deep-model training runs.

## Dataset

The original dataset comprises 18,240 PNG spectrograms (9,120 percussion and 9,120 palpation), 38 subjects, 480 images per subject. **The dataset is not redistributed here.** Researchers must obtain appropriate authorization and data access independently. Do not upload subject-labeled manifests, spectrogram images, or raw participant data.

## Reproducibility status

These are source-code records and saved configurations, not a guaranteed one-command replication package. The original notebooks include local environment assumptions and exploratory cells. To reproduce the study, one must obtain the permitted dataset, resolve paths and dependencies, reconstruct the saved split against locally authorized subject identifiers, and select the correct training and evaluation cells. A complete independently tested pipeline and a pinned dependency lockfile are **not provided**.

## Saved experiment settings

| Model | Initial LR | Max epochs | Saved history epochs |
|---|---:|---:|---:|
| CNN baseline | 0.0001 | 25 | 25 |
| Transformer-only | 0.001 | 25 | 25 |
| Capsule-only | 0.001 | 20 | 8 |
| Capsule–Transformer | 0.001 (verified in notebook) | 20 (verified in notebook) | 16 |

All four used 224 × 224 input images, batch size 32, and recorded seed 42. For additional architecture-specific settings, see the saved configurations and notebook source.

## Data integrity caveat

Post hoc SHA-256 and pixel hashing identified 48 exact duplicate pairs within one validation subject (palpation class), none spanning subjects or classes. Perceptual-hash screening identified additional candidate similarities, not confirmed duplicates. A 20-repeat subject-wise logistic-regression diagnostic using three global image statistics achieved mean accuracy 0.6722 (SD 0.0594) and mean ROC-AUC 0.7297 (SD 0.0751). These results do not rule out acquisition or rendering artifacts.

## Publication and reuse

No software license has been granted yet. Before making this repository public, the author should confirm code ownership, coauthor/institutional approval where required, and review each file for sensitive information. This archive contains no original biomedical image dataset or model checkpoint files.
