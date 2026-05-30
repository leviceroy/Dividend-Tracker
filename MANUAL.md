# Dividend Tracker — User Manual

A practical walkthrough of the app, written for serious income investors. Cross-linked
with the [README](README.md).

---

## Getting started

### Install
1. Download the latest `.dmg` from
   [**Releases**](https://github.com/leviceroy/Dividend-Tracker/releases/latest).
2. Drag **Dividend Tracker** to `/Applications`.
3. First launch: **right-click → Open → Open** (Gatekeeper warning; the app isn't Apple-
   notarized yet — the cryptographic *update* signature is separate and is verified by the
   app itself).

### Where your data lives
A single SQLite file at
`~/Library/Application Support/com.chrismeiam.dividend-tracker/dividends.db`.
Back it up like any other file. Reveal it in Finder from **Admin → DATABASE → Open in
Finder**.

### Demo data
The app starts empty. Open **Admin → DEMO DATA → Load demo data** to seed two sample
accounts (Fidelity USD, Swissquote CHF), four holdings, and five dividends. Explore every
tab with realistic numbers, then **Delete demo data** to clear it — only the demo-tagged
rows are removed. Loading is blocked once any transaction exists, so the demo can never
mix with your real data.

---

## The six tabs

### 1. Dashboard

The income command center. Three KPI rows, an income-target progress strip, two charts,
breakdowns, a lifetime cumulative-income curve, an allocation chart, and the Top-10
dividend-payer treemap.

<p align="center"><img alt="Dashboard" src="images/dashboard.png" width="92%"></p>

**Realized income** — TTM, YTD, MTD, average monthly (with median month for lumpy
portfolios).

**Forward income** — annual run-rate on the *trailing-12-month DPS sum* (not "latest
payment × frequency"), with an "indicated" value visible on hover that uses the most
recent payment × frequency for a snapshot of the latest raise. Plus forward monthly,
yield-on-cost (on the reporting-ccy amount actually invested), and current yield.

**Valuation** — live market value, unrealized P&L, realized P&L on closed positions, and
total return (unrealized + realized + lifetime dividends). Refresh prices via the
↻ button.

**Dividend growth** — income growth YoY, average 3-year DPS CAGR across holdings,
consecutive-increase streaks, and dividend cuts.

**FIRE income target** — set it in **Admin → GOALS**; a progress bar shows forward annual
vs target with the remaining gap (monthly).

**Charts** — Monthly Income (last 24 months), Forward Calendar (next 12 months, projected
at historical cadence), Cumulative Income (lifetime), Allocation by value (sector), and
the Top-10 payer treemap (area = income, color = DPS growth — green growing, slate flat,
red cut).

<p align="center"><img alt="Dashboard charts & treemap" src="images/dashboard-charts.png" width="92%"></p>

> ⚠️ **Withholding-tax cards (WHT PAID, WHT %, US WHT RECOVERABLE) are under development.**
> Treat them as informational previews, not a tax filing source.

### 2. Dividends

Every payment in a year/month tree. Columns: pay date, ticker, account, description,
shares-at-pay-date, DPS, gross, withholding, net, source currency, FX rate, reporting-ccy
local net, effective WHT %, per-row YoC (split-adjusted). Filters: time range, account,
currency, free-text search. Toggle FX display mode (at-current vs at-transaction) in the
top-right.

<p align="center"><img alt="Dividends ledger" src="images/dividends.png" width="92%"></p>

**Adding a dividend** — open the form with **+ NEW (n)**:

- Pay date is the only required date; **ex date** defaults to pay-date and can be auto-
  fetched from Yahoo via the ↻ button.
- Pick **account** and **ticker**; if the ticker is new you can create the instrument
  inline.
- Enter **net** (what hit your account) and **WHT**; gross is computed.
- **FX rate** is the source→reporting rate at pay date. If a stored rate is missing the
  app uses the historical-rate table.
- Flags: **Qualifying dividend**, **Reinvested (DRIP)**, **Special (one-off)**.
- **DRIP**: ticking "Reinvested" reveals a **reinvest price** field. With both set, the
  app auto-creates a linked "buy" transaction (shares = net ÷ price, dated pay-date+1) so
  your holdings, WAC, cost basis, and future forward income all reflect the reinvestment.

<p align="center"><img alt="Dividend entry form" src="images/dividends-form.png" width="78%"></p>

### 3. Holdings

What you own, what it pays, what it cost — derived from your transactions, not entered
directly.

<p align="center"><img alt="Holdings" src="images/holdings.png" width="92%"></p>

Columns: account, ticker, name, native currency, shares, average cost, native cost,
**Cost (reporting ccy)** at the FX you actually paid at purchase, **Fwd Annual** (TTM DPS
× current shares × FX), **YoC** (Fwd Annual ÷ invested cost). The footer shows portfolio
totals — default sort by reporting-currency cost.

To buy, sell, or split a position, use the Transactions tab — Holdings recomputes
automatically.

### 4. Transactions

The ledger that everything else derives from. Buys, sells, opening balances, **stock
splits**, and **DRIP-generated buys** (linked back to the parent dividend).

<p align="center"><img alt="Transactions" src="images/transactions.png" width="92%"></p>

**Add a buy/sell/opening balance** — open the form with **+ NEW (n)**:

<p align="center"><img alt="Transaction form" src="images/transactions-form.png" width="78%"></p>

- **Type** — Buy adds to WAC; Sell reduces shares (WAC unchanged); Opening balance seeds
  a legacy / transferred-in position.
- **Trade date** — required. **Settle date** auto-fills to T+1 on the instrument's market
  calendar (US NYSE / Swiss SIX, holidays through 2030 included). Override if you like.
- **Account** + **Ticker** — both required. New tickers can be created inline.
- **Shares**, **Price / share** (native), **Fee** (optional).
- **FX rate (native → reporting)** — appears only for foreign instruments. Click **↻
  fetch** to pull the historical rate at the trade date. The reporting-ccy **cost basis**
  preview updates live.
- Save (⌘+S) — holdings recompute automatically.

**Add a stock split** — pick type **Stock split**; enter the ratio (e.g. *2 new : 1 old*
for a 2:1 forward split, or *1 new : 10 old* for a 1:10 reverse). Shares scale by the
ratio and WAC inversely, so total cost basis stays unchanged. Historical per-share
dividend amounts are automatically split-adjusted everywhere they're used (forward income,
CAGR, growth streaks).

**DRIP-generated buys** are flagged with `__DEMO__`-style notes saying "DRIP
reinvestment" and are **delete-protected** here — manage them from the parent dividend in
the Dividends tab.

### 5. Accounts

Each broker account (name, broker, account currency, type, country) with TTM income and
the live market value of its holdings (priced positions only). Sortable by value.

<p align="center"><img alt="Accounts" src="images/accounts.png" width="92%"></p>

An account's currency is just its *reference* currency — you can still hold securities in
any currency inside it. (Schwab account, USD reference, holding a CHF-denominated ETF
works fine.)

### 6. Admin

<p align="center"><img alt="Admin" src="images/admin.png" width="92%"></p>

**Portfolio**
- *Reporting currency* — every dashboard KPI converts to this.
- *FX display mode* — **at-current** (today's spot rate; best for net-worth tracking) or
  **at-transaction** (pay-date rate; required for tax reporting).
- *FX provider* — Frankfurter (ECB) primary with Yahoo Finance fallback (recommended),
  ECB only, Yahoo only, or **Manual** (disable auto-fetch entirely).

**Goals**
- *Annual income target (FIRE)* — the dashboard shows a progress strip toward this goal.

**Demo data**
- *Load demo data* — seed the sample portfolio (only when no transactions exist).
- *Delete demo data* — remove only demo-tagged rows.

**Database**
- File location (with reveal-in-Finder). Back it up like any other file.

**About**
- App version, copyright, stack, source link, **EULA**, **Release notes** (links to the
  public release page), and **Check for updates** — runs the same updater the app does on
  launch and shows the latest release notes inside a dialog.

---

## Concepts

### Reporting currency & FX modes
Your *reporting currency* is the lens everything is shown through. For non-reporting
currencies the app converts in one of two modes:
- **At-current** — every amount is revalued at today's spot rate. The right view for
  "what's my portfolio worth now," net-worth tracking, and forward projections.
- **At-transaction** — each dividend converts at its **pay-date** FX. The right view for
  **tax reporting**: the figure that actually hit your bank is preserved.

Toggle on the Dashboard banner and in the Dividends tab top-right. Yield-on-cost always
uses the FX **at purchase** (the reporting-currency actually invested), not today's spot.

### Forward income: TTM vs Indicated
Forward annual income is the **trailing-12-month sum of per-share dividends × current
shares** — which automatically captures seasonality, frequency changes, and dividend
growth, and excludes specials. A second figure, **Indicated** (latest × frequency), is
visible on hover for a quick read on the most recent raise.

### Yield on cost (YoC)
*Forward annual income ÷ reporting currency actually invested.* The denominator is built
from your real lot prices and the FX at each purchase (not today's spot applied to old
cost). Same number on the Dashboard, on Holdings, and on the per-row Dividends YoC.

### Splits
A split row scales shares ×ratio and WAC ÷ratio so total cost is preserved. Historical
per-share DPS is divided by the cumulative split factor for every later calc (forward
income, CAGR, growth streaks) — so a 2:1 split doesn't look like a 50% dividend cut.

### Special dividends
A "special" dividend is one-off (year-end specials, capital returns). The flag excludes
them from forward income and DPS-growth calcs while still counting them as realized cash.

### DRIP
Tick "Reinvested" + enter a reinvest price on a dividend. The app materializes a linked
"buy" (shares = net ÷ price, dated pay-date+1 so it doesn't distort that dividend's own
per-share calc), and holdings + WAC + cost basis + future forward income update
automatically. Delete or edit the dividend — the linked buy follows.

---

## Updates

Every launch the app checks the public release feed (`latest.json` in the
**Dividend-Tracker** repo's releases), and prompts to install a newer **cryptographically
signed** version with the release notes. Verify → download → install → relaunch happens
automatically. You can also trigger a check anytime from **Admin → Check for updates**,
and open the full release notes page from **Admin → Release notes**.

## Privacy

- Local-first. Portfolio data is stored only in your local SQLite file.
- The app contacts public, free services for read-only data only: **Frankfurter** (ECB
  exchange rates) and **Yahoo Finance** (market prices, dividend history). It also
  contacts **GitHub** to check for updates. That's it — no telemetry, no account, no
  broker login.
- Back up `~/Library/Application Support/com.chrismeiam.dividend-tracker/dividends.db` and
  you've backed up your portfolio.

## Withholding tax (under development)

Withholding-tax tracking, the effective-rate KPI, the "US WHT recoverable" / Swiss DA-1
reclaim card, and tax-year exports are **under active development** and currently shown
in the app as informational previews only. Verify any tax figure against your broker
statements and consult your tax adviser before filing. See the
[Roadmap](ROADMAP.md) for status.

---

© 2026 Chris Wenk. All rights reserved. See the [EULA](EULA.md).
