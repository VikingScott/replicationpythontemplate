***

# Quantitative Finance Replication: Project Checklist & Rubric Map

**Project:** Risk Parity / All Weather Strategy Replication
**Objective:** Replicate, Validate, and Extend the Equal Risk Contribution (ERC) strategy.

---

## 1. Specification - Hypotheses & Tests (10 pts)
> **Criteria:** Complete summary of hypotheses and tests for all components of the strategy (overall strategy theory, indicators, signal process, rules).

- [ ] **Define the Core Hypothesis:** Clearly state that "Asset allocation based on Equal Risk Contribution (ERC) produces a higher risk-adjusted return (Sharpe Ratio) and lower drawdown than market-cap weighted portfolios (e.g., 60/40)."
- [ ] **Define Component Hypotheses:**
    -   *Indicator Hypothesis:* Volatility clusters; past volatility predicts future volatility.
    -   *Signal Hypothesis:* Assets with higher volatility have lower expected risk-adjusted returns (Low Volatility Anomaly), warranting lower weights.
    -   *Strategy Hypothesis:* Diversification across non-correlated assets (Commodities, Treasuries, Stocks, Credit) reduces portfolio variance.

## 2. Constraints, Benchmarks, & Objectives (10 pts)
> **Criteria:** Complete description of constraints, benchmarks, and objectives, and how they will affect your design/implementation.

- [ ] **Objectives:** Maximize Sharpe Ratio? Minimize Drawdown? Target specific volatility (e.g., 10%)?
- [ ] **Constraints:**
    -   Long-only (No short selling).
    -   Fully Invested (Weights sum to 100%).
    -   Leverage constraints (Are we using leverage to match volatility?).
- [ ] **Benchmarks:**
    -   **Traditional:** 60% SPY / 40% IEF (Standard 60/40).
    -   **Naive:** 1/N (Equal Weight) portfolio.
    -   **Market:** S&P 500 (SPY) alone.

## 3. Data Description (10 pts)
> **Criteria:** Fully described Data with source citation and data dictionary. Code/text describing loading, cleaning, and preparing.

- [ ] **Data Sources:** Cite Yahoo Finance (yfinance) or other sources used.
- [ ] **Data Dictionary:** List tickers (SPY, IEF, GSG, LQD/HYG) and what they represent.
- [ ] **Cleaning Process:**
    -   Describe how you handled missing data (fill forward?).
    -   Describe how you handled different start dates (truncation?).
    -   **Reference Code:** `01_data_engineering/check_data_quality.py`.
- [ ] **Visual Proof:** Show the "Data Quality" plots (validity checks).

## 4. Indicators (10 pts)
> **Criteria:** Indicator detailed description, citations, implementation, and *worked tests (separate from a full backtest)*.

*Note: In Risk Parity, your "Indicator" is **Volatility** (Standard Deviation).*

- [ ] **Description:** Define how you calculate volatility (e.g., Rolling standard deviation with $N$-day lookback).
- [ ] **Statistical Testing (Crucial):** Do not just show the strategy result. Test the indicator itself.
    -   *Test:* Show Volatility Clustering (Autocorrelation of absolute returns).
    -   *Test:* Stationarity tests (ADF test) on returns vs prices.
- [ ] **Reference Code:** `02_simple_component_tests/test_indicator_vol_clustering.py`.

## 5. Signals (10 pts)
> **Criteria:** Describe signal process, test signal process *separately from the overall strategy* including forecast error/loss.

*Note: In Risk Parity, your "Signal" is the **Inverse Volatility Weight**.*

- [ ] **Signal Logic:** $w_i = \frac{1/\sigma_i}{\sum (1/\sigma_j)}$.
- [ ] **Predictive Test:** Does the signal work?
    -   *Test:* Check the correlation between "Predicted Risk Contribution" and "Realized Risk Contribution".
    -   *Error Metric:* Calculate the **Risk Parity Error** (Sum of squared differences between asset risk contributions). Ideally, this should be near zero.
- [ ] **Reference Code:** `02_simple_component_tests/test_signal_risk_contribution.py`.

## 6. Rules (10 pts)
> **Criteria:** Describe rules for enter/exit, rationale. Test with/without optional rules (stops, rebalancing).

- [ ] **Rebalancing Rule:** Monthly vs. Daily? (Explain why monthly is chosen to reduce turnover).
- [ ] **Execution:** Market on Close? Next day Open?
- [ ] **Transaction Costs:** Explicitly mention if you included slippage/fees (e.g., 10bps per trade).
- [ ] **Comparison:** Show performance *Gross* vs. *Net* of fees (if available in your extension).

## 7. Parameter Search (10 pts)
> **Criteria:** Describe free parameters, search process, and optimization methodology.

- [ ] **Identify Parameters:**
    -   Lookback Window for Volatility (e.g., 3 months, 6 months, 12 months).
    -   Rebalancing Frequency.
- [ ] **Optimization Method:** Grid Search (testing a range of lookback windows).
- [ ] **Reference Code:** `04_parameter_analysis`.

## 8. Walk Forward / Sensitivity Analysis (10 pts)
> **Criteria:** Apply walk forward analysis, discuss objective function and impact on parameter choice.

*Note: Since Risk Parity is often a "fixed rule" rather than a trained ML model, "Sensitivity Analysis" serves this purpose.*

- [ ] **Rolling Analysis:** Show **Rolling Sharpe Ratio** over time. Does the strategy only work in the 2010s bull market? Or did it work in 2008?
- [ ] **Parameter Sensitivity:** Show the Heatmap of "Lookback Window vs. Sharpe Ratio".
    -   *Goal:* Prove that the strategy is robust (stable colors on heatmap), not just lucky with one specific parameter.
- [ ] **Sub-period Analysis:** Break down performance by "Crisis", "Recovery", "Inflation" (2022).

## 9. Assess Overfitting (10 pts)
> **Criteria:** Assess probability of overfitting. In/Out of sample performance, degradation.

- [ ] **Discussion:** Argue that ERC is less prone to overfitting than Mean-Variance Optimization because it does not estimate *Returns* (which are noisy), only *Risks* (which are stable).
- [ ] **Degradation Check:** Compare the strategy's performance in the training period (if you had one) vs. the validation period.
- [ ] **Visual:** Use the Sensitivity Heatmap to argue for parameter stability.

## 10. Extensions & Conclusions (10 pts)
> **Criteria:** Extend analysis with recent data, new techniques, or sophisticated models. Conclusions and future work.

- [ ] **Extension 1 (Trend):** Applying a Trend Filter (Moving Average Rule) to avoid assets in a downtrend (e.g., 2022 Bonds).
- [ ] **Extension 2 (Real World):** Tax adjustments or Transaction Cost analysis.
- [ ] **Conclusion:** Summarize findings. Did you replicate the paper? Did it hold up in 2022?
- [ ] **Future Research:** Suggest adding Crypto, using GARCH for volatility, or Dynamic Conditional Correlation (DCC).

---

## Technical Appendix (Required for "Full Marks")

- [ ] **Bibliography:** `references.bib` file populated with the original Peterson paper + Data sources.
- [ ] **Code Quality:** Code snippets in the report should be readable.
- [ ] **Formatting:** Use Quarto to generate a clean PDF with proper Section Headers matching the Rubric.