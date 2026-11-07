# ICU In-Hospital Mortality Prediction Using LSTM and Liquid Neural Networks

A deep learning project exploring in-hospital mortality prediction among ICU patients using **Attention-BiLSTM, Liquid Neural Networks (LTC), and a Hybrid LSTM–LTC architecture**.

## Overview

Accurate mortality risk prediction in Intensive Care Units (ICUs) can support clinical risk assessment and patient monitoring. This project investigates deep learning approaches for modelling temporal patterns in ICU clinical data and predicting in-hospital mortality.

Three architectures are implemented and compared:

- **Attention-BiLSTM:** Bidirectional LSTM with an attention mechanism to learn temporal dependencies and relevant clinical patterns.
- **Liquid Neural Network (LNN):** Uses Liquid Time-Constant (LTC) cells to model time-dependent changes in clinical variables.
- **Hybrid LSTM–LTC:** Combines LSTM-based and LTC-based temporal representations using attention and feature fusion.

A validation-weighted ensemble is also evaluated.

## Model Architectures

| Model | Description |
|---|---|
| Attention-BiLSTM | Learns bidirectional temporal representations with attention |
| Liquid Neural Network | Uses LTC cells for continuous-time-inspired temporal modelling |
| Hybrid LSTM–LTC | Combines LSTM and LTC representations |
| Ensemble | Combines model predictions using validation-derived weights |

## Methodology

The experimental workflow includes:

1. ICU clinical data preprocessing and feature preparation.
2. Construction of temporal input sequences.
3. Training of Attention-BiLSTM, LTC-based LNN, and Hybrid LSTM–LTC models.
4. Class-imbalance handling through class weighting.
5. Probability calibration using Platt scaling.
6. Validation-weighted ensemble construction.
7. Performance evaluation using discrimination and calibration metrics.

## Experimental Results

The following results are from the current experimental run (v7).

| Model | AUROC | AUPRC | Brier Score | F1-score |
|---|---:|---:|---:|---:|
| Attention-BiLSTM | 0.9287 | 0.4787 | 0.0524 | 0.5714 |
| Liquid Neural Network | 0.8498 | 0.3381 | 0.0583 | 0.4571 |
| Hybrid LSTM–LTC | 0.9174 | 0.5426 | 0.0452 | 0.6400 |
| Ensemble | **0.9162** | 0.5179 | 0.0489 | 0.5926 |

### Additional Evaluation

- Ensemble AUROC 95% confidence interval: **0.8546–0.9669**
- SOFA-inspired baseline AUROC: **0.8403**
- DeLong comparison (ensemble vs. baseline): **p = 0.041**
- Ensemble net benefit: **0.0460**

The ensemble weights derived from validation performance were:

- Attention-BiLSTM: 0.487
- Liquid Neural Network: 0.174
- Hybrid LSTM–LTC: 0.339

## Evaluation Metrics

The models are evaluated using:

- **AUROC:** Overall discrimination between mortality and survival outcomes.
- **AUPRC:** Precision–recall performance, particularly relevant for imbalanced outcomes.
- **Brier Score:** Probability prediction accuracy and calibration.
- **F1-score:** Balance between precision and recall.
- **Confidence Intervals:** Uncertainty in AUROC estimates.
- **Decision Curve Analysis:** Assessment of potential clinical net benefit.

## Repository Structure

```text
ICU-Mortality-Prediction/
│
├── MIMIC_LNN_SLM.ipynb
└── README.md
```

The current repository contains the experimental
