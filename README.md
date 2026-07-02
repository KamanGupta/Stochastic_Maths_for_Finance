# Stochastic Mathematics for Finance

Self-directed 8-week project applying stochastic processes and probability theory to quantitative finance problems — from discrete probability and Markov chains through Monte Carlo methods to continuous-time stochastic calculus. Every result is derived analytically first, then validated against an independent simulation.

**Status:** Weeks 1–3 complete · Weeks 4–8 in progress (options pricing, Greeks/delta-hedging, exotic derivatives, C++ optimization)

---

## Overview

| Week | Topic
|---|---|---|
| 1 | Discrete probability, Markov chains, random walks 
| 2 | Central Limit Theorem, Monte Carlo methods 
| 3 | Brownian motion, Itô's Lemma, SDEs
| 4 | State classification, variance reduction 
| 5 | GBM derivation, Black-Scholes pricing
| 6 | Greeks, delta-hedging backtester (NIFTY 50)
| 7 | Exotic options (Asian, barrier), advanced Monte Carlo
| 8 | C++ performance optimization

Every question pairs a closed-form derivation with a Python simulation (Monte Carlo or discrete-event) that reconciles against the theoretical result — the same derive → simulate → validate discipline used in quant research.
---

## Week 1 — Discrete Probability, Markov Chains & Random Walks

- **Portfolio loss dependence:** Modeled correlated asset defaults via conditional probability; showed a naive independence assumption underestimates joint-loss probability by **3.5×** (0.02 vs. true 0.07), directly relevant to VaR/Expected Shortfall underestimation.
- **Credit rating migration:** Built a 4-state Markov chain (Investment Grade → Speculative → Distressed → Default), classified communicating classes, and derived the stationary distribution. Simulation confirmed **23.4%** of 1,000 simulated bonds reach Default by t=100.
- **Inventory random walks:** Simulated symmetric random walks on ℤᵈ for d = 1, 2, 3, empirically confirming the theoretical recurrence/transience dichotomy — **recurrent in 1D/2D, transient in 3D** — matching analytic p-series bounds.
- **Market regime switching:** Derived the stationary distribution of a 4-state regime chain (Bull/Neutral/Bear/Crisis) via Perron-Frobenius; found a **negative long-run expected weekly return (−0.11%)** despite a positive Bull-state mean, since Bear+Crisis account for 40.3% of long-run time.

## Week 2 — Central Limit Theorem & Monte Carlo Methods

- **Empirical CLT:** Validated convergence of standardized Bernoulli sums to N(0,1) across n = 10, 50, 200 — empirical mean/variance matched theory to within 1% even at n = 200.
- **Monte Carlo integration:** Estimated ∫₀¹ e⁻ˣ² dx, confirming the theoretical **O(1/√N)** error convergence rate via a log-log error plot.
- **Monte Carlo π estimation:** Cross-validated the MC machinery geometrically — accurate to **within 0.01%** of true π at N = 100,000.
- **Monte Carlo option pricing:** Priced a European call via 100,000-path simulation and ran a volatility sensitivity sweep (σ = 0.1 → 0.5), confirming positive vega — expected payoff scales from 1.05 to 23.60 as σ increases.

## Week 3 — Brownian Motion, Itô's Lemma & Stochastic Differential Equations

- **Quadratic variation:** Proved and numerically confirmed E[Qₙ] = T for Brownian motion, empirically measuring **QV ≈ 1.0068** (theory: 1.0) vs. total variation of **~79.95**, demonstrating BM's unbounded variation.
- **Itô's Lemma → GBM:** Derived the closed-form GBM solution from first principles and quantified the cost of skipping the Itô correction term: omitting **−σ²/2** overstates a 10-year expected price by **22.1%** (245.96 vs. correct 201.38).
- **Euler-Maruyama on the OU process:** Simulated a mean-reverting SDE (short-rate model), derived its stability condition (Δt < 2/θ) and stationary distribution, and confirmed empirical variance matched the theoretical σ²/2θ = 0.0625 across 20,000 paths.

---

## Tech Stack

`Python` · `NumPy` · `Matplotlib` · `SciPy`

---

## Key Results Summary

| Result | Value |
|---|---|
| Naive independence underestimates joint-loss probability by | 3.5× |
| Random walk recurrence threshold | Recurrent (d≤2) / Transient (d≥3) |
| Monte Carlo convergence rate | O(1/√N), confirmed empirically |
| GBM pricing error from omitting Itô correction | 22.1% |
| Simulations run | 10,000–100,000 paths per experiment |
