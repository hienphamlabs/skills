# General Analysis Skills

## Fundamentals Analyst
- **Profitability:** ROE (>15%), Net Margin (>20%), Op Margin (>15%).
- **Growth:** Revenue, Earnings, and Book Value growth (>10%).
- **Health:** Current Ratio (>1.5), Debt/Equity (<0.5).

## Growth Analyst
- **Trend Analysis:** Calculates the slope of trend lines for Revenue, EPS, and FCF growth.
- **Margin Monitoring:** Gross, Operating, and Net margin trends.
- **Insider Conviction:** Net flow ratio of insider trades.

## Sentiment Analyst
- **News Logic:** Combines LLM headline classification (70% weight) with insider trading patterns (30% weight).

## Valuation Analyst
- **Ensemble methodology:** DCF (35%), Owner Earnings (35%), EV/EBITDA (20%), Residual Income (10%).
- **WACC Logic:** CAPM-based cost of equity and interest-coverage based cost of debt.

## Implementation Snippet (Growth Trend)

```python
def _calculate_trend(data: list[float | None]) -> float:
    """Calculates the slope of the trend line using simple linear regression."""
    # ...
    slope = (n * sum_xy - sum_x * sum_y) / (n * sum_x2 - sum_x**2)
    return slope
```
