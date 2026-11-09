# Black-Scholes-Merton Pricing and Greeks Sensitivity Analysis

**Timeline:** 2025

Try the interactive Greeks explorer from this project on my [portfolio site](https://stevenghabyous.github.io/#options).

A from-scratch implementation of the Black-Scholes-Merton model for European options on dividend-paying stocks, with analytical Greeks, numerical verification, and sensitivity analysis.

## Highlights

- **Pricing:** BSM call and put prices with a continuous dividend yield
- **Greeks:** delta, gamma, vega, theta, and rho derived analytically, also reported in trader units (theta per day, vega and rho per 1 point)
- **Verification:** put-call parity holds to machine precision, and every Greek matches a finite-difference derivative of the price to within 1e-7
- **Sensitivity analysis:** how each Greek changes with moneyness, time to expiry, and volatility

## Example: 30-day at-the-money SPY option

Inputs: S = K = 560, 30 days to expiry, r = 4.5%, q = 1.2%, sigma = 18%

| | Call | Put |
|---|---|---|
| Price | $12.27 | $10.76 |
| Delta | 0.531 | -0.468 |
| Gamma | 0.0137 | 0.0137 |
| Vega (per 1 vol point) | 0.638 | 0.638 |
| Theta (per day) | -0.217 | -0.166 |

As expiry approaches, at-the-money gamma rises from 0.0097 (60 days) to 0.0338 (5 days), and daily time decay roughly triples.

## Revision note

An earlier version pulled live inputs and used the first strike in the option chain, a deep in-the-money contract with an unreliable implied volatility. It also used Yahoo's dividend yield in percentage form (1.19) as if it were a decimal, which treated it as a 119% yield and produced a positive theta for a long call. This version uses fixed, representative inputs for reproducibility, adds verification checks, and includes a corrected optional function for live data.

## Next steps

- Simulate discrete delta hedging to measure hedging error versus rebalancing frequency
- Compare model prices with market prices across strikes to study the volatility smile

## Tools

Python, NumPy, SciPy, Matplotlib (optional: yfinance)

---

**Steven Ghabyous** | [Portfolio](https://stevenghabyous.github.io) | [GitHub](https://github.com/stevenghabyous) | [LinkedIn](https://linkedin.com/in/steven-ghabyous) | [Email](mailto:steven.ghabyous2005@gmail.com)
