---
title: "DeFi Risk Monitoring Toolkit"
permalink: /project/
layout: single
classes: wide
toc: true
toc_label: "On this page"
toc_icon: "list"
header:
  overlay_color: "#000"
  overlay_filter: "0.45"
  teaser: /assets/images/toolkit/cover.png
  # overlay_image: /assets/images/toolkit/cover-wide.png
excerpt: "A practical toolkit to monitor DeFi risk exposure, CLMM positions, and performance over time — built with a market-maker mindset."
---

{% capture disclaimer %}
**Disclaimer**: This project is for educational and personal analytics purposes. It is **not** financial advice.
{% endcapture %}
<div class="notice--warning">
  {{ disclaimer | markdownify }}
</div>

## Why this toolkit exists

Most DeFi dashboards show *positions*. Few show **risk**.

This toolkit is designed to answer, at a glance:
- *What can hurt me today?* (liquidation, out-of-range, leverage drift, concentration)
- *What is working?* (fees vs IL, carry vs price move, real net performance)
- *What should I do next?* (actionable alerts + prioritized checklist)

<div class="notice--info">
  <strong>TradFi bridge:</strong> Think of it as a lightweight “risk desk” for DeFi — built for CLMM LPs, lending/borrowing strategies, and on-chain market making.
</div>

---

## What it covers

{% assign feature_row = site.data.feature_rows.defi_toolkit %}
{% include feature_row id="defi_toolkit" type="center" %}

---

## Modules

### 1. Position Monitoring (CLMM / LP / MM)
- Live state: in-range/out-of-range, range distance, inventory composition
- Operational workflow: rebalance triggers, harvest cadence, deployment sizing
- “MM mindset”: inventory risk, price range risk, fee volatility

**Go deeper →** [Position Monitoring](/testDeFi/project/positions/)

### 2. Risk Overview
- Lending/borrowing health: LTV monitoring, liquidation distance, collateral concentration
- CLMM risk: out-of-range probability cues, inventory drift, exposure by token
- Portfolio exposure: token, protocol, chain, stablecoin issuer, bridge/oracle dependencies

**Go deeper →** [Risk Overview](/testDeFi/project/category-1/)

### 3. Performance Overview
- Net performance over time: **fees – IL – funding – borrow cost**
- Per-position scorecards: realized vs unrealized, volatility regimes, fee consistency
- Strategy lens: range width, rebalancing frequency, fee-to-risk efficiency

**Go deeper →** [Performance Overview](/testDeFi/project/performance/)

---

## Key metrics (the “risk desk” layer)

**Lending / Borrowing**
- Current LTV, liquidation LTV, buffer (%), stress-LTV (scenario)
- Borrow APR vs Supply APR vs net carry
- Collateral correlation / concentration (top 3)

**CLMM / LP**
- In-range status + distance to bounds
- Inventory split (token0/token1) and drift
- Fee velocity (daily/weekly), volatility proxy
- Net PnL decomposition (fees vs IL)

**Portfolio**
- Exposure by token / protocol / chain
- “Single-point-of-failure” flags: stable issuer, bridge, oracle dependency

---

## Architecture (simple, reliable, extendable)

- **Data sources**: on-chain APIs / subgraphs / protocol endpoints (depending on module)
- **Storage**: Google Sheets (fast iteration) + optional exports
- **Logic**: formulas + scripts (Apps Script / Python optional)
- **Outputs**: dashboards, alerts, and weekly reports

<div class="notice--success">
  <strong>Design rule:</strong> Every metric must lead to a decision: <em>hold / rebalance / deleverage / exit / add</em>.
</div>

---

## Roadmap

- [ ] V1: risk overview (LTV + CLMM range monitoring + exposure table)
- [ ] V2: performance attribution (fees/IL/carry) with weekly snapshots
- [ ] V3: alerting system (threshold + anomaly detection)
- [ ] V4: automated report + “playbook” per strategy

---

## About the author

I come from a TradFi post-trade / market infrastructure background and built this toolkit to apply **risk discipline** to DeFi strategies (CLMM LPing, lending/borrowing, and on-chain market making).

**Links:** [GitHub](https://github.com/) · [Twitter](https://twitter.com/) · [LinkedIn](https://www.linkedin.com/)
