Project Overview

This project investigates the robustness of deep learning models for cyber-attack detection in Phasor Measurement Unit (PMU) data. Several LSTM-based approaches are evaluated under clean and adversarial conditions to understand their effectiveness against input manipulation attacks such as FGSM.

The main goal is to compare standard supervised models with robustness-enhanced and anomaly-based techniques in a realistic power system cyber-security setting.

Dataset:

Name: Phasor Measurement Unit Data – Labeled (PMU_data.xlsx)

Samples: ~101,000

Features: 15 PMU measurements

Labels:

0 → Normal operation

1 → Cyber-attack / anomaly

The data is standardized and reshaped into sequences of 10 time steps × 15 features for LSTM-based models.

Implemented Models

The following four approaches are implemented and evaluated:

Baseline LSTM

Trained only on clean data

High clean accuracy but vulnerable to adversarial attacks

Baseline LSTM under FGSM Attack

FGSM adversarial examples generated using gradient-based perturbations

Significant accuracy drop observed

Noise-Defense LSTM

Gaussian noise injected during training

Strong robustness against adversarial perturbations

LSTM Autoencoder (Anomaly Detection)

Trained to reconstruct normal PMU behavior

Uses reconstruction error with a statistical threshold (μ + 3σ)

Achieves near-perfect robustness without adversarial training

Project Structure
pmu_project/
│
├── data/
│   └── Phasor Measurement Unit Data - Labeled/
│       └── PMU_data.xlsx
│
├── notebooks/
│   ├── 01_baseline_lstm.ipynb
│   ├── 02_fgsm_attack_baseline.ipynb
│   ├── 03_noise_defense_lstm.ipynb
│   └── 04_lstm_autoencoder.ipynb
│
├── results/
│   ├── cm_clean_baseline.png
│   ├── cm_adv_baseline.png
│   ├── cm_clean_noise_defense.png
│   ├── cm_adv_noise_defense.png
│   ├── cm_clean_autoencoder.png
│   └── cm_adv_autoencoder.png
│
├── README.md
└── requirements.txt

Key Results (Summary)

Baseline LSTM: Performs well on clean data but suffers notable accuracy loss under FGSM attack.

Noise-Defense LSTM: Maintains almost identical performance on clean and adversarial data.

LSTM Autoencoder: Achieves the highest robustness, with near-perfect detection on both clean and adversarial inputs.

These results indicate that noise-regularized and anomaly-based models are more reliable than standard supervised models for PMU cyber-attack detection.

Requirements

Python 3.8+

TensorFlow / Keras

NumPy

Pandas

Scikit-learn

Matplotlib

Seaborn

Install dependencies using:

pip install -r requirements.txt

How to Run

Place the dataset in the data/ directory.

Run notebooks in order:

01_baseline_lstm.ipynb

02_fgsm_attack_baseline.ipynb

03_noise_defense_lstm.ipynb

04_lstm_autoencoder.ipynb

Results and confusion matrices will be saved in the results/ folder.

Conclusion

This project demonstrates that while standard LSTM models are effective on clean PMU data, they are vulnerable to adversarial manipulation. Noise-based regularization and anomaly detection using LSTM autoencoders significantly improve robustness and are better suited for real-world power system cyber-security application
