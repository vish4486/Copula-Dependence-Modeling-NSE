# 📊 Dependence Modeling of Financial Time Series using Copulas

This project is part of the *Data Science for Insurance* course. The objective is to model the **marginal dynamics** and **dependence structure** of financial log-returns from three Indian stocks: **RELIANCE**, **INFY**, and **HDFCBANK**.

The analysis is structured in two major parts:

---

## 🔹 Section 1: Univariate Modeling (ARMA-GARCH)

Each stock's log-returns are modeled individually to remove serial correlation and account for volatility clustering.

### ✔ Steps:
- Fit **ARMA(p,q)** models using `auto.arima()` with stationarity enforced.
- Perform residual diagnostics (ACF, Ljung-Box test).
- Fit **GARCH(1,1)** models using `rugarch::ugarchfit()` with **Student-t** innovations.
- Extract **standardized residuals**.
- Transform standardized residuals into **pseudo-observations** via empirical CDF (ranks).

---

## 🔹 Section 2: Dependence Modeling via Copulas

This section models the joint dependence between the standardized innovations of the three stocks.

### ✔ Steps:
1. **Scatterplots** of pseudo-observations to visually inspect dependence structure.
2. Estimate **nonparametric dependence measures**:
   - Kendall’s τ
   - Spearman’s ρ
3. Compute **empirical tail dependence coefficients**:
   - Lower tail (λₗ)
   - Upper tail (λᵤ)
4. Fit **four bivariate copulas** for each pair:
   - Clayton, Gumbel, Gaussian, t-copula
5. Select the **best copula model** using:
   - Log-likelihood comparison
   - Cramér-von Mises Goodness-of-Fit test (`VineCopula`)
6. Provide **graphical diagnostics**:
   - Density contours
   - Simulated vs empirical pseudo-observations

---

## 📌 Key Findings

| Pair                | Best Copula | λₗ (Lower Tail) | λᵤ (Upper Tail) | Observation |
|---------------------|-------------|------------------|------------------|-------------|
| RELIANCE – INFY     | t-Copula    | 0.193            | 0.092            | Weak tail dependence |
| RELIANCE – HDFCBANK | t-Copula    | 0.277            | 0.146            | Strongest dependence |
| INFY – HDFCBANK     | t-Copula    | 0.193            | 0.092            | Similar to REL–INFY |

---

## 🛠️ Packages Used
- `forecast` / `rugarch` – ARMA-GARCH modeling  
- `copula` – Copula fitting and diagnostics  
- `VineCopula` – GOF tests and copula validation  
- `ggplot2` – Custom visualization  

---

## 📁 Project Structure

project-root/
├── data/ # Raw and cleaned data
├── code/ # All R scripts (ARMA-GARCH, Copula fitting)
├── plots/ # Exported plots (ACF, GARCH residuals, pseudo-observations, copulas)
└── README.md # Project summary and documentation


---

## 📈 Author Notes
This project aims to demonstrate both **sound marginal modeling** and **robust dependence modeling** using copula theory in R — as commonly applied in risk management of financial portfolios or in insurance.

---

## 📌 Author
Vishal Nigam
University of Trieste – MSc in Data Science & Artificial Intelligence
July 2025
