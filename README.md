# Transformer-based High-Frequency Trade Engine (BTC-USD)

An advanced quantitative trading framework that integrates **Deep Learning (Transformer Architecture)** with **Statistical Market Efficiency filters** for high-probability scalping on 5-minute timeframes.

## Core Methodology
This project implements a hybrid approach to financial time series forecasting:

1.  **Forecasting Engine:** A 3-layer Transformer Encoder designed to capture long-range dependencies in Bitcoin's price action.
2.  **Predictive Logic:** Utilizes a **Recursive Multi-step Look-ahead (T+10)**. Instead of point-predictions, the model generates a trend vector for the next 50 minutes to calculate a "Bias-Corrected Expectation".
3.  **Signal Validation:**
    * **Kaufman Efficiency Ratio (ER):** Acts as a noise filter, ensuring trades only occur during periods of high price efficiency (period=20).
    * **Internal Bar Strength (IBS):** A mean-reversion check to prevent entering at the extreme ends of a price candle.
    * **Momentum Alignment:** Cross-references AI predictions with 15-minute price momentum to eliminate "lagging" false positives.

## Backtest Performance (Audit)
The model underwent rigorous backtesting over 1200 bars (~4 days) with a disciplined risk management protocol:
- **Capital:** 100 USDT (Leverage 20x)
- **Risk per Trade:** 0.8% - 1.0% Fixed Stop Loss
- **Reward Ratio:** 1:2.0 - 1:2.5
- **Trailing Strategy:** Break-Even activation after 5 bars of profitability.


## Tech Stack
- **Deep Learning:** PyTorch (Transformer Encoder)
- **Signal Processing:** Fast Fourier Transform (FFT) for Price Smoothing
- **Quant Tools:** Pandas, Numpy, Scikit-Learn
- **Data Source:** YFinance API

## Usage
1. Load your pre-trained weights (`.pth` file).
2. Sync 1m and 5m OHLCV data.
3. Run the **Signal Generator** for live Bybit execution levels.

---
**Author:** Dwilaksana Abdullah Rasyid, PhD in Statistics.
*Independent Researcher specializing in Bayesian Statistics and Quantitative Finance.*
