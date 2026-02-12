# Numerical Technique Project

**ISFA – M2 Actuariat**  
Techniques Numériques – Final Project (2026)

---

## Project Objective

This project focuses on the estimation of the **Provision for Durable Impairment (PDD)** in an insurance framework using Monte Carlo simulation.

Main objectives:

- Estimate PDD under stochastic interest rates (Vasicek model)
- Compare Naïve and Brownian Bridge Monte Carlo methods
- Extend analysis to multiple periods
- Perform sensitivity analysis (Delta, Vega, Rho)
- Simulate a multi-asset portfolio
- Construct and evaluate a model point
- Estimate Value-at-Risk (VaR)

---

## Model Setup

### Asset Dynamics (Risk-Neutral)

$$
\frac{dS_t}{S_t} = r_t dt + \sigma dW_t
$$

### Interest Rate Model (Vasicek)

$$
dr_t = \gamma (b - r_t) dt + \sigma_r dW_t^r
$$

Correlation between Brownian motions:

$$
\rho = 0.1
$$

### Baseline Parameters

- $r_0 = 2\%$
- $b = 2.5\%$
- $\gamma = 0.2$
- $\sigma_r = 1\%$
- $\sigma = 30\%$
- $S_a = 110$
- $S_0 = 100$
- $\alpha = 0.8$

---

## Monte Carlo Methods

### Naïve Method
- Euler discretization
- Barrier evaluated only on grid points
- Simple but biased

### Refined Method
- Brownian Bridge correction
- Improved barrier crossing estimation
- Better convergence

---

## Sensitivity Analysis

Greeks computed using finite differences:

$$
\text{Delta} = \frac{\partial PDD}{\partial S_0}
$$

$$
\text{Vega} = \frac{\partial PDD}{\partial \sigma}
$$

$$
\text{Rho} = \frac{\partial PDD}{\partial r_0}
$$

---

## Value-at-Risk

Portfolio loss:

$$
L_T = \sum_{i=1}^{10} \alpha_i \sum_{t=0}^{T-1} \lambda_t^i
$$

VaR definition:

$$
\text{VaR}_\beta(L_T) = \inf \{ x \in \mathbb{R} : P(L_T \le x) \ge \beta \}
$$

---

## Reproducibility

- Fixed random seed
- Manual Cholesky decomposition
- No built-in multivariate simulation functions
