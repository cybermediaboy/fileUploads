# Feature Discovery Summary — BTC Directional Lead-Lag

**Dataset:** tw_macro_aligned_full.csv (2,226 bars, 2026-05-29 → 2026-07-14)
**Method:** Spearman rank correlation vs BTC forward returns at 6 horizons (30m, 1h, 2h, 4h, 8h, 24h)
**Threshold:** p < 0.05 (uncorrected)

## Results: 36 significant features, 146 significant pairs

### Tier 1 — Strong Directional Leads (|ρ| > 0.35, all 6 horizons)

| Feature | Peak |ρ| | Best Horizon | Direction | Source Indicator |
|---|---|---|---|---|
| Fast EMA (corr) | 0.497 | 24h | + | Price vs VIX |
| TKBY Zone3 Upper | 0.480 | 24h | − | VIX Contango Slope |
| TKBY Zone2 Upper | 0.474 | 24h | − | VIX Contango Slope |
| TKBY Zone1 Upper | 0.469 | 24h | − | VIX Contango Slope |
| Fast EMA | 0.464 | 24h | + | Price vs VIX |
| TKBY Basis Center | 0.456 | 24h | − | VIX Contango Slope |
| TKBY Basis | 0.456 | 24h | − | VIX Contango Slope |
| TKBY Zone1 Lower | 0.422 | 24h | − | VIX Contango Slope |
| TKBY Zone2 Lower | 0.415 | 24h | − | VIX Contango Slope |
| TKBY Zone3 Lower | 0.404 | 24h | − | VIX Contango Slope |
| Slow EMA | 0.403 | 24h | + | Price vs VIX |

### Tier 2 — Moderate Leads (|ρ| 0.15–0.35, 4–5 horizons)

| Feature | Peak |ρ| | Best Horizon | Direction |
|---|---|---|---|
| Macro Risk (VIX) | 0.326 | 24h | + |
| VIX Short | 0.287 | 24h | + |
| Macro Infl (C-BEI) | 0.250 | 24h | + |
| Risk Oscillator | 0.201 | 24h | − |
| Risk Signal | 0.198 | 24h | − |
| Infl Oscillator | 0.170 | 24h | − |
| Infl Osc (Hist) | 0.170 | 24h | − |
| Infl Signal | 0.167 | 24h | − |

### Tier 3 — Weak Intraday Leads (|ρ| < 0.15)

| Feature | Peak |ρ| | Best Horizon | Direction | Note |
|---|---|---|---|---|
| USDJPY Flash Z | 0.106 | 8h | − | Peaks at 8h, not 24h — genuine intraday lead |
| M-KF Peak +/− | 0.079 | 8h | +/− | |
| M-KF Velocity | 0.075 | 2h | − | |
| MDLE.md_signed | 0.108 | 24h | + | |
| Macro Vol | 0.107 | 24h | − | |

## Key Findings

1. **TKBY (VIX Contango Slope) is the dominant macro predictor.** All zone upper/lower bands and basis show ρ > 0.40 at 24h. Elevated contango upper bands consistently precede BTC underperformance.

2. **Signal strength grows monotonically with horizon.** All Tier 1-2 features peak at 24h. These are slow macro forces — not suitable for sub-2h timing.

3. **USDJPY Flash Z is the exception** — it peaks at 8h, making it the best candidate for intraday (4–8h) directional prediction without horizon drift.

4. **3M-era indicators (MoCS, MDLE, M-KF) show weak signals** in the current 2,226-bar window. Insufficient history to draw strong conclusions — revisit when >6 months of data available.

5. **Do not assume prior K=4 / three-factor / six-bar kernel.** Feature ranking here does not match the prior regime model's weighting. TKBY and EMA dominate; Flash Z signals are weak but intraday-specific.

## Next Steps (require separate authorization)
- Block-bootstrap significance correction (serial correlation adjustment)
- Multivariate feature selection
- New regime model design with TKBY + EMA as primary factors
- Expand 3M indicator window when sufficient history accumulates
