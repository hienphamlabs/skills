# Technical Analysis Skill

## Philosophy
Mathematical and statistical analysis of price and volume data to identify market trends and momentum.

## Core Principles
- **Trend Following:** EMAs and ADX.
- **Mean Reversion:** Bollinger Bands and Z-scores.
- **Momentum:** Speed of price changes.
- **Volatility Regime:** Adjusting strategies based on ATR/Stdev.
- **Statistical Arbitrage:** Hurst exponent, skewness, and kurtosis.

## Implementation Logic (Python)

```python
def weighted_signal_combination(signals, weights):
    """
    Combines multiple trading signals (Trend, Mean Reversion, Momentum, etc.)
    using a weighted ensemble approach.
    """
    # signal_values = {"bullish": 1, "neutral": 0, "bearish": -1}
    # ...
```

## Logic
Combines five strategies using a weighted ensemble approach to generate a final consensus signal.
