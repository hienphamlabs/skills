---
name: invest-trading-strategy
description: Generate structured trading plans for crypto strategies, incorporating market snapshot metrics and portfolio-based risk management. Use for autonomous trading planning and risk evaluation.
---

# Invest Strategy (Prompt-based)

This skill enables autonomous crypto trading planning within the ValueCell Strategy Agent framework. It focuses on generating actionable, risk-adjusted trade instructions.

## Trading Lifecycle

1. **Feature Ingestion**: Analyze market snapshot metrics (prices, funding, OI, change %).
2. **Constraint Check**: Verify `max_positions`, `max_leverage`, `min_notional`, and `free_cash`.
3. **Decision Generation**: Propose one of: `open_long`, `open_short`, `close_long`, `close_short`, or `noop`.
4. **Normalization**: Align plans with exchange-specific precisions and portfolio equity.

## Performance Adaptation (Sharpe Ratio)

This skill requires adaptive behavior based on rolling performance:
- **Sharpe < -0.5**: EMERGENCY STOP (choose `noop` for 6+ cycles).
- **Sharpe -0.5 to 0**: Tighten criteria (confidence > 0.80) and reduce trade frequency.
- **Sharpe 0 to 0.7**: Maintain standard discipline.
- **Sharpe > 0.7**: Optimize for growth while staying within constraints.

## Constraints & Semantics

- **One Symbol, One Action**: Never hedge (long + short on the same symbol).
- **Churn Prevention**: Avoid rapid flipping. Use `entry_ts` to ensure positions are held for reasonable windows.
- **Liquidity Buffer**: Reserve a small buffer for fees (e.g., 1%) and slippage.
- **Position Sizing**: Use `free_cash` as the primary sizing budget.

## Strategy Output

- **Action Plan**: A structured JSON instructions list.
- **Transparent Rationale**: Must explain signals evaluated (e.g., funding, volume, price trends) and how sizing was derived.
