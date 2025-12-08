Objective:
Built a portfolio optimization framework using Mean–Variance (Markowitz) and CVaR (95%) tail-risk optimization to compare how risk definitions affect portfolio weights, expected returns, and downside risk. The goal is to identify how portfolios behave under normal conditions (variance-based) vs. extreme market stress (CVaR-based).

Process (How the weights were allocated)

Collected daily price data for AAPL, MSFT, GOOGL, AMZN and computed daily returns.

Markowitz Optimization:
Defined risk as portfolio variance and solved a convex optimization problem to minimize volatility under the constraints:
weights ≥ 0
sum of weights = 1
This allocated more weight to stocks with lower variance and stable return profiles, resulting in a diversified but risk-averse allocation.

CVaR Optimization (95%):
Defined risk as expected tail loss in the worst 5% return scenarios.
Built a linear optimization model using portfolio losses, VaR, and slack variables.
CVaR penalized assets with heavy downside tails, shifting more weight toward stocks with strong crash performance and away from those with large tail risks.

Generated the efficient frontier by blending Markowitz and CVaR portfolios to visualize the risk–return trade-off.

Results

| Stock     | Markowitz Weight | CVaR Weight (95%) | Interpretation                                                                     |
| --------- | ---------------- | ----------------- | ---------------------------------------------------------------------------------- |
| **AAPL**  | **27.3%**        | **20.5%**         | CVaR reduces exposure due to higher downside tail risk.                            |
| **GOOGL** | **9.8%**         | **6.0%**          | Significant cut under CVaR because of heavier drawdowns in stress periods.         |
| **AMZN**  | **22.2%**        | **24.9%**         | Slight increase, indicating better tail-risk behavior than AAPL/GOOGL.             |
| **MSFT**  | **40.7%**        | **48.6%**         | Largest allocation under both; CVaR favors MSFT due to strong downside resilience. |

Summary
1️.Markowitz Portfolio (Variance Minimization):
Focuses on lowering overall volatility.
Produces a more balanced allocation, but still overweight MSFT because of its stability.
Result: low-risk, stable portfolio, but may underperform in extreme scenarios.

2️.CVaR Portfolio (Tail-Risk Minimization):
Optimizes for worst-case 5% market outcomes.
Cuts exposure to assets with larger drawdowns (GOOGL, AAPL).
Increases weight in defensive performers (MSFT, AMZN).
Result: higher expected return with slightly higher volatility but significantly reduced tail risk.

3️.Risk–Return Profile Comparison:
CVaR portfolio delivers higher expected return with only a small increase in volatility.
The efficient frontier shows a smooth transition from variance-focused to tail-risk-focused portfolios.
Markowitz = optimal for normal markets.
CVaR = optimal for crisis markets.

Future Enhancements:
Add Sharpe ratio optimization, risk-parity, and Black–Litterman models for advanced portfolio construction.
Extend analysis to a broader multi-asset universe (equities, bonds, commodities, crypto) to create a more realistic efficient frontier.
Integrate transaction costs, short-selling constraints, and leverage scenarios.
Build a Streamlit dashboard for interactive visualization of weights, risk metrics, and efficient frontiers.
Incorporate Monte Carlo simulation to analyze portfolio performance under synthetic stress scenarios.
