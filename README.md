Project Overview:
Designed and implemented a portfolio optimization framework comparing Mean–Variance (Markowitz) and CVaR (95%) optimization to evaluate how different risk definitions impact portfolio weights, expected returns, volatility, and downside tail risk.the project demonstrates how variance-based optimization performs in normal markets, while CVaR-based optimization better controls losses under extreme stress scenarios, aligning with investment risk management and drawdown control objectives.

Objective:
To assess how risk metric selection (volatility vs. tail risk) influences portfolio construction and resilience by:
Minimizing portfolio variance under normal market conditions.
Minimizing expected losses in the worst 5% of scenarios (CVaR 95%).
Comparing risk–return trade-offs, allocations, and downside protection.

Methodology 
Data & Returns:
Collected daily price data for AAPL, MSFT, GOOGL, AMZN.
Computed log returns and empirical loss distributions for risk modeling.
Mean–Variance (Markowitz) Optimization.
Defined risk as portfolio variance.

Solved a convex quadratic optimization problem with constraints:
Long-only: 𝑤𝑖≥0.
Fully invested: ∑𝑤𝑖=1
Outcome:
Allocated higher weights to low-volatility, stable return assets.
Produced a diversified, volatility-efficient portfolio.


CVaR Optimization (95%)
Defined risk as Expected Shortfall (ES) in the worst 5% of return outcomes.
Formulated a linear optimization problem using:
Portfolio losses.
VaR threshold.
Slack variables to capture tail exceedances.
Outcome:
Penalized assets with fat-tailed loss distributions.
Shifted allocation toward assets with superior crash-period resilience.


Efficient Frontier Construction
Generated a risk–return frontier by blending variance-minimizing and CVaR-minimizing portfolios.
Visualized trade-offs between volatility efficiency and tail-risk protection.

Techstack:Numpy,Pandas,Matplolib,Yfinance,cvxpy.

Results

| Stock     | Markowitz Weight | CVaR Weight (95%) |                                       
| --------- | ---------------- | ----------------- | 
| **AAPL**  | **27.3%**        | **20.5%**         | 
| **GOOGL** | **9.8%**         | **6.0%**          | 
| **AMZN**  | **22.2%**        | **24.9%**         | 
| **MSFT**  | **40.7%**        | **48.6%**         |

Intepretation:

AAPL — Penalized Under Tail-Risk Optimization
Markowitz (27.3%) → CVaR 95% (20.5%): AAPL’s weight is reduced under CVaR as its downside tail losses are materially larger, despite appearing efficient under variance minimization.
Risk Interpretation: Markowitz captures AAPL’s average volatility, but CVaR correctly penalizes its left-tail risk, reallocating capital to improve crisis-period drawdown protection.

GOOGL — Largest Relative Cut Under CVaR
Markowitz (9.8%) → CVaR 95% (6.0%): GOOGL experiences the sharpest proportional reduction as CVaR identifies deep stress-period drawdowns not reflected in standard volatility.
Risk Interpretation: The asset’s asymmetric loss profile leads CVaR to aggressively de-risk exposure, highlighting limitations of variance in capturing extreme downside risk.

AMZN — Volatility vs Tail-Risk Contrast
Markowitz (22.2%) → CVaR 95% (24.9%): Despite relatively higher day-to-day volatility, AMZN receives a higher weight under CVaR as its worst-case losses are less severe than AAPL and GOOGL, making it less punitive under tail-risk optimization.
Risk Interpretation: CVaR rewards AMZN’s favorable loss distribution, demonstrating that higher variance does not necessarily imply higher tail risk, and that AMZN contributes positively to drawdown control in stress scenarios.

MSFT — Core Defensive Holding Across Risk Measures
Markowitz (40.7%) → CVaR 95% (48.6%): MSFT receives the largest weight under both frameworks, with CVaR further increasing exposure due to strong downside resilience.
Risk Interpretation: MSFT combines low variance with shallow tail losses, making it optimal for both normal-market efficiency and crisis-period capital preservation.

Future Enhancements
Incorporate Sharpe ratio, risk parity, and Black–Litterman frameworks.
Extend to multi-asset portfolios (equities, bonds, commodities, crypto).
Model transaction costs, leverage, and short-selling constraints.
Integrate Monte Carlo simulations for synthetic stress testing.
Build an interactive Streamlit dashboard for real-time risk analytics.

Key Takeaways:

Markowitz (Variance Minimization) delivers a volatility-efficient, balanced portfolio, overweighting MSFT due to stable returns, but does not explicitly control extreme downside risk, making it best suited for normal market conditions.

CVaR (95%) Optimization directly targets crisis-period losses, reducing exposure to high-drawdown assets (AAPL, GOOGL) and reallocating toward defensive, tail-resilient assets (MSFT, AMZN).

Risk–Return Trade-Off: The CVaR portfolio achieves materially lower Expected Shortfall with only a modest increase in volatility, and in this case delivers a higher expected return than the variance-minimized portfolio.

Portfolio Construction Insight: The efficient frontier highlights a smooth transition from volatility-focused to tail-risk-focused allocations, confirming that Markowitz is optimal for stable markets, while CVaR is superior for downside-risk-sensitive and stress-market environments.











