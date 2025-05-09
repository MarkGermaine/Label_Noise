# Gestational‐Diabetes Label Noise Study

![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)

## 1  Project Summary
This repository accompanies the notebook **`GDM_VAL_May_2025.ipynb`** and the paper *“Gestational Diabetes Diagnoses in Electronic Health Records: A Three‑Step Study of Label Accuracy and Its Impact on Machine‑Learning Models for Early Prediction”*.  
It provides all code needed to reproduce the experiments that investigate how mis‑labelled gestational‑diabetes (GDM) records affect predictive models trained on Irish maternity‑hospital EHR data.

> **Key questions addressed**
> * How accurate are GDM labels in routine electronic health records (EHR)?
> * What is the impact of noisy labels on model training versus model evaluation?
> * How robust are common ML algorithms (Logistic Regression, Random Forest, XGBoost, Explainable Boosting Machine) to increasing levels of false‑positive and false‑negative noise?

## 2  Repository Structure
```
├── environment.yml        # Conda env  (Python 3.10)
├── GDM_VAL_May_2025.ipynb # Executable analysis notebook
├── /src                   # Helper modules
│   ├── data_utils.py      # Data loading / de‑identification helpers (no raw PHI)
│   ├── modelling.py       # Model training / evaluation routines
│   └── plotting.py        # All figures & calibration curves
├── /docs                  # Paper draft, figures for submission
└── README.md              # <‑‑ YOU ARE HERE 🙌
```

## 3  Data Access & Privacy
* **No patient‑level data are stored in this repo.** All identifiers and dates are cryptographically hashed or date‑shifted **before** any file is written to disk.
* The original EHR tables (≈37 k pregnancies, 2018‑2022) are held behind hospital firewalls and can only be queried through the secured `data_utils.get_deidentified_frame()` helper.
* Researchers wishing to run the notebook must request access through the Coombe Hospital Research & Innovation Office and sign the data‑use agreement.

## 4  Quick‑Start
```bash
# 1. clone and create the conda env
git clone https://github.com/<your‑org>/gdm‑label‑noise.git
cd gdm‑label‑noise
conda env create -f environment.yml
conda activate gdm‑label‑noise

# 2. open the notebook
jupyter lab GDM_VAL_May_2025.ipynb
```
The notebook is fully parameterised; simply press **Run All** to regenerate all tables and figures used in the manuscript.

## 5  Reproducing the Experiments
1. **Validate raw EHR labels** against the clinician‑maintained ground‑truth (`src/data_utils.validate_labels`).  
2. **Train baseline models** using `src/modelling.train_models(train_df)`.  
3. **Inject controlled label noise** with `modelling.simulate_noise()` and re‑evaluate.
4. **Plot results** with `plotting.performance_grid()`.

Each step is wrapped in reproducible functions and can be executed from the CLI via `python -m src.run_pipeline --config configs/default.yaml`.

## 6  Dependencies
* Python 3.10
* numpy ≥1.23, pandas ≥1.5, scikit‑learn ≥1.4
* xgboost, interpret‑community, matplotlib
* See `environment.yml` for exact versions.

## 7  How to Cite
If you use this code, please cite the JMIR article:
```bibtex
@article{Germaine2025GDM,
  title={Gestational Diabetes Diagnoses in Electronic Health Records: A Three-Step Study of Label Accuracy and Its Impact on Machine Learning Models for Early Prediction},
  author={Germaine, Mark et al.},
  journal={Journal of Medical Internet Research},
  year={2025}
}
```

## 8  License
This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details.

## 9  Contact
For questions, please open an issue or contact **Mark Germaine** (mark.germaine2 _at_ mail.dcu.ie).
