# Trees for Stock Options (Credit Default Options via Binary Puts) 

This repository contains the notebook **`TreesForStockOptions.ipynb`**, which studies the valuation of **credit default options (CDOs) on individual stocks** by exploiting their equivalence to **cash-or-nothing (binary) put options**, under both **European** and **American** exercise styles.

## Project Overview

A credit default option on a stock can be treated (under the modeling assumptions used here) as equivalent to a **binary put** that pays a fixed cash amount if the stock price falls below a default threshold at maturity (European) or at any time up to maturity (American).

To value these claims numerically, the project extends the classic **binomial tree** approach and implements five discrete-time models:

- **Cox–Ross–Rubinstein (CRR)**
- **Tian**
- **Jarrow–Rudd**
- **CRR with drift adjustment**
- **Leisen–Reimer**

## Methodology

1. **European binary options (cash-or-nothing puts)**  
   - We compute binomial-tree prices across increasing numbers of time steps.
   - We benchmark convergence against the **Black–Scholes closed-form solution** for European cash-or-nothing puts.
   - We determine step sizes (number of time steps) required to achieve stable convergence for each model.

2. **American binary options (cash-or-nothing puts)**  
   - Using the step sizes calibrated in the European case, we price the corresponding **American** binary options.
   - We compare the results across models, focusing on:
     - **Convergence speed**
     - **Stability**
     - Sensitivity to the **“shark-teeth” effect** (oscillatory/non-monotone convergence patterns often seen in lattice pricing, especially for discontinuous payoffs like binaries)

## Key Questions Explored

- Which binomial model converges fastest to the Black–Scholes benchmark for European binaries?
- How does discretization choice affect American binary option valuation?
- Which models are more robust to oscillations and instability (including shark-teeth behavior)?
- What are the practical implications for **credit risk protection** on single-name equities?

## Contents

- `TreesForStockOptions.ipynb` — main notebook containing:
  - model implementations
  - European calibration vs. Black–Scholes
  - American pricing experiments
  - comparative numerical analysis and discussion

## How to Run

1. Clone the repository.
2. Open the notebook:
   - Jupyter Notebook / JupyterLab, or
   - VS Code with the Jupyter extension.
3. Run all cells in `TreesForStockOptions.ipynb`.

## Notes

- The payoff studied is **discontinuous** (binary cash-or-nothing), which makes lattice convergence behavior especially important.
- Results may depend strongly on the choice of time steps, tree parameterization, and the model used—this is a core focus of the experiments.

## Citation / Attribution

If you use or adapt this work, consider citing the notebook/repository and referencing the implemented tree models (CRR, Tian, Jarrow–Rudd, drift-adjusted CRR, Leisen–Reimer) and the Black–Scholes benchmark for European cash-or-nothing puts.

**Authors:**  
- Diego Lozoya Morales  
- Luis Eduardo Jiménez del Muro  
- Luis Fernando Márquez Bañuelos  
- Fernando López Coronado 
