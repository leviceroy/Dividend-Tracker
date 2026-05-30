# Roadmap

High-level direction for Dividend Tracker. This is the curated view — granular tracking
happens privately. Suggestions welcome via
[feature requests](https://github.com/leviceroy/Dividend-Tracker/issues/new?template=feature_request.yml).

## Shipped

- Multi-account / multi-currency income ledger with reporting-currency conversion
  (at-current and at-transaction modes)
- Live prices → market value, current yield, unrealized P&L, realized P&L, total return
- Forward income on the trailing-12-month DPS sum + Indicated rate
- Yield-on-cost on the reporting-currency actually invested (FX at purchase)
- Dividend CAGR, growth streaks, cut detection, income-growth YoY
- Stock splits (with split-adjusted historical DPS)
- Special dividends (excluded from forward / growth)
- DRIP — reinvested dividends materialize a linked buy and accrue shares
- FIRE / income-target progress strip
- Concentration (HHI) + upcoming-ex-dividend calendar
- In-app auto-update (signed, GitHub Releases)
- Auto-update settings + manual "Check for updates"
- Demo data: one-click load/delete from Admin

## In development

- **Withholding-tax tracking, the effective-WHT KPI, and the Swiss DA-1 reclaim card.**
  The cards are visible in the app but flagged "under development" — treat as
  informational previews, not a tax filing source.
- DA-1 tax-year CSV export

## Planned

- Real broker-declared ex-dividend calendar (replace the historical-cadence projection)
- Expense ratio & TTM yield per instrument
- Dividend safety score (payout ratio, coverage)
- Benchmark vs. a chosen index
- Windows build
- License key activation (yearly subscription)

## Considering

- Linux build
- Optional encrypted iCloud backup of the local database
- Multi-portfolio profiles in a single install

---

© 2026 Chris Wenk. All rights reserved.
