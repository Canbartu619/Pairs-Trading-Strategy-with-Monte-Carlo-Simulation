# 📊 Pairs Trading Strategy with Monte Carlo Simulation

## Overview
This project explores the mechanics of **Statistical Arbitrage (Pairs Trading)** using **Monte Carlo simulations**. It analyzes how noise, correlation breakdown, and volatility affect mean-reversion strategies in a controlled environment.

Rather than focusing on a single historical backtest, the goal is to study **algorithmic robustness under stochastic price dynamics**.

---

## 🔬 Motivation
Pairs trading is often presented theoretically as a risk-free arbitrage. However, real financial data is plagued by:
* **Non-Stationarity:** Correlations are unstable over time.
* **Noise:** High variance often masks the true signal.

This project was built to validate the trading logic by:
- Simulating a perfectly cointegrated environment to isolate strategy performance.
- Analyzing how the algorithm reacts to "Mean Reversion" speed.
- Demonstrating why **Model Validation** via simulation is crucial before deployment.

---

## 🛠️ Methodology
The project follows a Quantitative Research workflow:

1.  **Synthetic Data Generation:**
    Assets are simulated using **Geometric Brownian Motion** and a cointegrated spread model:
    $$Y_t = \alpha + \beta X_t + \epsilon_t$$
    (Where $\epsilon_t$ is stationary Gaussian noise)

2.  **Statistical Validation:**
    The relationship is verified using the **Engle-Granger Two-Step Method** (P-Value < 0.05 confirmed).

3.  **Signal Generation (Z-Score):**
    Trading signals are triggered based on the standardized spread:
    $$Z = \frac{S_t - \mu}{\sigma}$$
    (Long/Short signals generated at $\pm 2.0$ thresholds)
    
---

## 📊 Example Outputs

### 1. Simulated Paired Assets
*Demonstrating the "Random Walk" nature of individual assets.*
![Simulated Assets](images/Simulated_Assets.png)

### 2. Trading Signals (Z-Score Analysis)
*Visualizing the mean-reverting spread and algorithmic entry/exit points.*
![Trading Signals](images/Pairs_Trading_Signals.png)

---

## 💡 Key Takeaways
- **Proof of Concept:** The algorithm successfully captures mean-reversion opportunities in a mathematically controlled environment.
- **Sensitivity:** Strategy performance is highly sensitive to the standard deviation window (Z-Score threshold).
- **Validation:** Monte Carlo analysis provides deeper insight into "Model Risk" than single-path historical backtests.

---

## 💻 Tools
* **Python:** Core Logic
* **NumPy:** Monte Carlo Simulation
* **Statsmodels:** Cointegration Testing (`coint`)
* **Pandas & Matplotlib:** Data Handling & Visualization

---

## ⚠️ Limitations
- **Transaction Costs:** Slippage and commission fees are not modeled.
- **Fixed Parameters:** The lookback period for Z-Score is static across the simulation.
- **Gaussian Assumption:** Returns are assumed to be normally distributed (unlike heavy-tailed real markets).

---

## 📜 Disclaimer
For educational and research purposes only. Not financial advice.

*This project complements my work on **Robust Portfolio Optimization**, exploring inverse problems under noisy financial data.*

---

**Author:** Can Bartu Aydınlık  
*Applied Mathematics • Quantitative Finance*
