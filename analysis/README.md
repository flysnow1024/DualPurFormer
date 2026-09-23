# DualPurFormer

**DualPurFormer: A Dual Purification Transformer for sEEG-Based Speech Decoding**

## Overview

DualPurFormer decodes spoken words from stereo-electroencephalography (sEEG) signals by refining neural representations along the feature and network depth dimensions.

- **Classwise Feature Purification (CFP)** uses learnable class prototypes to select word-discriminative feature dimensions during training, without additional inference cost.
- **Hierarchical Purification (HP)** aggregates log energy descriptors from intermediate Transformer blocks and refines the main prediction through controlled residual integration.

On the DU-IN Chinese word reading sEEG dataset, DualPurFormer achieves a mean accuracy of **58.17%** across 12 participants, outperforming MDM-Tent by **10.41 percentage points**.

## Release Status

This repository currently provides a method overview, experiment settings, supplementary subject-level component ablation results, and a result aggregation utility. The complete model implementation and training and inference code will be released upon acceptance of the paper.

**This partial release does not yet support model training or inference.**

## Available Materials

- [Experiment settings](configs/paper_settings.json): documented settings for the fixed-residual-scale model used in the paper.
- [Supplementary results](results/README.md): per-subject component ablation results for the six configurations in Table 2, including six-seed means and standard deviations.
- [Result aggregation utility](summarize_results.py): summarizes existing per-seed result files for each subject.
- [Utility instructions](docs/result_aggregation.md): expected input layout and usage.
- [Environment notes](docs/environment.md): dependency information from the development repository.

The configuration is provided for documentation; it is not a runnable training configuration in this partial release. Neural recordings, trained weights, and private server paths are not included.

## Evaluation Protocol

Experiments are performed independently for each of the 12 participants on the 61-class DU-IN word decoding task. Within each class, trials are split into training, validation, and test sets at an 80:10:10 ratio. Experiments use six random seeds: 42, 0, 1, 2, 3, and 4. Model selection uses validation accuracy.

The dataset is provided by the original DU-IN authors and is not redistributed here. Please obtain it from the original release and follow its access and usage conditions.

## Acknowledgments

This work builds on the DU-IN dataset and tokenizer and the multi-scale temporal modeling approach of MDM-Tent. Full implementation attribution and third-party license notices will accompany the complete code release.
