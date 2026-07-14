# Pine Guard Findings — Chart LOHaz9j1

## Scope
Pine source was readable for **1 of 5 indicators** (MCkg7B — Macro Shock: Flash Detection).
The remaining 4 could not be read via remote CDP due to Pine Editor focus limitation.

---

## MCkg7B — Macro Shock: Flash Detection [Perplexity]

### Static Analysis Results

| Category | Finding | Severity |
|---|---|---|
| Lookahead | `request.security` uses default (no `lookahead=barmerge.lookahead_on`) | ✅ PASS |
| Future bars | No `plot(..., offset=N)` with positive N | ✅ PASS |
| Centered filters | No centered MA, no symmetric smoothing | ✅ PASS |
| Retrospective relabeling | No `var` label reassignment after close | ✅ PASS |
| Array safety | No array usage | ✅ PASS |
| Pivot usage | No `ta.pivothigh/pivotlow` (which repaint) | ✅ PASS |
| Security nesting | `request.security` nested inside `request.security` — non-standard pattern | ⚠️ WARN |
| NA carry-forward | No explicit `na()` fill — relies on TradingView default gap fill | ℹ️ INFO |
| Warmup adequacy | LB_Z=100 bars declared; vel_ext_lookback=1000 adds percentile warmup | ℹ️ INFO |
| Calendar/session | 23/5 futures data — weekend gaps carried forward by TV | ℹ️ INFO |
| Internal values not exported | sync_score, flash_count, composite_z — analytically valuable, not plotted | ℹ️ INFO |

### Nested request.security Warning
The pattern `request.security(syminfo.tickerid, tf, [request.security(...), ...])` is non-standard and may produce unexpected NA propagation on historical bars. Functionally works in Pine v5 but is fragile. No data integrity issues observed in exported CSV.

### Recommendation
MCkg7B is **safe for directional prediction research** — no repainting, no lookahead, no future leakage. The nested security pattern should be refactored in production. The `composite_z`, `sync_score_bear/bull`, and `flash_count` internals should be exported as additional plots for feature discovery.

---

## Pb4Rzx, VRzezH, VZWcOf, CatTZA
Source not available for Pine Guard validation. Manual Pine Editor focus required per indicator.
