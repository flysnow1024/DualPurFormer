# DualPurFormer
**DualPurFormer: A Dual Purification Transformer for sEEG-Based Speech Decoding**

## Release Status
This repository currently provides a method overview, experiment settings, summarized results and related word analysis. The complete model implementation and training and inference code will be released upon acceptance of the paper.

## Subject-Level Component Ablation Results on DU-IN Dataset

| Configuration | CFP | HP | EMA |
| --- | :---: | :---: | :---: |
| A: Plain backbone | — | — | — |
| B: Backbone + EMA | — | — | ✓ |
| C: CFP + EMA | ✓ | — | ✓ |
| D: HP + EMA | — | ✓ | ✓ |
| E: CFP + HP | ✓ | ✓ | — |
| F: Full DualPurFormer | ✓ | ✓ | ✓

### Test Accuracy (%)

Each subject-level cell reports mean ± population standard deviation across six random seeds. The last row reports the macro-average across subjects ± pooled within-subject seed standard deviation, matching the convention in Table 2.

| Subject | A | B | C | D | E | F |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| sub-001 | 71.09 ± 1.49 | 71.36 ± 1.55 | 76.93 ± 1.77 | 73.18 ± 2.24 | 77.50 ± 1.19 | 79.01 ± 1.01 |
| sub-002 | 43.70 ± 2.49 | 43.34 ± 2.14 | 49.09 ± 1.44 | 47.17 ± 1.07 | 48.81 ± 1.39 | 50.28 ± 0.88 |
| sub-003 | 29.48 ± 2.36 | 30.27 ± 3.30 | 32.36 ± 2.05 | 30.64 ± 2.33 | 31.99 ± 1.97 | 33.89 ± 2.60 |
| sub-004 | 62.79 ± 1.50 | 62.29 ± 2.52 | 69.89 ± 1.92 | 65.85 ± 2.09 | 69.94 ± 1.25 | 69.51 ± 1.53 |
| sub-005 | 70.16 ± 3.13 | 71.04 ± 1.69 | 78.03 ± 1.65 | 73.66 ± 2.54 | 76.67 ± 0.44 | 78.41 ± 1.48 |
| sub-006 | 36.68 ± 2.19 | 37.63 ± 3.41 | 42.65 ± 2.14 | 38.78 ± 1.94 | 39.40 ± 1.33 | 42.89 ± 2.15 |
| sub-007 | 40.31 ± 3.17 | 41.28 ± 3.26 | 46.33 ± 1.86 | 44.12 ± 3.62 | 45.91 ± 3.02 | 47.24 ± 4.10 |
| sub-008 | 49.50 ± 1.13 | 49.86 ± 1.52 | 57.06 ± 2.69 | 51.46 ± 2.66 | 57.43 ± 2.68 | 56.51 ± 1.43 |
| sub-009 | 57.99 ± 1.40 | 59.01 ± 2.12 | 64.34 ± 2.53 | 60.40 ± 2.50 | 64.49 ± 2.47 | 65.97 ± 3.53 |
| sub-010 | 28.54 ± 3.02 | 27.49 ± 2.02 | 31.58 ± 2.09 | 30.07 ± 2.16 | 30.90 ± 1.97 | 33.15 ± 1.64 |
| sub-011 | 70.67 ± 2.37 | 70.16 ± 1.28 | 75.68 ± 2.78 | 71.23 ± 2.49 | 76.04 ± 2.04 | 76.75 ± 2.40 |
| sub-012 | 53.01 ± 3.34 | 53.55 ± 3.50 | 63.85 ± 2.13 | 55.65 ± 2.59 | 63.93 ± 1.70 | 64.48 ± 1.54 |
| **Overall** | **51.16 ± 2.42** | **51.44 ± 2.49** | **57.32 ± 2.12** | **53.52 ± 2.42** | **56.92 ± 1.92** | **58.17 ± 2.23

## Usage
### Environment Setup
* **OS**: Linux
* **CUDA**: 11.8
* **Python**: 3.11.13
* **Pytorch**: 2.4.1
```bash
pip install -r requirements.txt
```

### Dataset
We use the Chinese word reading sEEG dataset released by DU-IN. Please visit the [official DU-IN repository](https://github.com/liulab-repository/Du-IN) for dataset access instructions and follow the original authors' usage requirements.

### Evaluation Protocol
Experiments are performed independently for each of the 12 participants on the 61-class DU-IN word decoding task. Within each class, trials are split into training, validation, and test sets at an 80:10:10 ratio. Experiments use six random seeds: 42, 0, 1, 2, 3, and 4. Model selection uses validation accuracy.
