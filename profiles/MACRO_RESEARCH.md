# TEMPT Profile: Macro Research

## Metadata

| Field | Value |
|-------|-------|
| **Name** | Macro Research |
| **Version** | 1.0 |
| **Created** | 01-30-2026 |
| **Freshness Class** | weeks |
| **Primary Use Case** | Economic analysis, policy research, systemic trends, geopolitical impacts, currency/rates analysis |

---

## Trigger Keywords

### Tier 1 — Unambiguous (Auto-load silently)

```
Federal Reserve, Fed, FOMC, Jerome Powell, ECB, Christine Lagarde,
Bank of Japan, BOJ, Bank of England, BOE, central bank,
GDP, gross domestic product, unemployment rate, CPI, inflation rate,
PPI, PCE, nonfarm payrolls, jobs report, labor market,
fiscal policy, monetary policy, quantitative easing, QE, QT,
interest rate decision, rate hike, rate cut, basis points, bps,
Treasury yield, 10-year yield, yield curve, inverted yield curve,
de-dollarization, dollar index, DXY, currency crisis, fiat,
sovereign debt, national debt, deficit, debt ceiling,
BLS, Bureau of Labor Statistics, BEA, Bureau of Economic Analysis,
trade deficit, trade war, tariff, sanctions, BRICS,
recession, soft landing, hard landing, stagflation, deflation,
Two Economies, systemic risk, wealth divergence
```

### Tier 2 — Likely (Auto-load with confirmation)

```
economy, economic, macroeconomic, macro, policy, government,
inflation, deflation, rates, bonds, treasuries, sovereign,
currency, forex, exchange rate, dollar, euro, yen, yuan,
employment, wages, labor, workforce, productivity,
growth, contraction, expansion, cycle, downturn, recovery,
banking, financial system, liquidity, credit, lending,
globalization, deglobalization, reshoring, supply chain,
demographics, population, aging, migration
```

### Tier 3 — Ambiguous (Ask if sole match)

```
rate, rates, policy, government, market, crisis, risk,
debt, deficit, balance, capital, flow, trend
```

---

## Freshness Requirements

| Data Type | Freshness Threshold | Auto-Inject |
|-----------|---------------------|-------------|
| Breaking policy news | <24 hours | "today" or "latest" |
| Economic data releases | <7 days post-release | "[indicator] [month] [year]" |
| Fed/central bank statements | <7 days | "[institution] [month] [year]" |
| Policy analysis | <4 weeks | "[year]" or "recent" |
| Economic research/papers | <6 months | "[year]" |
| Structural trends | <12 months | "[year]" or no injection |
| Historical context | any | [no injection] |

**Default freshness:** <4 weeks

**Stale handling:** Flag for policy-sensitive topics; acceptable for structural analysis

---

## Source Priority

1. **Official Government Sources** — Primary data authority
   - Federal Reserve (federalreserve.gov, FRED)
   - Bureau of Labor Statistics (bls.gov)
   - Bureau of Economic Analysis (bea.gov)
   - Treasury Department
   - Congressional Budget Office

2. **Central Bank Communications** — Policy signals
   - FOMC statements, minutes, dot plots
   - Fed speeches (Fed Listens, Jackson Hole)
   - ECB, BOJ, BOE official communications

3. **Major Economic News** — Context and analysis
   - Reuters, Bloomberg, WSJ, Financial Times
   - The Economist

4. **Research Institutions** — Deep analysis
   - Brookings, NBER, Peterson Institute
   - IMF, World Bank, BIS reports
   - Academic papers (SSRN, NBER working papers)

5. **Market Commentary** — Interpretation
   - Major bank research (Goldman, JPM, Morgan Stanley)
   - Named economists with track records

**Avoid:** 
- Partisan political sources for economic data
- Sources that don't cite primary data
- Outdated projections presented as current

---

## Additional BB Pairs

