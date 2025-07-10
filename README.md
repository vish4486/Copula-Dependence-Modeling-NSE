# Modeling Dependence in Indian Stock Returns Using ARMA-GARCH and Copulas

This project applies a two-step modeling approach to financial time series of Indian NSE stocks (RELIANCE, INFY, and HDFCBANK):

1. **Univariate Modeling** using ARMA-GARCH to remove autocorrelation and conditional heteroskedasticity.
2. **Dependence Modeling** using copulas to capture and analyze nonlinear dependence between assets.

---

## 📊 Dataset

- Daily adjusted closing prices from [Yahoo Finance](https://finance.yahoo.com)
- Stocks: `RELIANCE.NS`, `INFY.NS`, `HDFCBANK.NS`
- Time range: 2015 to 2025

---

## 🔧 Tools & Libraries

- R
- `quantmod`, `rugarch`, `forecast`, `copula`, `VineCopula`, `tseries`

---

## 🔍 Modeling Workflow

### 1. Univariate Modeling
- ARMA(p,q) model selection via AIC
- GARCH(1,1) fitted with Student-t innovations
- Residuals standardized and transformed to pseudo-observations [0,1]

### 2. Dependence Modeling
- Pairwise scatterplots of pseudo-observations
- Estimation of Kendall's τ and tail dependence coefficients
- Parametric copula fitting (Clayton, Gumbel, t, Gaussian)
- Model validation using goodness-of-fit and diagnostic plots

---

## 📁 Structure

- `Project_work_24_25.Rmd`: Full R Markdown source
- `Project_work_24_25.pdf`: Final compiled report
- `data/`: Folder for any saved data
- `plots/`: Generated figures and diagnostic visuals

---

## 📌 Author

**Vishal Nigam**  
University of Trieste – MSc in Data Science & Artificial Intelligence  
July 2025

