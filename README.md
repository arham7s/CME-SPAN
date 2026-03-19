**CME SPAN Margin Model — Portfolio Risk & Margin Engine**

This project is a complete educational implementation of the CME SPAN (Standard Portfolio Analysis of Risk) margin methodology, designed to help users understand how exchanges calculate portfolio-level margin requirements for futures and options trading.

The model simulates realistic risk scenarios, computes worst-case losses, applies spread benefits, and produces final margin requirements for a multi-asset derivatives portfolio.

This repository is ideal for students, risk management interns, quant learners, and derivatives traders who want to build strong intuition about exchange margining systems from first principles.

ACCESS TO THE METHODOLOGY PDF: https://www.cmegroup.com/clearing/files/span-methodology.pdf

⸻

Project Overview

Financial exchanges require traders to maintain margin deposits to ensure that potential losses can be covered during adverse market movements.

Unlike traditional margin systems that calculate risk contract-by-contract, the SPAN framework evaluates entire portfolios holistically, recognizing hedges, correlations, and option nonlinearities.

This project recreates that logic step-by-step through a modular architecture including:
	•	Scenario-based risk simulation
	•	Worst-case loss (Scan Risk) computation
	•	Calendar spread and inter-commodity spread credits
	•	Portfolio margin aggregation
	•	Options pricing using Black-76
	•	Final margin reporting and risk waterfall

The goal is to provide a transparent and intuitive learning framework for understanding real-world derivatives risk management systems.  ￼

⸻

Key Features
	•	Portfolio-level margin calculation (not per contract)
	•	Simulation of 16 market scenarios including price shocks and volatility shifts
	•	Recognition of hedged positions through spread credits
	•	Futures risk engine with scenario P&L logic
	•	Options risk support using Black-76 pricing model
	•	Short Option Minimum (SOM) safety floor
	•	Margin allocation and credit rebalancing algorithm
	•	Structured output reports including:
	•	Scenario risk summary
	•	Spread credit breakdown
	•	Position-wise margin
	•	Margin waterfall (gross → net)

⸻

Model Architecture

The SPAN engine is implemented using a 6-module pipeline:

Module 1 — Data Layer

Defines contracts, portfolio positions, and SPAN risk parameters.

Module 2 — Risk Array Engine

Simulates scenario P&L for each contract and computes Scan Risk (worst-case loss).

Module 3 — Spreading Credits

Applies margin reductions for:
	•	Calendar spreads (same product, different expiry)
	•	Inter-commodity spreads (correlated products)

Module 4 — Margin Aggregator

Allocates spread credits to positions and computes final SPAN margin per contract.

Module 5 — Output Layer

Generates structured reports and portfolio summaries.

Module 6 — Options Support

Extends the model to handle options using:
	•	Black-76 pricing
	•	Volatility shocks
	•	Greek sensitivities
	•	Short Option Minimum logic

⸻

Example Portfolio Covered

The sample implementation demonstrates margin computation for a diversified derivatives portfolio including:
	•	Crude Oil futures calendar spreads
	•	Natural Gas correlated exposure
	•	Gold futures diversification
	•	Short call and long put option positions

The model shows how spread recognition can significantly reduce total margin requirements by capturing true net portfolio risk instead of gross exposure.  ￼

⸻

How to Run

Requirements
	•	Python 3.8+
	•	pandas
	•	numpy
	•	scipy (required for options module)

Run Futures-Only Model

results = run_span_model()

Run Full Model (Futures + Options)

results = run_span_model_v2()

Outputs include:
	•	Position-wise margin table
	•	Spread credit breakdown
	•	Scenario risk summary
	•	Total portfolio margin

⸻

Learning Objectives

This project helps users understand:
	•	How exchanges protect market stability through margining
	•	Scenario-based risk measurement
	•	Hedging benefits in derivatives portfolios
	•	Non-linear option risk dynamics
	•	Practical quantitative risk engineering concepts

⸻

Limitations

This is a simplified educational implementation and differs from real exchange SPAN systems in several ways:
	•	Fixed scenario grid (real exchanges update parameters daily)
	•	Simplified volatility assumptions
	•	No cross-exchange margin offsets
	•	No delivery risk adjustments near expiry
	•	Flat inter-commodity credit structure

However, the core mechanics accurately reflect how portfolio margin logic works conceptually.  ￼

⸻

Future Improvements
	•	Dynamic volatility surface integration
	•	Historical calibration of scan ranges
	•	Multi-currency margining
	•	Stress testing framework
	•	SPAN 2 style granular scenario grid
	•	Real exchange parameter file ingestion

⸻

Author

Built as a derivatives risk analytics learning project to develop intuition about exchange margin systems and portfolio risk modeling.

⸻

