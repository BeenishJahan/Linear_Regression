# Building Energy Performance Prediction
**Reproducing Published Research on Sustainable Building Design**

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

## 📋 Project Overview

Independent reproduction and verification of **Tsanas & Xifara (2012)** research on predicting building heating loads using machine learning. This project validates key research findings through modern ML implementation and extends the methodology with Ridge Regression.

**Status:** ✅ Phase 1 Complete | 🔄 Phase 2 (Random Forest) Coming Soon

---

## 🎯 Key Findings Verified

| Research Finding | Status | Evidence |
|-----------------|--------|----------|
| Orientation has negligible impact | ✅ Verified | Correlation ~0.00, coefficients ~0.00 |
| Multicollinearity in structural features | ✅ Verified | RC↔SA: -0.99, OH↔RA: -0.97 |
| Linear regression shows mediocre results | ✅ Verified | RMSE ~2.89 kWh (comparable to paper's ~3.14) |
| Ridge improves stability, not accuracy | ✅ Verified | Minimal metric improvement (0.0002 kWh) |

**Conclusion:** All findings independently reproduced. Non-linearity confirmed as primary limitation.

---

## 📊 Model Results

| Model | R² Score | RMSE (kWh) | MAE (kWh) | Key Insight |
|-------|----------|-----------|----------|-------------|
| **Linear Regression** | 0.9178 | 2.8876 | 2.1019 | Baseline performance |
| **Ridge (α=0.1)** | 0.9178 | 2.8874 | 2.1017 | Stabilized coefficients, minimal prediction improvement |

Ridge's small optimal alpha (0.1) confirms multicollinearity is not the primary limitation — non-linearity is.

---

## 🛠️ Tech Stack

- **Language:** Python 3.8+
- **Libraries:** pandas, numpy, matplotlib, seaborn, scikit-learn
- **Models:** LinearRegression, RidgeCV
- **Preprocessing:** StandardScaler, OneHotEncoder
- **Environment:** Jupyter Notebook

---

## 📁 Repository Structure

```
├── energy_efficiency_analysis.ipynb    # Main analysis notebook
├── ENB2012_data.csv                    # Dataset (UCI ML Repository)
├── README.md                           # This file
└── requirements.txt                    # Python dependencies
```

---

## 📈 Dataset

**Source:** UCI Machine Learning Repository  
**Paper:** Tsanas, A. & Xifara, A. (2012). Energy and Buildings, Vol. 49, pp. 560-567  
**Samples:** 768 simulated residential buildings  
**Features:** 8 design parameters (compactness, surface area, glazing, orientation, etc.)  
**Target:** Heating Load (kWh)

---

## 🚀 Quick Start

```bash
# Clone repository
git clone https://github.com/BeenishJahan/Linear_Regression.git

# Install dependencies
pip install -r requirements.txt

# Open notebook
jupyter notebook model.ipynb
```

---

## 🔬 Methodology

1. **Exploratory Data Analysis** → Identified bimodal distribution, multicollinearity
2. **Preprocessing** → One-hot encoding, StandardScaler
3. **Baseline Model** → Linear Regression (OLS)
4. **Regularization** → RidgeCV with 5-fold cross-validation
5. **Verification** → Compared results to paper's IRLS findings

**Note:** This project uses OLS (sklearn) rather than IRLS (paper's method). Despite methodological differences, findings align.

---

## 🌍 Real-World Relevance

**India's Building Challenge:**
- 75% of 2030 building stock yet to be constructed
- 300M new urban residents by 2040
- Buildings account for 33% of electricity consumption
- AC demand projected to grow 15x by 2050

**ML can guide energy-efficient design BEFORE construction begins.**

---

## 🔮 Future Work (Phase 2)

Implement Random Forest to:
- Verify paper's claim of **3x performance improvement** (target: RMSE ~1.01 kWh)
- Capture non-linear relationships linear models miss
- Compare feature importance (RF vs linear coefficients)
- Complete full research reproduction study

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

**Beenish Jahan** | [LinkedIn]([LinkedIn](https://www.linkedin.com/in/beenishjahan)) | [Email]([Email](mailto:beenishjahan2003@gmail.com))

⭐ If you found this project helpful, please consider starring the repository!

---

## 📄 License

MIT License - See [LICENSE](LICENSE) file for details.