# Semantic Arbitrage: Short-Horizon Sentiment Decay & Cross-Sectional Alpha

[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)[![PyTorch](https://img.shields.io/badge/PyTorch-GPU%20Accelerated-ee4c2c.svg)](https://pytorch.org/)[![Model](https://img.shields.io/badge/Model-FinBERT-yellow.svg)](https://huggingface.co/ProsusAI/finbert)[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

> **Project AlphaQuest**: A Multi-Scale NLP–Finance Integration Study on Large-Cap U.S. Equities.

## 📈 Executive Summary

This repository hosts a full-stack quantitative research pipeline that integrates **Financial News NLP**, **Analyst Sentiment Extraction**, and **Market Price Dynamics**. 

Unlike traditional sentiment analysis relying on simple lexicons (e.g., TextBlob), this study employs **FinBERT** (a Transformer-based LLM) to capture nuanced semantic signals. We rigorously test the predictive power of these signals on the "Magnificent Seven" and other large-cap U.S. technology stocks.

![equity_curve](./assets/equity_curve-1766676174016-1.svg)

### 🏆 Key Performance Indicators (2020-2025)

| Metric | Strategy (Smart Beta) | Benchmark (Sector Avg) |
| :--- | :--- | :--- |
| **Total Return** | **728.20%** | 387.82% |
| **Alpha (Excess Return)** | **+340.37%** | - |
| **Active Ratio** | **17.40%** | N/A |
| **Pure Alpha Multiplier** | **1.71x** | 1.0x |

---

## 🧠 Core Philosophy: The "Sniper" Approach

Our research reveals that Analyst Sentiment is a **sparse but potent** signal. The strategy does not trade frequently; it waits for high-conviction moments.

1.  **The Efficiency Paradox**: Alpha decays rapidly. Our term-structure analysis proves that a **4-Day Holding Period** is mathematically optimal. Holding longer (e.g., 7 days) exposes the portfolio to mean reversion and beta drift.
2.  **The Shoulder Alpha**: Contrary to intuition, the extreme "Top 10%" sentiment bucket often suffers from overcrowding. The "Sweet Spot" for Alpha lies in the **90-80% decile** (Secondary Conviction).
3.  **High Efficiency**: The strategy is active only **17.4%** of the time. For the remaining 82.6%, it passively tracks the benchmark, minimizing transaction costs and noise exposure.

---

## 🛠️ Research Pipeline

The project is structured into modular, mathematically grounded stages:

1.  **Data Engineering**: strict universe selection (US Tech Giants) and UTC timestamp normalization.
2.  **NLP Core**: GPU-accelerated **FinBERT** inference for institutional-grade sentiment scoring ($S \in [-1, 1]$).
3.  **Network Dynamics**: Construction of Kendall correlation graphs to visualize systemic risk.
4.  **Signal Visualization**: Temporal Heatmaps, Z-Score Anomaly Detection, and "Confidence Chain" Mosaics.
5.  **Vectorized Backtesting**: A high-performance simulation engine implementing the **Active Overlay Strategy**.

---

## 📊 Visualizations & Evidence

### 1. The Cumulative Equity Curve
*The strategy (Red) vs. Benchmark (Gray). Note the "Alpha Explosion" post-2020.*

![equity_curve](./assets/equity_curve-1766676179163-3.svg)

### 2. Performance Attribution (The "Report Card")
*Deconstructing the returns into Beta (Market) and Pure Alpha (Skill).*

![attribution](./assets/attribution-1766676184251-5.svg)

### 3. Signal Decay Analysis
*Why we exit at Day 4: The Alpha Spread (Green) collapses and turns negative by Day 8.*

| Holding Period | Top 10% Return | Bottom 10% Return | **Spread (Alpha)** |
| :--- | :--- | :--- | :--- |
| **Day 4 (Peak)** | **1.33%** | **0.77%** | **+0.56%** (Max Efficiency) |
| **Day 8 (Reversion)** | 2.42% | 2.83% | **-0.41%** (Alpha Loss) |

---

## 💻 Installation & Usage

### Prerequisites
* Python 3.10+
* CUDA-enabled GPU (Recommended for BERT inference)

### Setup
```bash
git clone [https://github.com/Republic/Semantic-Arbitrage.git](https://github.com/Republic/Semantic-Arbitrage.git)
cd Semantic-Arbitrage
```