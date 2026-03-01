# Risk Management Skill

## Philosophy
Prudent capital allocation based on volatility-adjusted risk and correlation management.

## Core Principles
- **Volatility-Adjusted Position Sizing:** Larger allocations for stable stocks.
- **Correlation Control:** Reducing limits for highly correlated assets.
- **Downside Protection:** Ensuring no single position exposes the portfolio to excessive risk.

## Implementation Logic (Python)

```python
def calculate_volatility_adjusted_limit(annualized_volatility: float) -> float:
    """
    Logic:
    - Low volatility (<15%): Up to 25% allocation
    - Medium volatility (15-30%): 15-20% allocation  
    - High volatility (>30%): 10-15% allocation
    - Very high volatility (>50%): Max 10% allocation
    """
    # ...
    return base_limit * vol_multiplier

def calculate_correlation_multiplier(avg_correlation: float) -> float:
    """Map average correlation to an adjustment multiplier (0.7x to 1.1x)."""
    if avg_correlation >= 0.80: return 0.70
    if avg_correlation >= 0.60: return 0.85
    # ...
```

## Logic
Adjusts a 20% base limit by volatility and correlation multipliers, then caps by available cash.
