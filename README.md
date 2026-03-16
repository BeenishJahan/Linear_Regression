# Building Energy Performance Prediction
**Reproducing Published Research on Sustainable Building Design**

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## 📋 Project Overview

Independent reproduction and verification of **Tsanas & Xifara (2012)** research on predicting building heating loads using machine learning. This project validates key research findings through modern ML implementation — starting with a linear baseline and progressively extending to ensemble methods.

**Workflow:** Phase 1 (OLS Linear Regression + Ridge) → Phase 2 (Random Forest)

**Status:** ✅ Phase 1 Complete | ✅ Phase 2 Complete

---

## 🎯 Key Findings Verified

| Research Finding | Status | Evidence |
|-----------------|--------|----------|
| Orientation has negligible impact | ✅ Verified | Correlation ~0.00, coefficients ~0.00 |
| Multicollinearity in structural features | ✅ Verified | RC↔SA: -0.99, OH↔RA: -0.97 |
| Linear regression shows mediocre results | ✅ Verified | RMSE ~2.89 kWh (comparable to paper's ~3.14) |
| Ridge improves stability, not accuracy | ✅ Verified | Minimal metric improvement (0.0002 kWh) |
| Non-linearity is the primary limitation | ✅ Verified | Random Forest RMSE dropped to 0.51 kWh |

**Conclusion:** All findings independently reproduced. Non-linearity confirmed and addressed.

---

## 📊 Model Results

| Phase | Model | R² Score | RMSE (kWh) | MAE (kWh) | Key Insight |
|-------|-------|----------|-----------|----------|-------------|
| **Phase 1** | Linear Regression (OLS) | 0.9178 | 2.8876 | 2.1019 | Baseline performance |
| **Phase 1** | Ridge (α=0.1) | 0.9178 | 2.8874 | 2.1017 | Stabilized coefficients, minimal improvement |
| **Phase 2** | Random Forest | 0.9974 | 0.5103 | — | Captures non-linearity, near-perfect fit |

> Ridge's small optimal alpha (0.1) confirmed multicollinearity was not the primary limitation — non-linearity was. Random Forest proved this by cutting RMSE by ~82%.

---

## 🔬 Methodology

This project was built in two phases, intentionally starting simple:

### Phase 1 — Linear Baseline
1. **Exploratory Data Analysis** → Identified bimodal distribution, multicollinearity
2. **Preprocessing** → One-hot encoding, StandardScaler
3. **OLS Linear Regression** → Established performance baseline
4. **Ridge Regression** → Tested regularization via RidgeCV (5-fold CV)
5. **Verification** → Compared results to paper's IRLS findings

### Phase 2 — Ensemble Model
6. **Reused the exact same train/test split** from Phase 1 (saved as `.npy` files) to ensure a fair comparison
7. **Random Forest Regressor** → Captured non-linear relationships linear models could not
8. **Evaluation** → Compared all models head-to-head

**Note:** This project uses OLS (sklearn) rather than IRLS (paper's method). Despite methodological differences, findings align closely.

---

## 📈 Dataset

**Source:** UCI Machine Learning Repository  
**Paper:** Tsanas, A. & Xifara, A. (2012). Energy and Buildings, Vol. 49, pp. 560-567  
**Samples:** 768 simulated residential buildings  
**Features:** 8 design parameters (compactness, surface area, glazing, orientation, etc.)  
**Target:** Heating Load (kWh)

---

## 🛠️ Tech Stack

- **Language:** Python 3.8+
- **Libraries:** pandas, numpy, matplotlib, seaborn, scikit-learn
- **Models:** LinearRegression, RidgeCV, RandomForestRegressor
- **Preprocessing:** StandardScaler, OneHotEncoder
- **Environment:** Jupyter Notebook

---

## 📁 Repository Structure

```
├── model.ipynb              # Phase 1 — OLS + Ridge Regression
├── ensemble_mod...          # Phase 2 — Random Forest
├── data_energy.csv          # Dataset (UCI ML Repository)
├── requirements.txt         # Python dependencies
├── .gitignore               
├── LICENSE                  
└── README.md
```

---

## 🚀 Quick Start

```bash
# Clone repository
git clone https://github.com/BeenishJahan/Linear_Regression.git

# Install dependencies
pip install -r requirements.txt

# Run Phase 1 first (generates the train/test split)
jupyter notebook Linear_Regression/model.ipynb

# Then run Phase 2
jupyter notebook ensemble_model/random_forest.ipynb
```

> ⚠️ Run Phase 1 before Phase 2 — the Random Forest notebook loads the preprocessed train/test split saved by the linear regression notebook.

---

## 🌍 Real-World Relevance

**India's Building Challenge:**
- 75% of 2030 building stock yet to be constructed
- 300M new urban residents by 2040
- Buildings account for 33% of electricity consumption
- AC demand projected to grow 15x by 2050

**ML can guide energy-efficient design BEFORE construction begins.**

---

## 🔮 Future Work

- Hyperparameter tuning for Random Forest (grid search / random search)
- Compare feature importance: Random Forest vs linear coefficients

---

## 📚 Reference

```
Tsanas, A., & Xifara, A. (2012). 
Accurate quantitative estimation of energy performance of residential buildings 
using statistical machine learning tools. 
Energy and Buildings, 49, 560-567.
DOI: 10.1016/j.enbuild.2012.03.003
```

---

## 📧 Contact

**Beenish Jahan** | [LinkedIn](https://www.linkedin.com/in/beenishjahan) | [Email](mailto:beenishjahan2003@gmail.com)

⭐ If you found this project helpful, please consider starring the repository!

---

## 📄 License

MIT License - See [LICENSE](LICENSE) file for details.