# DualPurFormer
**DualPurFormer: A Dual Purification Transformer for sEEG-Based Speech Decoding**

## Release Status
This repository currently provides a method overview, experiment settings, summarized results and related word analysis. The complete model implementation and training and inference code will be released upon acceptance of the paper.

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
