# Residual catch-up after the cycle-lag kill

Working paper note. 10 September 2026.  
Companion to [THESIS.md](THESIS.md). Primary computations live on ls-crude factor 102 / 103.

## Question

After 097 established that a 60-day cycle-lag engine does not beat buy-and-hold out of sample, a sharper claim remains:

\[
HIR_t = R^{HLX}_t - \mathbb{E}[R^{HLX}_t \mid \text{oil and oil-service factors}]
\]

When \(Z(HIR_t)\) is sufficiently negative, does Helix subsequently catch up versus a peer basket?

This is not “Helix goes up after it goes down.” The object is peer-neutral catch-up.

## Design (frozen before holdout)

| item | rule |
| --- | --- |
| Tape | HLX through 2026-09-01. No HOS splice. |
| Ordinary proof window | ends 2026-04-21 |
| M&A quarantine | 2026-04-22 – 2026-09-01, unused for proof |
| Expected return | causal rolling Ridge, \(\lambda=1\), 252 sessions |
| Factors | WTI, Brent, RBOB, ULSD, XLE, SLB, HAL, BKR, upstream EW, OSB EW |
| Standardisation | prior residuals only |
| Primary event | \(Z \le -1.50\) |
| Execution | next session; 20 sessions; non-overlap |
| P&amp;L | \(R^{HLX}-R^{OSB}-40\,\text{bp}\) |
| Development | entries 2012-01-03 – 2021-12-31, **exit-date** purge |
| Holdout | 2022-01-03 – 2026-04-21, sealed until ADVANCE |

Alpha-Lock requires all fourteen gates on attested holdout. Development may not open holdout in the same sitting as a new rule.

## Results

### 102 v19 first-breach (close-to-close)

| book | n | mean net | Sharpe | bootstrap 95% lo |
| --- | ---: | ---: | ---: | ---: |
| DEV | 55 | −0.60% | −0.13 | −4.89% |
| HOLD | 29 | −0.25% | −0.09 | −3.48% |

HOLD 100 bp mean −0.85%. Neighbors on DEV: 0 / 9 positive. Fourth holdout slice negative. Verdict **NOT_PROVEN**. Holdout was opened under the v19 protocol and failed.

Source: [102 README](https://github.com/Noah-TaeHwan/ls-crude/blob/main/research/factors/102-helix-hir-alphalock/README.md)

### 103 peer pairs

Rolling-beta long-cheap / short-rich on HLX versus OII, FTI, SLB, XPRO, TDW, and among those peers. Same freeze.

HLX–OII 20-day correlation 0.88 / 0.70 (DEV / HOLD). Daily residual AR(1) on DEV ≈ 0.016 (half-life ≈ 0.2 sessions). A 20-day pair hold is sitting on white noise.

HLX–OII pair book: DEV −3.23%, HOLD +1.08% with bootstrap lower bound −1.97%. Verdict **NOT_PROVEN**.

Source: [103 README](https://github.com/Noah-TaeHwan/ls-crude/blob/main/research/factors/103-helix-peer-pairs/README.md)

### 102 v22 two-turn confirmation (DEV only after v19 holdout fail)

Distress still \(Z\le-1.50\). Trade only after two consecutive HIR improvements. HOLD not re-opened.

| | |
| --- | ---: |
| n | 38 (floor 40) |
| mean net | +2.65% |
| bootstrap lo | −2.31% |
| neighbors + | 6 / 9 (need 7) |
| ADVANCE | false |

Synthetic self-test passed; null worlds did not look like alpha. Real ADVANCE failed. Engine file: [helix_v22_engine.py](https://github.com/Noah-TaeHwan/ls-crude/blob/main/research/factors/102-helix-hir-alphalock/v22/helix_v22_engine.py)

### 102 v22 move D — twin OSB = OII + FTI

DEV mean −1.04%, neighbors 2 / 9. Worse than baseline. HOLD sealed.

### 102 v23 — 10-session episode cap (move A)

If two-turn confirmation does not arrive within 10 sessions, abandon the episode.

| | v22 | v23 |
| --- | ---: | ---: |
| n | 38 | 37 |
| mean net | +2.65% | +3.85% |
| bootstrap lo | −2.31% | −1.24% |
| neighbors + | 6/9 | 6/9 |
| ADVANCE | false | false |

The 15-session neighbor column remains negative at every threshold. That is what blocks 7/9. Engine has no holdout mode.

Source: [v23 README](https://github.com/Noah-TaeHwan/ls-crude/blob/main/research/factors/102-helix-hir-alphalock/v23/README.md)

## Interpretation

Three economically distinct statements have been tested on the same HLX tape.

1. Cycle lag versus OSB is a tradable lead. **False** out of sample (097).
2. Extreme negative residual mean-reverts versus OSB at \(Z\le-1.50\), 20 sessions. **False** on the v19 holdout (102).
3. Waiting for two HIR up-turns, or capping the wait at 10 sessions, recovers a development book that clears the written ADVANCE rule. **False** so far (v22, v23). Means can be positive while event counts, neighbor stability, and bootstrap lower bounds are not.

OII is the closest listed twin in correlation space. That does not make HLX–OII a mean-reverting spread.

## What this note does not do

- It does not reopen 2022–2026-04-21 after v22/v23.
- It does not lower \(n=40\) or \(7/9\).
- It does not treat synthetic qualification as proof.
- It does not splice HOS.

## Status

```
NOT_PROVEN
HOLD sealed after v19 failure
DEV line open only under a single pre-registered change
```
