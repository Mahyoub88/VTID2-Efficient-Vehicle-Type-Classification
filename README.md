# Efficient Neural Network Architectures for Vehicle Type Classification in Intelligent Transportation Systems

### A Content-Audited, Leakage-Aware, and Efficiency-Focused Study Using VTID2

This repository contains an MSc Artificial Intelligence portfolio project investigating neural network architectures for vehicle type classification using the **Vehicle Type Image Dataset Version 2 (VTID2)**.

The study focuses on **data-quality auditing, leakage-aware evaluation, neural-network efficiency, and explainability** rather than accuracy alone.

## Project Overview

The workflow includes:

- Dataset discovery, integrity checks, and class analysis
- Exact-duplicate and near-duplicate auditing
- Leakage-controlled group splitting
- Neutral letterbox preprocessing
- Training-only normalisation statistics
- Training augmentation
- MLP baseline
- Standard CNN
- Efficient CNN
- Efficient CNN with Squeeze-and-Excitation (SE)
- Multi-seed training and held-out test evaluation
- Paired bootstrap uncertainty analysis
- Computational-efficiency benchmarking
- Ablation study
- Grad-CAM explainability and padding-attention analysis
- Ethics, responsible AI, and reflection

## Research Questions

The project examines:

1. Whether a convolutional architecture performs better than an MLP baseline for VTID2 vehicle classification.
2. How a conventional image-level evaluation compares with a leakage-controlled protocol.
3. Whether an efficient CNN can substantially reduce computational cost while retaining predictive performance.
4. Whether Squeeze-and-Excitation improves the efficient CNN.
5. Whether model attention is disproportionately directed toward letterbox padding.

## Main Findings

- The **Standard CNN** outperformed the MLP baseline, although unequal model capacity means the difference cannot be attributed to spatial inductive bias alone.
- The conventional image-level protocol produced higher scores, but it was treated as a **non-equivalent diagnostic contrast**, not as a direct leakage estimate.
- The **Efficient CNN** reduced trainable parameters by **87.24%** and MACs by **81.67%** relative to the Standard CNN, with a small reduction in mean Macro-F1.
- In the executed benchmark, the Efficient CNN reduced batch-one latency by **8.49% on CPU** and **18.32% on GPU**.
- Adding **Squeeze-and-Excitation (SE)** did not improve mean test performance and increased measured latency.
- Grad-CAM analysis indicated that padding attention remained below the geometric null; however, padding geometry itself carries information about aspect ratio and therefore is not a fully neutral artefact.

## Repository Contents

```text
.
├── VTID2_Efficient_Vehicle_Type_Classification.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

## Environment Used

The submitted notebook was executed using:

- Python 3.10.11
- PyTorch 1.12.1 + CUDA 11.3
- NVIDIA Quadro M3000M
- Reproducibility seed: 42

## Installation

Create a Python environment and install the main dependencies:

```bash
pip install -r requirements.txt
```

> PyTorch installation is hardware- and CUDA-dependent. If reproducing the original GPU environment, install a PyTorch build compatible with the available CUDA toolkit.

## Dataset

The project uses **VTID2 (Vehicle Type Image Dataset Version 2)**.  
The dataset itself is **not included in this repository**. Users should obtain it from its original source and configure the notebook dataset path locally.

## Running the Notebook

1. Obtain VTID2.
2. Open `VTID2_Efficient_Vehicle_Type_Classification.ipynb`.
3. Update the dataset path and output path for your local environment.
4. Run the notebook cells sequentially.

## Academic Context

- **Programme:** MSc Artificial Intelligence
- **Module:** UFCEYQ-15-M — Artificial Neural Networks
- **Assessment:** Individual Portfolio
- **Framework:** PyTorch

## Notes on Reproducibility

The notebook uses fixed random seeds and a leakage-controlled grouping strategy. Results can still vary slightly across hardware, library versions, and GPU execution environments.

## Author

**Mohammed Mahyoub**  
MSc Artificial Intelligence

## License

This repository is shared for educational and portfolio purposes. The VTID2 dataset remains subject to the terms of its original provider.
