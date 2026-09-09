# helix-factor-screen

HLX (through 2026-09-01 only; HOS is not spliced) factor screen.

The 96-factor book is **not** checked into this GitHub account as a single file. This repo screens the **energy-chain subset that can actually be built from public prices** plus solar/geomagnetic leftovers from the 093/094 tests.

Question: which factors help **predict HLX**, not just explain the same day?

## Verdict

| Role | Factors | Useful for HLX price *prediction*? |
|---|---|---|
| Same-day beta | OIH, OSB, XLE, UPB, FTI, BKR, TDW | Yes as *explanation* (IC 0.60–0.76). **No** as 20D forecast (IC ~0). |
| Crude / products | WTI, Brent, RBOB, ULSD, USO | Same-day IC 0.39–0.50. Forward 20D IC ~0.02, insignificant. |
| Cracks | RBOB_CRK, ULSD_CRK | Dead both ways. |
| Dollar / credit | DXY, HYG | DXY same-day −0.17. Forward ~0. |
| Solar | SN27, Ap | SN27 forward IC +0.04 (p=0.005) but OOS p=0.19. Ap dead. |
| Relative value | z_HLX_WTI, z_HLX_OSB | Cheap-on-WTI has **negative** 20D IC (−0.09). Mean-reversion pair fails. |
| Vol / fear | VIX_lvl, HLX_rv20 | Weak positive 20D IC (~0.08) and OOS +0.14 — high vol precedes higher *average* 20D return (risk premium), not a timing edge after costs. |
| Momentum | HLX_mom60, HLX_minus_OSB_20 | Negative forward IC. OOS HLX-minus-OSB IC **−0.23** (continuation of relative weakness, not catch-up). |
| Service momentum | OSB_mom20 | Small positive 20D IC +0.05; OOS +0.09 / XOSB +0.16. Best *weak* forward candidate, still tiny. |

**OSB/OIH explain HLX. Almost nothing in this set forecasts HLX +20D in a way that survived HECM / pair tests.**

## Method

- Target A: Spearman IC(factor_t, HLX return t+1..t+20)
- Target B: same vs HLX−OSB +20D
- Same-day IC for comparison only
- Sample 2008-01-01 → 2026-04-21 (pre deal). OOS column = 2020-01-01 → 2026-04-21
- HLX ends 2026-09-01. Do not use historical HOS ticker before 2026-09-02

See `factor_screen.csv` and `screen.py`.

## What from a 96-factor oil book maps here

Keep as **HLX cycle filters / same-day controls**, not alpha:
1. Oil-service basket (OSB / OIH)
2. Upstream producers (UPB / XLE)
3. WTI and Brent *levels and 20D momentum* as environment
4. VIX / realized vol as risk regime

Kill / do not promote for HLX timing:
- WTI–HLX ratio mean reversion
- Cracks as incremental predictors
- Same-day crude returns as lead
- Solar/geomagnetic as linear alpha
- Six-factor HECM residual 20D catch-up (see prior HECM work)

HOS: FORWARD_ONLY. Re-run this screen after several quarters of combined prints.