| Dimension | Builder | Breaker | Trigger |
|-----------|---------|---------|---------|
| Policy Impact | Policy Optimist | Unintended Consequences Analyst | Fed, policy, stimulus |
| Systemic Risk | Stability Analyst | Systemic Risk Hunter | banking, financial system |
| Currency | Currency Strategist | Fiat Skeptic | dollar, currency, de-dollarization |
| Inflation | Inflation Modeler | Inflation Skeptic | CPI, inflation, prices |
| Debt Sustainability | Fiscal Analyst | Debt Crisis Modeler | debt, deficit, sovereign |
| Geopolitical | Geopolitical Analyst | Sanction/Trade War Simulator | BRICS, tariff, sanctions |

### Pair Descriptions

**Policy Impact: Policy Optimist / Unintended Consequences Analyst**
- Builder: Policy will achieve stated goals, transmission mechanisms work
- Breaker: Second-order effects, lag effects, policy errors, political constraints
- Trigger: Fed, FOMC, monetary policy, fiscal policy, stimulus

**Systemic Risk: Stability Analyst / Systemic Risk Hunter**
- Builder: System is resilient, safeguards work, contagion contained
- Breaker: Hidden leverage, interconnections, correlation in crisis, liquidity spirals
- Trigger: banking, financial system, crisis, contagion, stability

**Currency: Currency Strategist / Fiat Skeptic**
- Builder: Dollar hegemony, reserve currency status, relative strength
- Breaker: De-dollarization trends, alternative systems, confidence loss
- Trigger: dollar, DXY, de-dollarization, currency, BRICS, yuan

**Inflation: Inflation Modeler / Inflation Skeptic**
- Builder: Models predict path, expectations anchored, transitory factors
- Breaker: Model failures, measurement issues, regime changes, political pressure
- Trigger: CPI, inflation, PCE, prices, deflation

**Debt Sustainability: Fiscal Analyst / Debt Crisis Modeler**
- Builder: Debt manageable at current rates, growth solves, reserve currency privilege
- Breaker: Interest expense spiral, crowding out, confidence thresholds, historical parallels
- Trigger: national debt, deficit, debt ceiling, sovereign, fiscal

---

## Anchoring Instructions

### Search Query Modifications

- **Include institution name** for policy queries (e.g., "Federal Reserve January 2026")
- **Add data release date** for economic indicators (e.g., "CPI December 2025")
- **Specify "official" or source name** to prioritize primary sources
- **For trends, include timeframe** (e.g., "de-dollarization trends 2024-2026")

### Verification Requirements

- Cross-reference economic data with FRED or official source
- Verify Fed statements against official transcript
- Check projection dates — old forecasts may be outdated
- Note when analysis predates significant policy changes

### Domain-Specific Flags

| Flag | Condition |
|------|-----------|
| ⚠️ DATA RELEASE PENDING | Major economic data within 7 days |
| ⚠️ FOMC PENDING | Fed meeting within 14 days |
| ⚠️ PROJECTION DATED | Source projections >6 months old |
| ⚠️ POLICY SHIFT | Recent policy change may invalidate older analysis |

---

## Conflict Behavior

| Conflict | Resolution |
|----------|------------|
| Freshness | Yield to Stock Research (if combined) for price data; macro freshness for policy |
| Sources | Government/central bank sources take priority |
| BB Pairs | Additive |

---

## Example Activations

**Example 1: Policy analysis**
```
Query: "How will the Fed's rate decision affect Treasury yields?"
Detection: Tier 1 — Fed, rate decision, Treasury yields
Loaded: Macro Research
Freshness: <7 days for Fed statements, <24 hours for yield data
BB Pairs: Policy Impact, Inflation
```

**Example 2: Structural trend**
```
Query: "Is de-dollarization accelerating based on BRICS developments?"
Detection: Tier 1 — de-dollarization, BRICS
Loaded: Macro Research
Freshness: <4 weeks (structural trend)
BB Pairs: Currency, Geopolitical
```

**Example 3: Combined with Stock**
```
Query: "How does the Fed rate decision affect my MSFT position?"
Detection: Macro (Fed rate) + Stock (MSFT, position)
Conflict: Stock freshness for MSFT price; Macro freshness for Fed analysis
BB Pairs: [Macro: Policy Impact] + [Stock: Market Timing, Valuation]
```

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 01-30-2026 | Initial profile |
