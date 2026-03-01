---
name: invest-grid-trading
description: Provide dynamic grid trading parameter advice based on market volatility, liquidity, and portfolio constraints. Use for rule-based mean-reversion trading strategy configuration.
---

# Invest Grid

This skill advises on grid trading parameters within the ValueCell Grid Agent framework. It uses an LLM to dynamically optimize rule-based grid execution.

## Core Mechanism

- **Mean-reversion**: Automate adds and reduces as the price crosses "grid lines" (increments of `step_pct`).
- **Base Quantity**: Calculated from equity and `base_fraction`.
- **Spot vs. Perp**: Spot is long-only; Perps are bi-directional.

## Parameter Advice Guidelines

When generating grid advice, consider:
1. **Sensitivity**: Use smaller `step_pct` (high sensitivity) for high-liquidity, high-volatility pairs.
2. **Step Control**: Max `max_steps` per cycle (typically 1 to 5).
3. **Risk/Capital**: Scale `base_fraction` (0.03 to 0.10) relative to `free_cash` and `max_leverage`.
4. **Continuity**: Prefer gradual adjustments to `grid_count` (±2) to avoid abrupt strategy shifts.

## Market-Driven Triggers

- **High Funding/OI**: Suggest tighter grids and smaller fractions.
- **Stable Regime**: Maintain existing parameters if volatility is within thresholds.
- **High Volatility**: Increase `max_steps` to capture wider price swings.

## Advisory JSON Structure

Provide pure JSON output for parameter updates:
```json
{
  "grid_step_pct": 0.001,
  "grid_max_steps": 3,
  "grid_base_fraction": 0.08,
  "grid_lower_pct": 0.10,
  "grid_upper_pct": 0.10,
  "grid_count": 2,
  "advisor_rationale": "Brief rationale on market indicators used"
}
```
