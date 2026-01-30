# TEMPT Profile: Stock Research

## Metadata

| Field | Value |
|-------|-------|
| **Name** | Stock Research |
| **Version** | 1.0 |
| **Created** | 01-30-2026 |
| **Freshness Class** | real-time |
| **Primary Use Case** | Individual stock analysis, portfolio decisions, market timing, earnings analysis |

---

## Trigger Keywords

### Tier 1 — Unambiguous (Auto-load silently)

```
MSFT, AAPL, GOOGL, GOOG, AMZN, META, NVDA, TSLA, JPM, BAC, WFC, GS, 
XOM, CVX, JNJ, PFE, UNH, HD, WMT, PG, KO, PEP, MCD, DIS, NFLX, AMD,
INTC, CRM, ORCL, IBM, CSCO, QCOM, TXN, AVGO, ADBE, PYPL, SQ, COIN,
ticker, NYSE, NASDAQ, S&P 500, S&P500, Dow Jones, DJIA, Russell 2000,
stock price, share price, market cap, earnings call, EPS, P/E ratio,
10-K, 10-Q, 8-K, SEC filing, dividend yield, stock split, buyback,
GLDM, GLD, SLV, IAU, XLP, XLF, XLE, XLK, SPY, QQQ, IWM, VTI, VOO
```

### Tier 2 — Likely (Auto-load with confirmation)

```
stock, shares, equity, portfolio, holdings, position, long, short,
bull, bear, rally, correction, crash, volatility, VIX, options,
calls, puts, strike price, expiration, margin, leverage, hedge,
analyst, upgrade, downgrade, price target, buy rating, sell rating,
earnings, revenue, guidance, beat, miss, consensus, estimate,
trading, volume, bid, ask, spread, liquidity, float, outstanding
```

### Tier 3 — Ambiguous (Ask if sole match)

```
rate, return, yield, value, growth, income, price, cost, profit,
loss, gain, performance, benchmark, index, market, investment
```

---

## Freshness Requirements

| Data Type | Freshness Threshold | Auto-Inject |
|-----------|---------------------|-------------|
| Stock price / quote | real-time | "today [current date]" |
| Market indices | real-time | "today [current date]" |
| Trading volume | real-time | "today" |
| Earnings reports | <7 days post-release | "[company] earnings [quarter] [year]" |
| Analyst ratings | <30 days | "latest" or "[current month] [year]" |
| SEC filings | <7 days post-filing | "recent" or "[year]" |
| Dividend info | <30 days | "[year]" |
| Company news | <24 hours | "today" or "latest" |
| Historical data | any | [no injection] |

**Default freshness:** <24 hours

**Stale handling:** Flag ⚠️ STALE SOURCE → re-query with date → note if still stale

---

## Source Priority

1. **Official Exchange Data** — NYSE, NASDAQ official quotes
2. **SEC EDGAR** — 10-K, 10-Q, 8-K, Form 4
3. **Company Investor Relations** — Earnings releases, presentations
4. **Major Financial News** — Reuters, Bloomberg, WSJ, FT
5. **Analyst Research** — FactSet, Refinitiv consensus

**Avoid:** Anonymous forums, promotional sites, stale sources

---

## Additional BB Pairs

| Dimension | Builder | Breaker | Trigger |
|-----------|---------|---------|---------|
| Market Timing | Momentum Trader | Contrarian Analyst | buy, sell, timing |
| Volatility | Volatility Analyst | Black Swan Hunter | VIX, options, hedge |
| Valuation | Fundamental Analyst | Bubble Detector | valuation, P/E, fair value |
| Earnings Quality | Earnings Optimizer | Accounting Skeptic | earnings, EPS, revenue |
| Sector Risk | Sector Specialist | Contagion Analyst | sector-focused queries |

---

## Anchoring Instructions

- **Always include ticker symbol** in searches
- **Append "today" or current date** for price queries
- **Include "SEC" or "EDGAR"** for filings
- **Cross-reference** prices with major source

### Domain-Specific Flags

| Flag | Condition |
|------|-----------|
| ⚠️ MARKET HOURS | Query during trading hours |
| ⚠️ AFTER HOURS | Query outside market hours |
| ⚠️ EARNINGS PENDING | Earnings within 7 days |
| ⚠️ HIGH VOLATILITY | VIX > 25 or stock > 5% move |

---

## Conflict Behavior

| Conflict | Resolution |
|----------|------------|
| Freshness | This profile wins (most restrictive) |
| Sources | Merge with other profiles |
| BB Pairs | Additive |

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 01-30-2026 | Initial profile |
