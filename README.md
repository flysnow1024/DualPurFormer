# DualPurFormer
**DualPurFormer: A Dual Purification Transformer for sEEG-Based Speech Decoding**

## Release Status
This repository currently provides a method overview, experiment settings, summarized results, and a result aggregation utility. The complete model implementation and training and inference code will be released upon acceptance of the paper.

## Usage
### Setup
* **OS**: Linux
* **CUDA**: 11.8
* **Python**: 3.11.13
* **Pytorch**: 2.4.1
```bash
pip install -r requirements.txt
```
## Available Materials
- [Experiment settings](configs/paper_settings.json): documented settings for the fixed-residual-scale model used in the paper.
- [Results](results/README.md): baseline comparison and hyperparameter sensitivity summaries.
- [Result aggregation utility](summarize_results.py): summarizes existing per-seed result files for each subject.
- [Utility instructions](docs/result_aggregation.md): expected input layout and usage.
- [Environment notes](docs/environment.md): dependency information from the development repository.

## Evaluation Protocol
Experiments are performed independently for each of the 12 participants on the 61-class DU-IN word decoding task. Within each class, trials are split into training, validation, and test sets at an 80:10:10 ratio. Experiments use six random seeds: 42, 0, 1, 2, 3, and 4. Model selection uses validation accuracy.

The dataset is provided by the original DU-IN authors and is not redistributed here. Please obtain it from the original release and follow its access and usage conditions.
