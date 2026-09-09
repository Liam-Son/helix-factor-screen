# helix-factor-screen

**Buy & hold HLX vs cycle-lag strategy**

![bh vs strategy](cycle_lag/bh_vs_strategy.svg)

| 2012-01 → 2026-09-01 | End NAV (start=1) | What it is |
|---|---|---|
| **Strategy** (navy) | **2.06x (+106%)** | Long HLX only when 2-day G1·G2·G3 on; cash otherwise; skip <5d flicker |
| **Buy & hold HLX** (orange) | **0.69x (−31%)** | Always long |
| OSB peers (grey) | 0.71x | SLB/HAL/NOV/RIG/OII |

Navy line is flat most of the time — that *is* the strategy. It does not ride 2015 or 2020 down. It is in-sample after 2022. Live ticker is **HOS**; do not splice. Engine today: **WAIT**.

Trade bars: [engine_trades_tight.svg](cycle_lag/engine_trades_tight.svg) · [csv](cycle_lag/engine_trades_tight.csv) · [RESULTS](RESULTS.md) · [engine](cycle_lag/buy_engine.py)
