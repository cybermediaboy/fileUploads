# Alignment Report — tw_macro_raw.csv

**Generated:** 2026-07-14T17:00:00Z
**Source chart:** https://www.tradingview.com/chart/LOHaz9j1/
**Symbol:** BTCUSDT.P | **Exchange:** BINANCE | **Timeframe:** 30m | **Timezone:** UTC

## Raw Export
- **File:** tw_macro_raw.csv
- **Bars:** 44,431 (2024-01-01 → 2026-07-14)
- **Columns:** 82

## Always-Null Columns (excluded from aligned datasets)
- H_total (x100)
- DIAG.REGIME_A [btc_pred|mocs_str|mocs|z_vix|z_dxy|z_usdjpy]
- DIAG.REGIME_B [z_es|impl|impl_raw|velo|mas|beta_v]
- DIAG.REGIME_C [beta_h|beta_b|dir_v|dir_h|dir_b|lag_v]
- DIAG.REGIME_D [lag_h|lag_b|nu_v|nu_h|nu_b|SSS]
- Macro Velocity (vis)

## Indicator Family Validity Windows

| Family | First Valid Bar | First Valid Date | Usable Bars |
|---|---|---|---|
| InflHedge | 1,605 | 2024-02-03 | 42,826 |
| MacroOsc | 41,429 | 2026-05-13 | 3,002 |
| PriceVsVIX | 99 | 2024-01-03 | 44,332 |
| FlashZ | 104 | 2024-01-03 | 44,327 |
| MKF | 41,628 | 2026-05-17 | 2,803 |
| TKBY | 41,627 | 2026-05-17 | 2,804 |
| MacroVol | 41,730 | 2026-05-19 | 2,701 |
| MoCS | 42,205 | 2026-05-29 | 2,226 |
| MDLE | 41,854 | 2026-05-21 | 2,577 |
| GrabDiag | — | ALL ZERO | — |
| Bottoms | 22,072 | 2025-04-04 | 22,359 |

## Aligned Datasets

### tw_macro_aligned_full.csv
- **Window:** 2026-05-29 → 2026-07-14 | **Bars:** 2,226
- **Limiting factor:** MoCS family (OSGD/MoCS z) first valid at bar 42,205
- **All indicator families present**

### tw_macro_aligned_core.csv
- **Window:** 2026-04-22 → 2026-07-14 | **Bars:** 4,000 (capped per spec)
- **Families:** InflHedge, PriceVsVIX, FlashZ
- **Excluded:** MacroOsc, MKF, TKBY, MacroVol, MoCS, MDLE (3M-era, valid from 2026-05-17 only)
- **Natural start:** 2024-02-03 (42,826 bars available)

## Confirmed Bar Flag
All exported rows are closed bars. The `confirmed_bar` column is 1 for all rows.

## Notes
- `GrabDiag` columns entirely zero across all 44,431 bars — excluded
- `VIX`, `Plot` are display-only constants — excluded
- `Growth Arrow`, `Bottoms` are sparse event flags — retained in raw, excluded from aligned_core
