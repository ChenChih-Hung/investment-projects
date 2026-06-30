## Results

### CAPE vs 5-Year Forward Return

![CAPE vs 5Y Return](CAPE_vs_5Y_Return.png)

# CAPE-Based Asset Allocation Strategy

## Overview

This project develops and backtests a dynamic asset allocation strategy using the Shiller CAPE ratio and 103 years of historical S&P Composite market data (1922–2024). The strategy dynamically adjusts portfolio allocations between equities and Treasury bills based on market valuation and compares its performance against a traditional 60/40 benchmark.

## Objectives

- Evaluate CAPE's predictive power for future equity returns.
- Develop a valuation-based asset allocation strategy.
- Compare strategy performance with a traditional 60/40 portfolio.

## Methodology

2.1 Data and CAPE Construction
Real CAPE in a given year is computed as the inflation-adjusted S&P Composite price index divided by the trailing ten-year average of inflation-adjusted earnings. Real and nominal annual price returns, along with forward 1-year and forward 5-year returns (both nominal and real), are derived from the price, dividend, and CPI series to evaluate the predictive relationship between valuation and subsequent performance.

2.2 Regression Analysis
Four single-variable OLS regressions were run, regressing forward 1-year and forward 5-year returns (nominal and real) on the prior year's real CAPE ratio. In every specification the CAPE coefficient is negative, consistent with the mean-reversion hypothesis that higher valuations are associated with lower subsequent returns.

For 1-year horizons, the relationship is weak: the real-return regression has an R² of roughly 3% and the CAPE coefficient is not statistically significant at the 5% level (p ≈ 0.085), implying that short-term returns are dominated by noise rather than valuation. For 5-year horizons, the relationship strengthens considerably: R² rises to roughly 13% (real) and 25% (nominal), with CAPE coefficients significant at well beyond the 1% level. This is consistent with the view that valuation-driven mean reversion operates over a multi-year horizon rather than from one year to the next.

2.3 Dynamic Allocation Strategy
Using the prior year's real CAPE as the signal, the portfolio is rebalanced annually according to three valuation bands:
•	CAPE below 15 (undervalued): 80% S&P 500 / 20% Treasury bills
•	CAPE between 15 and 25 (fair value): 60% S&P 500 / 40% Treasury bills
•	CAPE above 25 (overvalued): 30% S&P 500 / 70% Treasury bills
This dynamic strategy is compared against a static 60/40 benchmark held constant across the full sample period.

3. Results

3.1 Regression Results
As detailed in Section 2.2, real CAPE shows a statistically weak relationship with forward 1-year returns (R² ≈ 3–6%, not significant at 5%) but a markedly stronger and statistically significant relationship with forward 5-year returns (R² ≈ 13–25%). The full regression output is summarized in the Appendix.

3.2 Allocation Rule
The prior year's real CAPE is mapped to a portfolio weight each year according to the three-tier rule below:
Real CAPE Range	S&P 500 Weight	Treasury Bill Weight
Below 15 (Undervalued)	80%	20%
15 – 25 (Fair Value)	60%	40%
Above 25 (Overvalued)	30%	70%

3.3 Portfolio Growth
Applying the allocation rule annually from 1933 through 2024 produces the cumulative growth path below, plotted on a log scale against the static 60/40 benchmark. A hypothetical $1 invested in 1933 grew to approximately $3,130 under the CAPE-based strategy, versus approximately $1,918 under the static 60/40 benchmark.
 
3.4 Performance Metrics
Summary risk and return statistics over the full 1933–2024 sample are shown below. The CAPE-based strategy delivered a higher compound annual growth rate, at the cost of slightly higher volatility and a marginally lower Sharpe ratio; maximum drawdown was modestly shallower than the static benchmark.
Metric	CAPE Strategy	60/40 Benchmark
CAGR (1933–2024)	9.14%	8.56%
Annualized Volatility	11.61%	10.56%
Sharpe Ratio (rf = 0)	0.84	0.86
Maximum Drawdown	-21.4%	-22.0%
Growth of $1	$3,130	$1,918
Note: Sharpe ratios are computed using annual returns with a 0% risk-free rate assumption for simplicity; using actual contemporaneous Treasury bill yields as the risk-free rate would modestly adjust both figures but would not change their relative ordering materially.

4. Conclusion
The evidence supports the core premise of valuation-based asset allocation: CAPE has limited power to predict next year's return but meaningfully more power to predict returns over a five-year horizon, where the regression relationship is both economically and statistically significant. Translating this signal into a simple three-tier rebalancing rule improved compound growth relative to a static 60/40 portfolio over the 1933–2024 sample (9.14% vs. 8.56% CAGR), though with slightly higher volatility and a marginally lower Sharpe ratio (0.84 vs. 0.86), and a comparably sized maximum drawdown.
The strategy's limitations are worth noting. It relies on a single valuation metric, ignores transaction costs and taxes, uses fixed (rather than continuous) allocation bands, assumes annual rebalancing with no implementation lag, and is tested on overlapping historical data that may not fully capture structural shifts in market valuation over the past century. Extensions could include continuous (rather than discrete) position sizing as a function of CAPE, the addition of complementary signals such as momentum or interest-rate trends, and out-of-sample or rolling-window validation to test robustness.
 
## Tools

- Microsoft Excel
- Financial Modeling
- Regression Analysis
- Investment Research

## Key Findings

- CAPE demonstrates stronger predictive power for 5-year returns than for 1-year returns.
- The CAPE-based strategy modestly outperformed the traditional 60/40 benchmark over the historical sample.

## Project Files

- Investment Research Report (PDF)
- Excel Financial Model (.xlsx)
