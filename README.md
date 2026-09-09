# helix-factor-screen

Helix (HLX through 2026-09-01) and Hornbeck (HOS from 2026-09-02). **Do not splice.**

Live engine (2026-09-09): **WAIT**.

## Tight engine chart (21 trades, 71% hit)

![tight trades](cycle_lag/engine_trades_tight.svg)

Ledger: [cycle_lag/engine_trades_tight.csv](cycle_lag/engine_trades_tight.csv)

## What is live

Cycle-lag BUY engine (`cycle_lag/buy_engine.py`). Cash is default. Three 2-day-confirmed gates. HOS G3 locked until 60 return days.

## What is dead

Oil-up + stock-down standalone buy: loose rule is a coin; tight 2022-like rule 8 events, 60d hit 25%, avg -19%. Full writeup in [RESULTS.md](RESULTS.md).
