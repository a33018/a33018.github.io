---
layout: page
title: Volatility Modeling of U.S. 10-Year Treasury Yields Using GARCH
---

This page presents a GARCH (Generalized Autoregressive Conditional Heteroskedasticity) volatility analysis of 10-Year U.S. Treasury yields using data from the Federal Reserve Economic Data (FRED).

## Overview

GARCH models are used to model and forecast financial volatility. Unlike simple rolling standard deviations, GARCH models capture:
- **Volatility clustering**: periods of high volatility tend to cluster together
- **Mean reversion**: volatility tends to return to a long-run average
- **Persistence**: the impact of past shocks on current volatility

---

## Summary Statistics

Key statistics for 10-Year Treasury yields and their daily changes over the analysis period.

**Insert summary statistics table here after running the analysis**

---

## 1. Historical 10-Year Treasury Yields

The complete time series of 10-Year U.S. Treasury constant maturity rates.

![10-Year Treasury Yields](/assets/images/treasury/Plot1_Yields_TimeSeries.png)

---

## 2. Daily Yield Changes

Daily changes in Treasury yields show periods of high and low volatility, with occasional extreme movements during market stress events.

![Daily Yield Changes](/assets/images/treasury/Plot2_Yield_Changes.png)

---

## 3. Distribution of Yield Changes

The distribution of daily yield changes compared to a normal distribution (red dashed line). Notice the "fat tails" - extreme changes occur more frequently than a normal distribution would predict.

![Distribution of Changes](/assets/images/treasury/Plot3_Distribution.png)

The distribution typically shows:
- **Higher kurtosis** than normal distribution (fat tails)
- **Slight skewness**
- Evidence that extreme events are more common than normally distributed data would suggest

---

## 4. GARCH(1,1) Conditional Volatility

The estimated volatility from the GARCH(1,1) model. This represents the model's real-time estimate of the standard deviation of yield changes.

![GARCH Volatility](/assets/images/treasury/Plot4_GARCH_Volatility.png)

**Key observations:**
- Volatility spikes during financial crises and market stress periods
- Clear evidence of volatility clustering
- Volatility is time-varying and persistent

---

## 5. GARCH vs Rolling Window Volatility

Comparison between GARCH(1,1) conditional volatility and a simple 30-day rolling standard deviation.

![Volatility Comparison](/assets/images/treasury/Plot5_Volatility_Comparison.png)

**Why GARCH is better:**
- More responsive to recent market conditions
- Captures volatility dynamics more accurately
- Provides probabilistic forecasts of future volatility
- Better captures the persistence of volatility shocks

---

## 6. Recent Volatility (Last 5 Years)

A closer look at recent volatility patterns.

![Recent Volatility](/assets/images/treasury/Plot6_Recent_Volatility.png)

---

## 7. Evidence of Volatility Clustering

Autocorrelation function (ACF) of squared yield changes. Significant autocorrelation indicates volatility clustering - the key feature that GARCH models capture.

![ACF Squared Returns](/assets/images/treasury/Plot7_ACF_Squared_Returns.png)

Bars extending beyond the red dashed lines indicate statistically significant autocorrelation, confirming the presence of ARCH effects (volatility clustering).

---

## GARCH Model Results

### Model Specification
- **Model**: GARCH(1,1)
- **Mean equation**: Constant mean
- **Variance equation**: σ²ₜ = ω + α·ε²ₜ₋₁ + β·σ²ₜ₋₁

Where:
- **ω** (omega): Long-run variance level
- **α** (alpha): Impact of past shocks on current volatility
- **β** (beta): Persistence of volatility
- **α + β**: Total persistence (closer to 1 = more persistent)

### Model Comparison

Two GARCH(1,1) models were estimated:
1. **GARCH(1,1) with Normal distribution**
2. **GARCH(1,1) with Student-t distribution** (better for fat-tailed data)

The Student-t distribution typically provides a better fit for financial data due to its heavier tails.

**Model comparison based on Information Criteria available in output files**

---

## Interpretation

### What does this analysis tell us?

1. **Volatility is not constant**: Treasury yield volatility varies significantly over time
2. **Volatility clusters**: High volatility periods are followed by high volatility, low by low
3. **Fat tails**: Extreme yield changes are more common than normal distribution predicts
4. **Persistence**: Volatility shocks have long-lasting effects
5. **Predictability**: GARCH models can forecast near-term volatility with reasonable accuracy

### Practical Applications

This analysis is useful for:
- **Risk management**: Understanding and forecasting interest rate risk
- **Portfolio allocation**: Adjusting fixed income exposure based on volatility forecasts
- **Option pricing**: Volatility inputs for interest rate derivatives
- **Policy analysis**: Understanding how monetary policy affects yield volatility
- **Trading strategies**: Volatility-based trading signals

---

## Methodology

### Data Source
- 10-Year Treasury Constant Maturity Rate (DGS10) from FRED
- Daily frequency
- Starting from 1990 (adjustable)

### Software & Packages
Analysis performed in R using:
- `quantmod`: Data download from FRED
- `rugarch`: GARCH model estimation
- `tidyverse`: Data manipulation and visualization
- `forecast`: Time series analysis

### Model Diagnostics
The analysis includes:
- Ljung-Box test for ARCH effects
- Information criteria (AIC, BIC) for model comparison
- ACF plots for volatility clustering
- Standardized residuals analysis

---

## Files Available for Download

After running the analysis, the following CSV files are generated:
- `Treasury_10Y_GARCH_Analysis.csv` - Full dataset with yields and volatility estimates
- `GARCH_Coefficients.csv` - Estimated model parameters
- `GARCH_Model_Comparison.csv` - Model selection criteria
- `Summary_Statistics.csv` - Descriptive statistics

---

[← Back to Home](/)
