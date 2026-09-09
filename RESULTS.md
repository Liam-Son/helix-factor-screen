# Results dump (2026-09-09)

## 1. Real-data z-pairs (paper rules on actual HLX/WTI)

Params: 60d OLS beta, |z|>2 in, |z|<0.5 out, |z|>3.5 stop, next-day, 15bp/switch.

| | Synthetic paper | Real 2016-09-09..2026-09-01 |
|---|---|---|
| Net Sharpe | 0.89 | 0.31 |
| MDD | -26% | -73% |
| Total | +267% | -29% |
| 2021-22 | +25% ann | **-42% ann / -66% cum** |

Static residual ADF p=0.11. Mean rolling beta 0.89, sd 0.80.

## 2. Factor ICs vs HLX (2008..2026-04)

Top same-day: OIH 0.76, OSB 0.75, XLE 0.70, UPB 0.66, WTI 0.47.
Top fwd20 (still small): z_HLX_WTI -0.09, VIX_lvl +0.08, HLX_rv20 +0.07.
OOS fwd20 HLX_minus_OSB_20 = -0.23 (relative weakness continues).

## 3. QET channel tests (Spearman IC, 20d forward)

Crack z → crack+20 OOS IC -0.113; z<=-2 then +0.118 (MR in cracks).
Crack z → HLX+20 OOS: z<=-2 then HLX -0.066 (no transmission).
Ref/WTI z → REF-WTI+20 Val IC -0.287 OOS -0.202; z<=-2 then +0.05..+0.06.
HLX/WTI z → HLX+20: cheap stays cheap (oos z<=-2 then -0.095).

## 4. Tight cycle-lag trades

See cycle_lag/engine_trades_tight.csv (21 rows).
Standout plus: 2016-07, 2018-03, 2021-12..2022-02, 2022-07-19.
Standout minus: 2017-01-09..03-28 (-27%), 2022-06-23 (-16%).

## 5. Live snapshot

2026-09-09 HOS WAIT. G1 True G2 True G3 locked.
