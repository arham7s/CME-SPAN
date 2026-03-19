# CME SPAN Margin Model — Portfolio Risk & Margin Engine

This project is a **complete educational implementation of the CME SPAN (Standard Portfolio Analysis of Risk)** margin methodology, designed to help users understand how exchanges calculate **portfolio-level margin requirements for futures and options trading**.

The model simulates realistic risk scenarios, computes worst-case losses, applies spread benefits, and produces final margin requirements for a **multi-asset derivatives portfolio**.

This repository is ideal for:

- Students  
- Risk management interns  
- Quantitative finance learners  
- Derivatives traders  

who want to build strong intuition about **exchange margining systems from first principles**.

**Access to official CME methodology PDF:**  
https://www.cmegroup.com/clearing/files/span-methodology.pdf

---

## Project Overview

Financial exchanges require traders to maintain **margin deposits** to ensure that potential losses can be covered during adverse market movements.

Unlike traditional margin systems that calculate risk **contract-by-contract**, the SPAN framework evaluates **entire portfolios holistically**, recognizing:

- Hedging benefits  
- Product correlations  
- Non-linear option risk  

This project recreates that logic step-by-step through a modular architecture including:

- Scenario-based risk simulation  
- Worst-case loss (**Scan Risk**) computation  
- Calendar spread credits  
- Inter-commodity spread credits  
- Portfolio margin aggregation  
- Options pricing using **Black-76 model**  
- Final margin reporting and **risk waterfall analysis**

The goal is to provide a **transparent and intuitive learning framework** for understanding real-world derivatives risk management systems.

---

## Key Features

- Portfolio-level margin calculation (not per contract)
- Simulation of **16 market scenarios** including price shocks and volatility shifts
- Recognition of **hedged positions through spread credits**
- Futures risk engine with scenario P&L logic
- Options risk support using **Black-76 pricing model**
- Short Option Minimum (**SOM**) safety floor
- Margin allocation and credit rebalancing algorithm

### Structured Output Reports

- Scenario risk summary  
- Spread credit breakdown  
- Position-wise margin  
- Margin waterfall (**Gross Risk → Net Margin**)  

---

## Model Architecture

The SPAN engine is implemented using a **6-module pipeline**.

### Module 1 — Data Layer
Defines:

- Contract specifications  
- Portfolio positions  
- SPAN risk parameters  
- Scenario grid  

### Module 2 — Risk Array Engine
- Simulates scenario P&L for each contract  
- Computes **Scan Risk (worst-case loss)**  

### Module 3 — Spreading Credits
Applies margin reductions for:

- Calendar spreads (same product, different expiry)
- Inter-commodity spreads (correlated products)

### Module 4 — Margin Aggregator
- Allocates spread credits to positions  
- Computes **final SPAN margin per contract**

### Module 5 — Output Layer
- Generates structured reports  
- Produces portfolio margin summaries  

### Module 6 — Options Support
Extends the model to handle options using:

- Black-76 pricing  
- Volatility shocks  
- Greek sensitivities (Delta, Gamma, Vega, Theta)
- Short Option Minimum (**SOM**) logic  

---

## Example Portfolio Covered

The sample implementation demonstrates margin computation for a diversified derivatives portfolio including:

- Crude Oil futures calendar spreads  
- Natural Gas correlated exposure  
- Gold futures diversification  
- Short Call and Long Put option positions  

The model illustrates how **spread recognition significantly reduces margin requirements** by capturing **true net portfolio risk instead of gross exposure**.

---

## How to Run

### Requirements

- Python 3.8+
- pandas
- numpy
- scipy (required for options module)

### Run Futures-Only Model

```python
results = run_span_model()
