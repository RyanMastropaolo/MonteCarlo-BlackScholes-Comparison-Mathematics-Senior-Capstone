# Black-Scholes vs. Monte Carlo (European Call Options)

This repository contains my MA 398 Senior Capstone (Fall 2025), which compares the Black–Scholes closed-form solution to a Monte Carlo (GBM) estimator for **European call options** under consistent assumptions, and demonstrates how Monte Carlo prices converge toward the Black–Scholes price as the number of simulated paths increases.

## Contents
- **SeniorCapstone_MonteCarlo_BlackScholes_Comparison.pdf**  
  Full paper: theory, assumptions, qualitative comparison, convergence discussion, and proof that GBM implies log-normal stock prices.
- **BS_MS_Calculator.ipynb**  
  Reproducible notebook that pulls market inputs, computes implied volatility, and generates **Black–Scholes vs. Monte Carlo** prices (the pipeline used to produce the comparison table in the paper).

## Reproduce the BS vs. MC Comparison Table
1. Clone the repo and install dependencies:
   ```bash
   python -m pip install numpy pandas scipy yfinance jupyter
   ```

2. Open the Notebook:
   ```bash
   jupyter notebook BS_MS_Calculator.ipynb
   ```

3. Run all cells. The notebook:
    - fetches the latest underlying price and options chain data via yfinance
    - estimates dividend yield
    - solves for implied volatility using the market option price
    - computes the Black–Scholes call price
    - runs a risk-neutral Monte Carlo GBM simulation and reports price + standard error

## Notes / Assumptions
- Pricing is done under a risk-neutral measure with drift (𝑟 − 𝑞)
- The Monte Carlo estimator uses GBM with discretized steps (default ~252 trading days/year).
- Results may vary slightly run-to-run depending on the random seed, number of paths, and live market data at execution time.

