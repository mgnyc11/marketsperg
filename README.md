# MarketSperg v1.0 📊

A TradingView Pine Script indicator that replicates the MarketSurge/IBD data panel as a chart overlay. Get CANSLIM ratings, earnings data, relative strength, and a full buy checklist — right on your chart.

![Pine Script v6](https://img.shields.io/badge/Pine%20Script-v6-blue)
![License](https://img.shields.io/badge/license-MIT-green)

## Features

### 📊 Ratings Panel
- **Composite Rating** — weighted blend of RS + EPS + fundamentals (0-99)
- **RS Rating** — relative strength vs S&P 500 (weighted multi-timeframe)
- **EPS Rating** — based on quarterly YoY earnings growth
- **SMR Rating** — Sales, Margins, ROE composite (A-D)
- **Acc/Dis Rating** — 50-day up/down volume ratio (A-E)
- **P/E, ROE, 52-week range**
- **Trend Template** — Minervini's moving average stacking check (PASS/FAIL)

### 📈 Earnings Section
- Annual EPS + YoY growth %
- Last 4 quarters EPS with year-over-year % change
- **EPS Acceleration** detection (is growth speeding up?)
- Quarterly revenue + growth %

### 💰 Financials
- Net margin, Debt/Equity ratio
- Annual revenue, net income

### ✅ CANSLIM Checklist
Automatic 6-point O'Neil checklist:
- **C** — Current quarterly EPS ≥ 25%
- **A** — Annual EPS growth ≥ 25%
- **N** — Near new high (within 10% of 52-week high)
- **S** — Supply/demand (U/D volume ratio ≥ 1.0)
- **L** — Leader (RS Rating ≥ 80)
- **I** — Institutional quality (Composite ≥ 70)

Score: **BUY ZONE** (5-6) / **WATCH** (3-4) / **AVOID** (0-2)

### 📉 Chart Overlays
- **S&P 500 comparison line** — percentage-anchored scaling (black, semi-transparent)
- **RS Line** — relative strength vs benchmark (blue)
- **Moving Averages** — 21 EMA (pink), 50 DMA (red), 150 DMA (orange), 200 DMA (black)
- **EPS surprise markers** — on-chart labels at earnings dates

## Installation

1. Open [TradingView](https://www.tradingview.com) and go to any chart
2. Click **Pine Editor** (bottom panel)
3. Copy the contents of `marketsperg_v1.0.pine`
4. Paste into the Pine Editor
5. Click **Add to Chart**

## Settings

All sections are toggleable in the indicator settings:
- Show/hide Ratings, Earnings, Financials panels
- Show/hide individual MAs (21 EMA, 50 DMA, 150 DMA, 200 DMA)
- Show/hide RS Line and S&P 500 overlay
- Show/hide EPS markers on chart
- Change RS benchmark (default: SPY)
- Adjust text size (tiny/small/normal)

## Screenshots

*Coming soon*

## How Ratings Are Calculated

**RS Rating (1-99):** Weighted relative performance vs benchmark:
- 40% last quarter (63 bars)
- 20% each for prior 3 quarters (126, 189, 252 bars)
- Normalized to 1-99 scale

**EPS Rating:** Based on most recent quarterly YoY EPS growth:
- \>100% → 95 | >50% → 85 | >25% → 75 | >10% → 60 | >0% → 45

**Composite Rating:** `(RS × 0.4) + (EPS × 0.4) + (50 × 0.2)`

**Acc/Dis Rating:** 50-day up/down volume ratio:
- A (≥1.5) | B+ (≥1.2) | B (≥1.0) | C+ (≥0.8) | C (≥0.6) | D (≥0.4) | E

**SMR Rating:** Combined score from revenue growth, profit margin, and ROE.

## Known Limitations

- Financial data comes from FactSet via TradingView's `request.financial()` — may lag by a few days after earnings
- IBD's exact rating algorithms are proprietary; our calculations are approximations
- Fund ownership % and institutional sponsor data not available in Pine Script
- `syminfo.exchange` not available in Pine v6 (removed from panel)
- EPS estimates / forward guidance not available via `request.financial()`

## Requirements

- TradingView account (free tier works, Premium recommended for more data)
- Pine Script v6 compatible

## Contributing

PRs welcome! Ideas for v1.1+:
- [ ] Industry group RS ranking
- [ ] Earnings date countdown
- [ ] Volume dry-up detection (tight areas)
- [ ] Pivot point detection and labeling
- [ ] Dark mode panel option
- [ ] Custom color schemes

## License

MIT License — see [LICENSE](LICENSE)

## Credits

Inspired by [MarketSurge](https://marketsurge.investors.com/) by Investor's Business Daily and William O'Neil's CANSLIM methodology.

Built with 🤖 by Wilson & Michael.
