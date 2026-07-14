# Indicator Inventory — Chart LOHaz9j1
**Chart:** https://www.tradingview.com/chart/LOHaz9j1/
**Symbol:** BINANCE:BTCUSDT.P | **Timeframe:** 30m | **Generated:** 2026-07-14

## Chart State
- Symbol: BINANCE:BTCUSDT.P
- Resolution: 30 (30-minute bars)
- Chart Type: 1 (Candlestick)
- Timezone: UTC
- Replay Mode: Not active
- Bar Status: Closed bars exported

---

## 1. Price vs VIX — Global Bottoms Strategy
- **Entity ID:** Pb4Rzx
- **Source:** Could not switch Pine Editor to this indicator via remote CDP (dropdown not accessible). Source protected or requires manual open.
- **Access type:** Editable Pine (confirmed open-source based on CSV outputs)
- **Exported CSV columns:** VIX Short, VIX Long, Slow EMA, Fast EMA, Fast EMA (corr), Global Bottom (event), Local Bottom (event), Growth Arrow (event), Plot (display constant)
- **Value types:** Price-relative levels (EMA/VIX overlay), boolean event flags
- **Warmup:** ~200+ bars (EMA-based)
- **Repainting risk:** LOW (closed bar, no lookahead evident from outputs)
- **Session dependency:** VIX feed required
- **First valid bar:** ~bar 99 (2024-01-03)

---

## 2. Inflation Hedge Decomposition [Dual Oscillator]
- **Entity ID:** VRzezH
- **Source:** Not currently open in Pine Editor — could not read remotely
- **Access type:** Editable Pine
- **Exported CSV columns:** β Pure (×1000), β Risk (×1000), Infl Oscillator, Infl Signal, Infl Osc (Hist), Risk Oscillator, Risk Signal, Pure Hedge Signal, Risk Contamination, Mean Reversion Setup, Dual Tailwind, Dual Headwind, Factor Divergence, Regime End, Regime Start, Infl Subcycle Break, Risk Subcycle Break, Macro Midline, Macro +50, Macro -50, Macro Infl (C-BEI), Macro Risk (VIX), Macro Base
- **Value types:** β coefficients (raw×1000), oscillator levels, signal flags, boolean event flags
- **Warmup:** ~1,605 bars (~2024-02-03)
- **Repainting risk:** UNKNOWN (source not read — requires manual Pine Editor focus)
- **First valid bar:** 1,605 (2024-02-03)

---

## 3. VIX Contango Slope — Predictive Edition
- **Entity ID:** VZWcOf
- **Source:** Not currently open in Pine Editor — could not read remotely
- **Access type:** Editable Pine
- **Exported CSV columns:** TKBY Basis, TKBY Zone1-3 Upper/Lower, TKBY Basis Center, H_total (x100) [ALL NULL], Macro Vol Baseline, Macro Vol, Model Activity Score (MAS)
- **Value types:** VIX contango basis/levels, volatility regime scores
- **Warmup:** ~41,627 bars — valid only from 2026-05-17 (3M indicator)
- **Repainting risk:** UNKNOWN (source not read)
- **First valid bar:** 41,627 (2026-05-17)

---

## 4. Macro Shock: Flash Detection [Perplexity]
- **Entity ID:** MCkg7B
- **Source:** FULLY READ (297 lines, 17,079 chars)
- **Version:** Pine Script v5
- **Libraries:** None
- **Access type:** Editable Pine (open source)
- **request.security symbols:** FX:USDJPY, CME_MINI:ES1!, CBOT:ZN1!, COMEX:GC1!, CBOE:VX1!, TVC:DXY — all same TF, no lookahead, gaps=default
- **Inputs (effective):** LB_FLASH=4, LB_TREND=16, LB_Z=100, Z_FLASH_TRIG=2.5, ACCEL_TRIG=0.15, FLASH_VEL_TRIG=0.2, LABEL_SPACING=5, vel_ext_lookback=1000, vel_tail_pct=5.0
- **Exported plots:** USDJPY Flash Z, ES Flash Z, VIX Flash Z, DXY Flash Z (z-scores); Extreme Up/Down Vel (bool event shapes)
- **NOT exported (internal):** composite_z, sync_score_bear/bull, flash_count_bear/bull, individual sig_* booleans, comp_vel_3, individual accelerations
- **Warmup:** 100 bars (LB_Z baseline)
- **Repainting:** NONE — closed-bar request.security, no lookahead, no pivots, no centered filters
- **Normalization:** Z-score = (velocity − SMA(velocity, 100)) / StDev(velocity, 100)
- **First valid bar:** 104 (2024-01-03)

---

## 5. Crypto Macro 3-Factor Expectations v0.4.9
- **Entity ID:** CatTZA
- **Source:** Not currently open in Pine Editor — could not read remotely
- **Access type:** Editable Pine (version tag suggests active development)
- **Exported CSV columns:** macro3f, M-KF Velocity (peak channel), M-KF Peak +/−, Macro Velocity (vis) [ALL NULL], Diag: M-KF Bull/Bear Peak, MoCS z, OSGD LONG/SHORT, OSGD A LONG/SHORT, MDLE.md_signed, MDLE.md_impl_mag, MDLE.md_lag_min/max, LGD.active, MDLE.lag_lgd_pack, MDLE.te_lag_comp, Diag: Grab→Up/Down [ALL ZERO], DIAG.REGIME_A/B/C/D [ALL NULL]
- **Value types:** Momentum/regime scores, Kalman-filtered velocities, lag diagnostics, OSGD signals
- **Warmup:** ~42,205 bars — valid from 2026-05-29 (newest, binding constraint)
- **Repainting risk:** UNKNOWN — Kalman filtering implies smoothing delay; MDLE lag diagnostics suggest lag-compensation logic
- **First valid bar:** 42,205 (2026-05-29)

---

## Pine Editor Limitation
`pine_get_source` with `entity_id` fails remotely — Pine Editor only exposes the currently focused script. Only MCkg7B was readable. Indicators 1, 2, 3, 5 require manual Pine Editor focus per indicator to read source remotely.
