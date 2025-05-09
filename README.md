# Gestational‐Diabetes Label Noise Study

![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)

## 1  Project Summary
This repository accompanies the notebook **`GDM_VAL_May_2025.ipynb`** and the paper *"Gestational Diabetes Diagnoses in Electronic Health Records: A Three‑Step Study of Label Accuracy and Its Impact on Machine‑Learning Models for Early Prediction"*.  
It provides code examples and analysis pipelines used to explore the effects of label noise in gestational diabetes (GDM) diagnosis. The notebook is designed as a reference for researchers who wish to adapt the methods to their own datasets.

> **Key questions addressed**
> * How accurate are GDM labels in routine electronic health records (EHR)?
> * What is the impact of noisy labels on model training versus model evaluation?
> * How robust are common ML algorithms (Logistic Regression, Random Forest, XGBoost, Explainable Boosting Machine) to increasing levels of false‑positive and false‑negative noise?

## 2  Repository Structure
```
├── environment.yml        # Conda environment (Python 3.10)
├── GDM_VAL_May_2025.ipynb # Annotated reference notebook
├── /src                   # Modular helper scripts
│   ├── data_utils.py      # Data loading / de-identification helpers (no raw PHI)
│   ├── modelling.py       # Model training / evaluation routines
│   └── plotting.py        # All figures & calibration curves
├── /docs                  # Paper draft, figures for submission
└── README.md              # <-- YOU ARE HERE 🙌
```

## 3  Data Access & Privacy
* **No patient-level data are included in this repository.** All identifiers are hashed or omitted, and the code is written to be adaptable to other de‑identified datasets.
* The original EHR data (≈37k pregnancies, 2018–2022) remains securely within the Coombe Women & Infants University Hospital infrastructure and is not accessible externally.
* If attempting to replicate the pipeline on local data, ensure compliance with your institution’s data privacy protocols.

## 4  Getting Started
```bash
# 1. Clone the repository and create the environment
git clone https://github.com/<your-org>/gdm-label-noise.git
cd gdm-label-noise
conda env create -f environment.yml
conda activate gdm-label-noise

# 2. Open the notebook for review and adaptation
jupyter lab GDM_VAL_May_2025.ipynb
```
The notebook is intended as a guide. It is not runnable end-to-end without a valid, structured dataset. Instead, researchers are encouraged to copy and adapt relevant cells and functions to their own cohort.

## 5  Using the Methods
1. **Review the validation logic** in `data_utils.validate_labels()` to understand the reference-standard comparison.
2. **Adapt the modelling pipeline** from `modelling.py` to your local dataset schema.
3. **Introduce simulated label noise** using `simulate_noise()` to test robustness.
4. **Plot results** with the heatmap and calibration functions in `plotting.py`.

All experiments shown in the paper were conducted using internally validated, time-restricted features available at ≤12 weeks’ gestation.

## 6  Dependencies
* Python 3.10
* numpy ≥1.23, pandas ≥1.5, scikit-learn ≥1.4
* xgboost, interpret-community, matplotlib
* See `environment.yml` for full environment spec

## 7  How to Cite
If you use or adapt this code, please cite the JMIR article:
```bibtex
@article{Germaine2025GDM,
  title={Gestational Diabetes Diagnoses in Electronic Health Records: A Three-Step Study of Label Accuracy and Its Impact on Machine Learning Models for Early Prediction},
  author={Germaine, Mark et al.},
  journal={Journal of Medical Internet Research},
  year={2025}
}
```

## 8  License
This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details.

## 9  Contact
For questions, please open an issue or contact **Mark Germaine** (mark.germaine2 _at_ mail.dcu.ie).
