# Dividend Tracker

A fast, local-first dividend journal for serious income investors — multi-account,
multi-currency, withholding-aware, with live valuation and dividend-growth analytics.
Your data stays on your Mac in a single SQLite file; nothing is uploaded.

> This repository hosts the **downloadable macOS builds** and release notes.
> The source code is maintained privately.

## Download

Grab the latest `.dmg` from the [**Releases**](https://github.com/leviceroy/Dividend-Tracker/releases/latest) page.

Currently free to download during the beta.

## Install (macOS)

The app is not yet notarized with an Apple Developer ID, so macOS Gatekeeper will
warn on first launch. To open it:

1. Move **Dividend Tracker.app** to `/Applications`.
2. Right-click the app → **Open** → **Open** (only needed the first time), or run:
   ```
   xattr -dr com.apple.quarantine "/Applications/Dividend Tracker.app"
   ```

Universal build — runs natively on Apple Silicon and Intel.

## Updates

The app checks for new releases on launch and offers to update in-place
(downloads, verifies a cryptographic signature, installs, relaunches). You can
also trigger a check anytime from **Admin → Updates**.

## What it does

- Multi-account, multi-currency dividend ledger (reporting currency of your choice)
- Live market value, current yield, unrealized & realized P&L, total return
- Forward income (trailing-12-month DPS), yield-on-cost on capital actually invested
- Dividend CAGR, growth streaks, and cut detection
- Withholding-tax tracking with Swiss DA-1 reclaim
- Stock splits, special dividends, and DRIP handled correctly
- FIRE / income-target progress

## Feedback

Found a bug or want a feature? Open an [issue](https://github.com/leviceroy/Dividend-Tracker/issues/new/choose).
See the [roadmap](ROADMAP.md) for what's planned.

## License

Proprietary — free to use during the beta. See the [EULA](EULA.md). The Software
is licensed, not sold; redistribution and reverse engineering are not permitted.

---
© Chris Wenk. All rights reserved.
