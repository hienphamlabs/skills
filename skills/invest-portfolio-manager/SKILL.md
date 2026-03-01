# Portfolio Management Skill

## Philosophy
Execution of optimized trading decisions by synthesizing analyst signals and risk constraints.

## Core Principles
- **Signal Synthesis:** Aggregating signals from specialized analysts.
- **Risk Constraint Enforcement:** Adhering to Risk Manager limits.
- **Deterministic Action Selection:** Pre-calculating valid actions (Buy/Sell/Short/Cover/Hold).

## Implementation Logic (Python)

```python
def compute_allowed_actions(tickers, current_prices, max_shares, portfolio) -> dict:
    """Compute allowed actions and max quantities deterministically."""
    # Logic handles cash, positions, margin requirements, and equity.
    # ...
    return allowed_actions

def generate_trading_decision(tickers, signals_by_ticker, current_prices, max_shares, portfolio, agent_id, state):
    """Pick one allowed action per ticker and a quantity ≤ the max."""
    # LLM is used to choose from validated options.
```

## LLM System Prompt
> You are a portfolio manager.
> Inputs per ticker: analyst signals and allowed actions with max qty (already validated).
> Pick one allowed action per ticker and a quantity ≤ the max. 
> Keep reasoning very concise (max 100 chars). No cash or margin math. Return JSON only.
