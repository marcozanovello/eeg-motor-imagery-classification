# EEG Motor Imagery Classification for Brain-Computer Interfaces

> Comparison of EEGNet and a custom Multiscale Inception CNN on the Kaya 2018 dataset for 3-class motor imagery classification.

---

## Overview

This project implements and compares two deep learning architectures for EEG-based motor imagery classification, a core task in non-invasive Brain-Computer Interfaces (BCI). The goal is to decode imagined hand movements from EEG signals to enable direct brain-to-computer communication.

**Authors:**  Tommaso Bianciardi - Marco Zanovello
**Course:** Machine Learning for Healthcare Devices — University of Padova, MSc ICT
**Year:** 2024/2025

---

## Task

3-class classification of motor imagery EEG signals:
- Left Hand
- Right Hand
- Passive Rest

---

## Dataset

**Kaya 2018** — A large-scale EEG dataset for motor imagery BCI research.

- Files used: CLA and HaLT paradigms
- Subjects: 13 total → 9 train / 2 validation / 2 test (split at subject level)
- Preprocessing: 8–30 Hz bandpass filter + 50 Hz notch filter

---

## Architectures

### EEGNet
Compact convolutional architecture designed specifically for EEG signals. Uses depthwise and separable convolutions to capture temporal and spatial features with very few parameters.

### Multiscale Inception CNN (custom)
Lightweight Inception-style architecture with parallel convolution branches at different temporal scales, adapted for EEG motor imagery classification.

---

## Results

| Model | Accuracy | Cohen's κ |
|---|---|---|
| EEGNet | ~69% | ~0.54 |
| Multiscale Inception CNN | ~69% | ~0.54 |

Results averaged over 5 random seeds. The gap between architectures is smaller than run-to-run variability — the two models are **statistically equivalent** on this task and dataset.

---

## Repository Structure

```
├── notebook.ipynb       # Full pipeline: preprocessing, training, evaluation
├── report.pdf           # Full project report (IEEEtran format)
└── README.md
```

---

## How to Run

The notebook was developed on **Kaggle** (GPU T4 x2 recommended).

1. Download `notebook.ipynb` from this repo
2. Upload it to Kaggle (or run locally with the dependencies below)
3. Add the Kaya 2018 dataset to the environment
4. Run all cells

**Dependencies:** Python 3.10+, TensorFlow 2.x, MNE, NumPy, scikit-learn, Matplotlib

---

## Key Design Choices

- Cross-subject split at the **subject level** to avoid data leakage
- Multi-seed stability analysis (5 seeds) to assess result robustness
- Class weights to handle mild class imbalance
- Early stopping + learning rate scheduling

---

## Report

- 📄 [Report (PDF)](./report.pdf)

---

## License

This project was developed for academic purposes. Dataset credits: Kaya et al., 2018.
