# Volatility Index Equity Trade
Quantitative research examining whether U.S. presidential election cycles systematically affect implied volatility dynamics in October.

## Overview
This notebook tests whether political uncertainty during election years leads to statistically significant changes in October VIX performance.

## Key Findings
- Average October VIX return ≈ **+3.4%**
- Average election-year October return ≈ **+25.0%**
- OLS coefficient on ElectionYear = **0.28 (p = 0.007)**
- Only election-year Octobers have mean returns statistically > 0 (95% bootstrap CI: 15–36%)

## Methods
- **Data:** Daily VIX close prices (1990–2023)
- **Models:** OLS and logistic regressions (statsmodels)
- **Bootstrap:** 10,000 resamples for robustness
- **Visualization:** Matplotlib bar chart highlighting election years

## Interpretation
Election-year Octobers show structurally different volatility behavior, consistent with risk repricing under political uncertainty.

## Reproduction
1. Clone the repo  
2. Install requirements: `pip install -r requirements.txt`  
3. Open notebook: `notebook/vix_october_analysis.ipynb`  
4. Replace path to your own VIX dataset if necessary

## License
For academic and personal demonstration only.
