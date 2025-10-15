# October VIX Analysis

### Quantitative Study on Election-Year Volatility Dynamics (1990–2023)

This project investigates whether **U.S. presidential elections systematically influence volatility pricing** in equity markets, using the **CBOE Volatility Index (VIX)** as a proxy for implied risk.  
By isolating **October**, a historically pivotal month for volatility repricing, the analysis quantifies how **political uncertainty** manifests in market-implied expectations of risk.

## Summary of Findings

- **Average October VIX Return (All Years):** +3.4%  
- **Average October VIX Return (Election Years):** +25.0%  
- **Probability of Positive Return:** 56% overall vs. 100% in election years  
- **OLS:** Election years correspond to roughly **+28 percentage points** higher October VIX returns (*p = 0.007*).  
- **Penalized Logit:** Election years increase the odds of a positive October return by ~7x (*p ≈ 0.09*).  
- **Bootstrap CIs:** Only election-year Octobers show mean returns statistically distinguishable from zero (95% CI: 15.4%–35.8%).

Together, these results indicate that **election cycles act as a structural catalyst for volatility repricing**, reflecting higher uncertainty premia embedded in options markets.

## Research Objective

To test whether **U.S. presidential election years** predict **systematic differences in VIX behavior** during October — a month historically associated with elevated market risk events (e.g., 1987, 2008, 2022).  
The analysis combines macroeconomic reasoning with empirical testing to bridge **political-cycle theory** and **market-based risk measurement**.

## Methodology

1. **Data**
   - Source: *Bloomberg Terminal — VIX Daily Close (1990–2023)*  
   - File: `data/vix_data_raw.xlsx`
   - Frequency: Daily (transformed to monthly endpoints)

2. **Computation**
   - October return = %Δ from September-end close → October-end close  
   - Election years = {1992, 1996, 2000, 2004, 2008, 2012, 2016, 2020}  

3. **Models**
   - **OLS Regression:**  
     `OctReturn ~ ElectionYear (+ SepEndVIX control)`  
   - **Penalized Logit (ridge):**  
     `Pos ~ ElectionYear` (binary indicator for positive return)
   - **Bootstrap (10,000 resamples):**  
     Non-parametric confidence intervals for mean October returns

4. **Diagnostics**
   - Confidence Intervals (95%)  
   - Pseudo R² / Accuracy  
   - Odds Ratios  
   - Robustness via bootstrapped sampling distributions

## Key Results

| Model | Variable | Coefficient | p-value | Interpretation |
|:--|:--|:--|:--|:--|
| **OLS (Baseline)** | ElectionYear | 0.2819 | 0.007 | +28 pp October return effect |
| **OLS (With SepEndVIX)** | ElectionYear | 0.2695 | 0.009 | Effect robust to baseline volatility |
| **Penalized Logit** | ElectionYear | 1.95 | 0.087 | ~7x higher odds of positive October return |
| **Bootstrap CI (Election Years)** | — | 24.97% | — | CI (15.4%, 35.8%) excludes zero |

## Interpretation

The results demonstrate that **election-year uncertainty is priced into volatility markets well before election day**.  
This pattern reflects elevated **demand for downside protection** and **systematic volatility risk premia**, consistent with macro-financial models of uncertainty and risk aversion.

Quantitatively, the effect is both **statistically significant** and **economically large** — suggesting that volatility instruments like the VIX internalize political-cycle risk as a recurring structural feature of market behavior.

## Analyst Perspective

This study integrates **macroeconomic intuition** with **empirical market modeling** — translating qualitative political uncertainty into quantifiable risk signals.  
The workflow mirrors how top macro hedge funds approach research:  
1. Form a hypothesis grounded in real-world dynamics.  
2. Test it empirically using robust statistical methods.  
3. Evaluate stability across model specifications and data subsamples.

---

## Technical Implementation

**Languages & Tools:**  
- Python (pandas, statsmodels, matplotlib, numpy)  
- Bloomberg Terminal data extraction  
- Jupyter Notebook environment  

**Techniques:**  
- Regression modeling (OLS, penalized Logit)  
- Bootstrap confidence intervals  
- Data cleaning, feature engineering, and reproducible analysis  

---

## Reproduction Notes

- **Data:** `data/vix_data_raw.xlsx`  
- **Notebook:** `vix_election_trade.ipynb`  
- October return defined as % change between September- and October-end VIX closes.  
- Models estimated using `statsmodels`.  
- Bootstrap uses 10,000 resamples with replacement.  
- Election years highlighted: 1992, 1996, 2000, 2004, 2008, 2012, 2016, 2020.


## Conclusion

This project quantifies how **political transitions transmit into volatility markets**, showing that U.S. election cycles consistently amplify October risk pricing.  
It demonstrates a research philosophy grounded in **data discipline, statistical rigor, and macroeconomic reasoning** — the same analytical foundations that drive investment research at leading quantitative and macro hedge funds.

### 🔗 Repository Structure
