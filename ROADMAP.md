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
- FIRE income-target progress strip **and** FIRE timeline chart with monthly-contribution
  projection (income-weighted 3y CAGR as growth assumption)
- Concentration (HHI) by income **and** by market value
- Upcoming ex-dividend list with deduped per-ticker sorting
- **Dividend Safety Score (open formula)** — 0-100 read per holding from streak, payout
  ratio, FCF coverage, debt/equity, earnings growth. Every weight documented; ETFs and
  funds skipped cleanly via Yahoo `quoteType`.
- **Quality KPI row** — Chowder Number, income-weighted 5y DGR, payout ratio, FCF
  coverage; each with click-through detail explaining the formula and threshold.
- **Aristocrat / King / Achiever / Contender badges** — automatic streak classification
  with income-share readout
- **Benchmark comparison** — portfolio vs a chosen index (SPY / VYM / SCHD / SSMI):
  1-year total return, current yield, 3-year DGR, with spread vs portfolio
- **Trajectory chart** — yield-on-cost and forward annual income over the last 36 months,
  honouring the gross-vs-net forward-income view
- **Drawdown chart** — TTM income drawdown and total-return drawdown side-by-side
- **Ex-date heatmap** — 78 weeks back + 26 weeks ahead, density-banded
- **Customisable dashboard** — hide/show widgets via the ⚙ customise panel; drag the ⋮⋮
  handle to reorder; layout auto-fits to viewport width (small panels pack side-by-side
  when there's room, stack when there isn't)
- **Command palette (⌘K)** — global fuzzy navigation across tabs, dialogs, and actions
- **Per-ticker drill page** — full dividend history, growth, fundamentals, positions
  across accounts, free-form research notes
- **CSV export** — Dividends, Holdings, Transactions, Accounts as portable CSV
- **Undo toasts** — non-destructive delete/edit workflow on the heavy-traffic tables
- **Per-jurisdiction treaty WHT rates** — default per-country withholding configurable
  in Admin
- **Yield band thresholds** — user-configurable cutoffs colour YoC and current yield
  across the app
- In-app auto-update (signed, GitHub Releases) with manual "Check for updates"
- Demo data: one-click load/delete from Admin

## In development

- **Withholding-tax tracking, the effective-WHT KPI, and the Swiss DA-1 reclaim card.**
  The cards are visible in the app but flagged "under development" — treat as
  informational previews, not a tax filing source.

## Planned

- Real broker-declared ex-dividend calendar **+ macOS notifications** before ex-date and
  on dividend cuts / raises (replaces the historical-cadence projection)
- Watchlist tab — pre-purchase research dock next to Holdings
- DA-1 + 1099-DIV tax-year CSV exports — broaden the tax export surface
- Allocation by **market value** — sector and geography lenses
- Reinvestment simulator — "what if I'd DRIP'd from date X"
- Expense ratio & TTM yield per instrument
- Windows build
- License key activation (yearly subscription)

## Considering

- Linux build
- Optional encrypted iCloud backup of the local database
- Multi-portfolio profiles in a single install
- iOS / iPad read-only companion
- Annual income report PDF (for your accountant or self)
- Owner-earnings + implied-cost-of-capital lens (Buffett / Damodaran)
- Signed model portfolios (downloadable, community)
- Monte-Carlo on forward income + sequence-of-returns (Kitces lens)

---

© 2026 Chris Wenk. All rights reserved.
