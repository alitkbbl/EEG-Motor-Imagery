# EEG Motor Imagery Classification (CSP + LDA)

A modular BCI pipeline for decoding left vs. right hand motor imagery from EEG, built on the PhysioNet Motor Movement/Imagery dataset (Subject 01, runs 4/8/12/14) using `mne-python` and `scikit-learn`.

## Pipeline
1. **EDA** – PSD/topomap inspection, confirming μ (8–12 Hz) and β (13–30 Hz) activity.
2. **Preprocessing** – High-pass filter (0.5 Hz), CAR, ICA-based artifact rejection.
3. **Epoching** – 60 epochs (30 left / 30 right), validated via contralateral μ-ERD (C3/C4).
4. **Feature Extraction** – CSP (4 components, Ledoit-Wolf shrinkage) + LDA classifier.
5. **Optimization** – Sliding-window search identified [1.5s, 2.2s] as the optimal discriminative window.
6. **Cross-subject Evaluation** – Tested on Subjects 01–10 to assess generalization.

## Results
- Best CV accuracy: **80.00% ± 6.67%** (Subject 01, optimized time window)
- Cross-subject accuracy varied (e.g., Subject 02: 84.44%), confirming subject-dependent BCI performance.

