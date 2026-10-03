# Discrete-Time Markov Chains for Credit Risk Modeling

This repository contains a quantitative finance project that implements a **Discrete-Time Markov Chain (DTMC)** model to analyze credit migration and estimate default probabilities using a representative sample of over **7.6 million monthly observations** from **200,000 unique mortgages** (covering the period 2020–2025).

##  Project Overview

The primary goal of this analysis is to study and apply discrete-time stochastic processes to credit risk assessment. Key methodologies and steps include:

1. **State Space Definition:**
   - **Transient States ($S_T$):** `C` (Current), `D30` (30–59 days delinquent), `D60` (60–89 days delinquent), `D90` (90+ days delinquent).
   - **Absorbing States ($S_A$):** `PRE` (Prepaid), `DEF` (Default).

2. **Transition Matrix Estimation:** 
   - Estimated transition probabilities using Maximum Likelihood Estimation (MLE) combined with Laplace smoothing ($\alpha = 1$) to regularize empirical estimates and prevent zero-probability transitions for rare events.

3. **Absorbing Chain & Lifetime PD Analysis:**
   - Conversion of the transition matrix to its Canonical Form ($P = \begin{bmatrix} Q & R \\ 0 & I \end{bmatrix}$).
   - Computation of the Fundamental Matrix $N = (I - Q)^{-1}$ after verifying spectral radius convergence ($\rho(Q) < 1$).
   - Calculation of the asymptotic absorption probability matrix $B = N \cdot R$ to estimate the non-time-conditioned Lifetime Probability of Default (PD).

4. **Macroeconomic Conditioning & Stress Testing (Basel III):**
   - Calibrating a systematic macroeconomic factor $Z_t$ to overcome time-homogeneity limitations, allowing transition probabilities to adapt dynamically to the economic cycle.

---

## Dataset Download

Due to file size constraints, the primary dataset is hosted externally on Google Drive.

* **Dataset Link:** [Download Mortgage Dataset (Google Drive)](https://drive.google.com/file/d/1A-TPC5s8Z5F08Q9oj-qkRAcvfXwmBmcn/view?usp=sharing)
* **Filename:** `sample_svcg_unificato.csv`

---

## Required Libraries

To run the Jupyter Notebook, ensure you have the following Python packages installed:

```bash
pip install pandas numpy matplotlib seaborn scipy statsmodels scikit-learn pandas-datareader
