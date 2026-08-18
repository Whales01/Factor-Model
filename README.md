# Cross-Market Multi-Factor Asset Pricing Analysis
## Empirical Assessment of FF3, Carhart4, and FF5 Models — US & UK Equity Markets (2014–2024)

**Author:** Olawale  
**Qualification:** ACA | MSc Financial Technology (Distinction)  
**Research Period:** 2014 – 2024  
**Markets Covered:** United States (NYSE/NASDAQ) | United Kingdom (LSE)

---

## Research Question

Which factor model — Fama-French Three-Factor (FF3), Carhart Four-Factor (C4), or Fama-French Five-Factor (FF5) — most completely explains the cross-section of stock returns across US and UK markets by minimising residual pricing error (alpha, α)?

What do the alpha residuals reveal about investment opportunities that systematic factor models cannot capture?

---

## Overview

This repository contains an empirical study comparing the explanatory power of three canonical asset pricing models across carefully selected US and UK equity portfolios. The primary objective is to determine which model best minimises unexplained alpha — the residual pricing error that represents genuine idiosyncratic return generation beyond systematic factor exposure.

The study is motivated by a practical investment question: **if factor models cannot fully explain a stock's returns, what does that residual alpha tell us about the investment opportunity?**

---

## Methodology

### Factor Models Tested

| Model | Factors |
|---|---|
| **Fama-French Three-Factor (FF3)** | Market (Mkt-RF), Size (SMB), Value (HML) |
| **Carhart Four-Factor (C4)** | Mkt-RF, SMB, HML, Momentum (Mom) |
| **Fama-French Five-Factor (FF5)** | Mkt-RF, SMB, HML, Profitability (RMW), Investment (CMA) |

All factor data sourced from the **Kenneth R. French Data Library** via `pandas-datareader`.  
UK market analysis uses a **European proxy factor model** to account for regional factor differences.

### Stock Selection Framework

Assets were selected across four distinct investment style categories to test whether factor models perform differently across return profiles:

| Category | US Assets | UK Assets |
|---|---|---|
| **Aggressive Growth** | NVDA (NVIDIA), TSLA (Tesla) | OCDO (Ocado Group) |
| **Deep Value** | XOM (ExxonMobil) | LLOY (Lloyds Banking Group) |
| **High Quality / Robust Profitability** | JNJ (Johnson & Johnson) | ULVR (Unilever) |
| **Mid-Cap / High Momentum** | NVDA (NVIDIA) | AAL (Anglo American Plc) |

### Regression Framework

For each asset and each factor model, OLS regression is run with the following specification:

```
R_i - R_f = α + β₁(Mkt-RF) + β₂(SMB) + β₃(HML) [+ β₄(Mom)] [+ β₄(RMW) + β₅(CMA)] + ε
```

Key metrics extracted per regression:
- **Alpha (α)** — residual unexplained return
- **Alpha p-value** — statistical significance of alpha
- **R²** and **Adjusted R²** — model explanatory power

---

## Key Findings

### 1. FF5 Provides the Most Complete Factor Explanation
Across both markets and all assets, the FF5 model consistently achieves the highest Adjusted R², confirming that adding profitability (RMW) and investment (CMA) factors materially improves model fit beyond the FF3 baseline. The Carhart momentum factor adds less incremental explanatory power in this sample.

### 2. Persistent Alpha Survives Even the Most Complete Factor Model
**NVIDIA (NVDA)** generates statistically significant positive alpha of approximately **3.3% per month** that no model eliminates — a finding robust across FF3, C4, and FF5 (p-value < 0.001 in all cases). This is the most important investment-relevant result: it demonstrates that factor models, even five-factor specifications, cannot fully capture the return dynamics of certain high-growth companies.

**JNJ and XOM** show alpha close to zero with statistically insignificant p-values — their excess returns are well-explained by systematic factor exposures, leaving limited room for alpha generation from stock selection alone.

**TSLA** occupies a borderline position — positive alpha approaching statistical significance — consistent with its unusual factor profile: high market beta, negative value loading, and partial momentum sensitivity.

### 3. US and UK Markets Show Different Alpha Profiles
The US sample shows higher idiosyncratic alpha, particularly in technology stocks, while the UK sample shows tighter factor explanation in financial sector stocks (Lloyds Banking Group). This cross-market difference has direct implications for where active long/short strategies are most likely to generate excess returns.

### 4. The Limits of Factor Models
The persistent alpha in NVDA across all models is a reminder that factor-based strategies leave genuine return opportunities on the table for investors who can identify company-specific drivers of excess return — the core thesis of fundamental long/short equity investing.

---

## Investment Implications

From a practical investing perspective, this analysis suggests three actionable takeaways:

1. **Stocks with persistent, statistically significant alpha that survives multi-factor adjustment are the most compelling candidates for fundamental long investment.** The factor models are telling you that something about this company's return profile cannot be explained by systematic exposure alone.

2. **Factor models are most useful for eliminating factor-driven noise from return attribution — not for identifying investment ideas.** The alpha residual is where the investment insight lives.

3. **Cross-market analysis reveals that the richest alpha opportunities in this sample period were concentrated in the US growth segment rather than UK financials** — consistent with the structural differences between the two markets during a period of US technology dominance.

---

## Repository Structure

```
├── FactorModelAssessment.ipynb    # Main analysis notebook — US & UK markets
├── US_Stock_Data_4_Factor_Model.csv   # Cached US daily price data
├── README.md                      # This file
```

---

## Technical Stack

| Library | Purpose |
|---|---|
| `pandas` | Data manipulation and time series alignment |
| `numpy` | Numerical computation |
| `yfinance` | Historical equity price data |
| `pandas-datareader` | Fama-French factor data from Kenneth French library |
| `statsmodels` | OLS regression and statistical inference |
| `matplotlib` / `seaborn` | Visualisation |

---

## How to Run

```bash
# Clone the repository
git clone https://github.com/Whales01/Factor-Model

# Install dependencies
pip install pandas numpy yfinance pandas-datareader statsmodels matplotlib seaborn

# Open the notebook
jupyter notebook FactorModelAssessment.ipynb
```

Run all cells sequentially. The notebook fetches live data from Yahoo Finance and the French Data Library — an internet connection is required.

---

## Limitations and Further Research

- Sample limited to four US and four UK stocks over a ten-year window
- Broader cross-section analysis would strengthen conclusions
- European proxy factors for the UK market introduce potential measurement error — a fully localised UK factor dataset would improve precision
- Alpha persistence across sub-periods (pre/post-COVID, rate cycle phases) warrants further investigation
- Additional factor specifications (quality, low-volatility, ESG factors) could extend the analysis

---

## Background

This analysis was developed as part of original research conducted during an MSc in Financial Technology at the University of Surrey. It reflects a genuine interest in understanding where systematic factor models succeed and where they fail — and what those failures reveal about active investment opportunities.

The methodology draws on foundational academic literature:
- Fama, E. F., & French, K. R. (1993). Common risk factors in the returns on stocks and bonds.
- Carhart, M. M. (1997). On persistence in mutual fund performance.
- Fama, E. F., & French, K. R. (2015). A five-factor asset pricing model.

---

*For questions or collaboration enquiries, please connect via [LinkedIn](https://www.linkedin.com/in/awotunde-olawale-0352079b/)*
