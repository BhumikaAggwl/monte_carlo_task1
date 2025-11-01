📄 README.md
# Monte Carlo Simulation of Geometric Brownian Motion (GBM)

### 📘 Overview
This project implements a **Monte Carlo simulation** of asset price paths using the **Geometric Brownian Motion (GBM)** model — a fundamental model in quantitative finance for stochastic asset pricing.

It generates multiple simulated price paths, visualizes their evolution, and compares **simulated vs theoretical** statistics for accuracy validation.

---

### 🧮 Mathematical Model

The GBM model assumes that the asset price follows a stochastic differential equation (SDE):

\[
dS_t = \mu S_t \,dt + \sigma S_t \,dW_t
\]

where  
- \( S_t \): Asset price at time \( t \)  
- \( \mu \): Expected return (drift)  
- \( \sigma \): Volatility  
- \( W_t \): Standard Brownian motion  

Discretized version used for simulation:
\[
S_{t+\Delta t} = S_t \exp\left((\mu - 0.5\sigma^2)\Delta t + \sigma \sqrt{\Delta t} Z\right)
\]
where \( Z \sim N(0,1) \).

---

### ⚙️ Parameters Used
| Parameter | Symbol | Value | Description |
|------------|---------|--------|--------------|
| Initial Price | S₀ | 100 | Starting stock price |
| Drift | μ | 0.08 | Expected annual return |
| Volatility | σ | 0.20 | Annualized volatility |
| Time Horizon | T | 1 year | Total simulation period |
| Time Step | Δt | 1/252 | Daily intervals |
| Paths | N | 1000 | Number of Monte Carlo simulations |

---

### 🧩 Project Structure


monte-carlo-gbm-simulation/
│
├── src/
│ ├── gbm_simulation.py
│ ├── stats_analysis.py
│ └── visualization.py
│
├── notebooks/
│ └── monte_carlo_gbm.ipynb
│
├── data/
│ ├── simulated_paths.npy
│ └── final_prices.csv
│
├── plots/
│ ├── gbm_price_paths.png
│ ├── final_price_histogram.png
│ └── comparison_table.png
│
├── README.md
├── report.pdf
└── requirements.txt


---

### 💻 Installation

```bash
git clone https://github.com/<your-username>/monte-carlo-gbm-simulation.git
cd monte-carlo-gbm-simulation
pip install -r requirements.txt
```
▶️ How to Run
# Run from Jupyter Notebook
```bash
jupyter notebook notebooks/monte_carlo_gbm.ipynb
```

or directly in Python:
```bash
from src.gbm_simulation import simulate_gbm_paths
from src.stats_analysis import compute_statistics, theoretical_values, compare_theoretical_vs_simulated
from src.visualization import plot_price_paths, plot_final_price_distribution

t, paths = simulate_gbm_paths(100, 0.08, 0.20, 1, 1/252, 1000)
sim_stats = compute_statistics(paths)
theo_stats = theoretical_values(100, 0.08, 0.20, 1)
```
###📊 Outputs
File	Description
gbm_price_paths.png	Sample of 10 simulated price paths
final_price_histogram.png	Distribution of final simulated prices
comparison_table.png	Simulated vs theoretical mean/std comparison

###📈 Example Visuals
Sample GBM Price Paths
Final Price Distribution

###🧠 Insights

GBM produces log-normally distributed prices and normally distributed returns.

Monte Carlo estimates of mean and volatility closely match theoretical values (within 1–3% error).

Increasing the number of paths improves convergence to analytical expectations.

###📚 References

QuantInsti: Monte Carlo Simulation Tutorial

NPTEL Lecture: Stochastic Processes in Finance

Columbia University Notes: GBM Theory and Applications
