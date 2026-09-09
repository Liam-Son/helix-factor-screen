# helix-factor-screen

Research log for **Helix (HLX) → Hornbeck (HOS)** as an equity, not an oil-trading satellite.

- HLX ends **2026-09-01**. HOS starts **2026-09-02**. Do not splice.
- Live engine status (2026-09-09): **WAIT** (HOS < 60 return days, G3 locked).

## Verdict board

| Idea | Verdict | Why |
|---|---|---|
| Financial astrology / lunar / SSOI → WTI | KILL | No OOS edge after placebos |
| Six-market HECM residual → HLX +20d | KILL | OSB alone wins; OOS catch-up fails |
| HLX/WTI rolling-β z-pairs (synthetic paper rules) | KILL | Real data 2021–22 **−66%**; ADF p=0.11 |
| Crack z → HLX | KILL | Cracks weakly mean-revert; do not transmit to HLX |
| Refiner basket / WTI 20d RV | CANDIDATE (not HLX) | Val/OOS IC negative as MR; separate book |
| Cycle-lag BUY engine G1·G2·G3 | KEEP as checklist | 2022-style setup only; default cash |

## Cycle-lag engine (what we run)

Gates must all be ON **two days in a row**. Trade next day. VIX top quintile → 0.5x. HOS post-merger cap 0.5x. G3 locked until 60 HOS days.

- G1 environment: 2 of (WTI +20% vs 12m low, WTI not −25% vs 12m high, UPB 60d > 0)
- G2 services: OSB 60d > 0 or OIH above 120d low
- G3 lag: target 60d return − OSB ≤ −10pp

Research filter: ignore episodes shorter than 5 sessions.

Tight ledger (21 trades, HLX 2012–2026-09-01):

- Win rate **15/21 = 71%** (vs OSB 57%)
- Avg log-return +3.9% (winners +10.1%, losers −11.6%)
- Account with 2-day confirm + drop <5d: NAV **+106%** vs HLX BH **−31%**
- In-sample after seeing 2022. Not a validated alpha paper.

Code: `cycle_lag/buy_engine.py`  
Trades: `cycle_lag/engine_trades_tight.csv`

## Factor screen

Same-day ICs are high for OIH/OSB/XLE (~0.70–0.76). Forward 20d ICs are ~0. See `factors/factor_screen.csv`.

## QET-MA mapping

Causal-first + PIT z + disc/val/oos:

- HLX/WTI z is continuation, not mean reversion → do not deploy.
- Crack z is a weak crack product, not an HLX product.
- Refiner/WTI relative value is the only QET-style candidate, and it is **not** the HOS engine.

## Live rule

`OFF` unless three confirmed gates. Today: **WAIT**. First HOS combined print before 1.0x.
