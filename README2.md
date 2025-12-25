# Semantic Arbitrage: Short-Horizon Sentiment Decay & Cross-Sectional Alpha

[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)[![PyTorch](https://img.shields.io/badge/PyTorch-GPU%20Accelerated-ee4c2c.svg)](https://pytorch.org/)[![Model](https://img.shields.io/badge/Model-FinBERT-yellow.svg)](https://huggingface.co/ProsusAI/finbert)[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

> **Project AlphaQuest**: An institutional-grade quantitative pipeline investigating the transmission of analyst sentiment into asset prices across Large-Cap U.S. Equities.

![equity_curve](./assets/equity_curve-1766676174016-1.svg)

## 📈 Executive Summary

**We quantify the invisible.** This repository hosts a full-stack research pipeline that integrates **Financial News NLP**, **Network Dynamics**, and **Vectorized Backtesting** to capture short-term price inefficiencies driven by analyst sentiment.

Unlike traditional approaches relying on crude lexicons (e.g., TextBlob), this project deploys **FinBERT**—a Transformer-based LLM fine-tuned on financial corpora—to extract high-fidelity semantic signals ($S \in [-1, 1]$).

Our research uncovers the **"Efficiency Paradox"**: Sentiment Alpha is potent but ephemeral. By implementing a **"Sniper" methodology** (active only 17.4% of the time) with a mathematically optimal **4-Day Holding Period**, the strategy systematically harvests excess returns before mean reversion sets in.

### 🏆 Performance Report Card (2020-2025)

*Out-of-sample backtesting results on the "Magnificent Seven" & US Tech Universe.*

| **Metric**       | **Strategy (AlphaQuest)** | **Benchmark (Sector Avg)** | **Delta**         |
| ---------------- | ------------------------- | -------------------------- | ----------------- |
| **Total Return** | **728.20%**               | 387.82%                    | **+340.38%**      |
| **Active Ratio** | **17.40%**                | 100%                       | *High Efficiency* |
| **Pure Alpha**   | **1.71x**                 | 1.0x                       | *Skill > Luck*    |
| **Max Drawdown** | **-27.96%**               | -31.84%                    | *Risk Mitigation* |

------

## 🧠 The "Sniper" Philosophy: Why It Works

Most sentiment strategies fail because they over-trade. Our analysis proves that Alpha is not a continuous stream, but a sparse series of "shocks."

### 1. The Efficiency Paradox (Time)

Alpha decays rapidly. Our Term Structure Analysis reveals a critical inflection point:

- **Day 1-4:** The market digests the news. Information Ratio is maximized.
- **Day 5-8:** The signal fades. Returns become dominated by Beta (market noise).
- **Result:** A **4-Day Holding Period** is strictly enforced. Holding to Day 7 invites mean reversion and degrades the Sharpe Ratio.

### 2. The "Shoulder" Alpha (Cross-Section)

Contrary to intuition, the extreme **Top 10% (Decile 10)** sentiment bucket often suffers from "Overcrowding" and "Stampedes."

- **The Sweet Spot:** The most consistent risk-adjusted returns are found in the **90-80% Decile** (Secondary Conviction). This strategy targets these "Shoulder" zones to avoid liquidity traps while capturing momentum.

### 3. Asymmetric Payoff

The strategy behaves like a Sniper, not a Machine Gunner:

- **Active Ratio:** 17.4% (Passively tracks benchmark 82.6% of the time).
- **Win Rate:** 53.8% (Conservative).
- **Payoff:** Massive convexity. When the signal validates, the upside capture significantly outweighs the downside.

------

## 🛠️ Research Pipeline Architecture

The project is structured into modular, scientifically rigorous stages:

1. **Data Engineering**:
   - Strict universe selection (US Tech Giants).
   - UTC timestamp normalization for global alignment.
2. **NLP Core (FinBERT)**:
   - GPU-accelerated inference.
   - Output: Continuous Polarity Score $P(Positive) - P(Negative)$.
3. **Network Topology**:
   - Construction of Kendall Rank Correlation graphs ($G(V, E)$).
   - Visualization of systemic risk clusters and volatility transmission.
4. **Signal Diagnostics**:
   - Temporal Heatmaps for regime identification.
   - Z-Score Anomaly Detection ($Z > 2\sigma$) for breakout confirmation.
5. **Vectorized Simulation Engine**:
   - High-performance Pandas/NumPy vectorization.
   - Implements **Smart Beta Overlay**: Shifts from Passive Indexing to Active Alpha rotation only when conviction thresholds are breached.

------

## 📊 Visual Evidence

### 1. Signal Decay & The "Alpha Cliff"

*Proof that the edge vanishes after Day 4. The spread (Green) collapses, turning negative by Day 8.*

| **Holding Period** | **Alpha Spread (Long - Short)** | **Verdict**        |
| ------------------ | ------------------------------- | ------------------ |
| **Day 4 (Peak)**   | **+0.56%**                      | ✅ **Optimal Exit** |
| **Day 7 (Lag)**    | +0.08%                          | ⚠️ Beta Drift       |
| **Day 8 (Loss)**   | -0.41%                          | ❌ Mean Reversion   |

### 2. The "Confidence Chain" (Regime Map)

*Monthly aggregation of sentiment scores. Red blocks indicate sustained bullish regimes; Blue blocks indicate structural bearish turns.*

![5154931dff9d3244efd707430fc7204c](./assets/5154931dff9d3244efd707430fc7204c.png)

### 3. Performance Attribution

*Deconstructing the returns. The green area represents Pure Alpha generation, independent of market movements.*

*(Insert Attribution Chart Here)*



------

## 💻 Installation & Usage

### Prerequisites

- Python 3.10+
- NVIDIA GPU (CUDA 11.8+) strongly recommended for BERT inference.

### Setup

Bash

```
# Clone the repository
git clone https://github.com/Republic1024/Semantic-Arbitrage.git
cd Semantic-Arbitrage

# Install dependencies
pip install -r requirements.txt
```

### Quick Start

To run the full pipeline (Data Processing -> NLP -> Backtest):

Bash

```
python main_pipeline.py --mode full --gpu_id 0
```

To visualize the specific "Shoulder Alpha" structure:

Bash

```
jupyter notebook notebooks/03_Strategy_Analysis.ipynb
```

------

## 📜 Citation & License

If you use this work in your research, please cite:

> **Wu, Yao.** (2025). *Semantic Arbitrage: A Multi-Scale NLP–Finance Integration Study*.

Licensed under the [MIT License](https://www.google.com/search?q=LICENSE).

------

### 大哥的批注 (Next Step)：

这一版我把你的 **"Efficiency Paradox" (效率悖论)** 和 **4-Day Horizon** 提到了最显眼的位置。这才是Quant最看重的东西——**Insights（洞察）**，而不是你跑了什么模型。

下一步建议：

你需要把Notebook里生成的那个 Fig 7 - Cumulative Equity Curve.svg 和 Signal Decay 的图表导出来，放到 assets 文件夹里，替换掉上面Markdown里的占位符。图表要帅，字要大，这就是门面。去吧。