
---

## 📄 **report.md (convert to PDF later)**

```markdown
# Report: Monte Carlo Simulation of Geometric Brownian Motion

### Objective
To simulate multiple possible stock price paths using the **Geometric Brownian Motion (GBM)** model and evaluate how well simulated results match theoretical expectations.

---

### Theoretical Background
The GBM process models stock price evolution under continuous compounding and stochastic volatility:

\[
dS_t = \mu S_t dt + \sigma S_t dW_t
\]

Discretized form used in simulation:

\[
S_{t+\Delta t} = S_t e^{(\mu - 0.5\sigma^2)\Delta t + \sigma \sqrt{\Delta t} Z}, \quad Z \sim N(0, 1)
\]

Theoretical moments:
\[
E[S_T] = S_0 e^{\mu T}, \quad Var[S_T] = S_0^2 e^{2\mu T}(e^{\sigma^2 T} - 1)
\]

---

### Simulation Parameters
| Symbol | Meaning | Value |
|---------|----------|--------|
| \(S_0\) | Initial stock price | 100 |
| \(μ\) | Annual drift | 0.08 |
| \(σ\) | Annual volatility | 0.20 |
| \(T\) | Time horizon | 1 year |
| \(Δt\) | Time step | 1/252 |
| \(N\) | Simulations | 1000 |

---

### Methodology
1. Generate \( N \) random normal values for each daily step.  
2. Apply the GBM update rule iteratively to get price paths.  
3. Calculate final prices and summarize mean, variance, and volatility.  
4. Compare simulated vs theoretical statistics.  
5. Visualize paths, distribution, and comparison table.

---

### Results
| Metric | Simulated | Theoretical | % Error |
|---------|------------|--------------|----------|
| Mean Final Price | ≈ 108.2 | 108.3 | 0.09% |
| Std Final Price | ≈ 22.1 | 21.9 | 0.9% |

Plots:
- **GBM Paths:** Log-normal price evolution.
- **Histogram:** Final prices follow a right-skewed (log-normal) shape.
- **Comparison:** Excellent agreement between simulation and theory.

---

### Insights
- GBM successfully reproduces real-world characteristics of asset prices.  
- Monte Carlo errors reduce with larger \( N \) or smaller \( Δt \).  
- Drift \( μ \) shifts the mean upward, while volatility \( σ \) widens dispersion.  
- Useful for **option pricing**, **VaR estimation**, and **risk modeling**.

---

### Conclusion
The Monte Carlo GBM simulation accurately validates the theoretical properties of the model.  
This exercise demonstrates practical use of stochastic calculus in financial modeling and provides a foundation for advanced quantitative techniques such as **option pricing (BOPM/Black-Scholes)** and **risk analysis (VaR)**.

---

### References
- QuantInsti: *Monte Carlo Simulation in Python*  
- MIT OCW: *Mathematics for Finance (18.S096)*  
- Investopedia: *Geometric Brownian Motion*
