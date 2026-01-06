---
title: "DeFi Risk & Performance Framework"
permalink: /project/
layout: single
classes: wide
author: false
author_profile: false
sidebar: false
toc: true
toc_label: "On this page"
toc_icon: "list"
header:
  overlay_color: "#000"
  overlay_filter: "0.45"
  teaser: /assets/images/toolkit/cover.png
  # overlay_image: /assets/images/toolkit/cover-wide.png
excerpt: "A structured approach to monitoring liquidity, risk exposure and performance across DeFi positions."
---

<style>
  /* Supprime les marges et force la largeur maximale sur le conteneur principal */
  .layout--single .archive, 
  .layout--single .page__content, 
  .layout--single .page__inner-wrap {
    width: 100% !important;
    max-width: 100% !important;
    padding-right: 0 !important;
  }

  /* Si vous voulez aussi réduire l'espace blanc en haut */
  .page {
    width: 100% !important;
    padding-right: 0 !important;
  }
</style>


{% capture disclaimer %}
**Disclaimer**: This project is for educational and personal analytics purposes. It is **not** financial advice.
{% endcapture %}
<div class="notice--warning">
  {{ disclaimer | markdownify }}
</div>

## Overview

The DeFi Risk Monitoring Toolkit is a personal, research-driven framework designed to monitor, analyze, and manage risk across decentralized finance strategies, with a strong focus on capital efficiency, liquidity provision, and market making mechanics.

Built from real-world DeFi usage, this framework aims to bridge the gap between on-chain execution and institutional-style risk monitoring, inspired by practices found in traditional trading, treasury, and market making desks.

The objective is simple:

👉 turn fragmented DeFi positions into a coherent, risk-aware portfolio view.

## Why this toolkit exists

Most DeFi dashboards show *positions*. Few show **risk**.

This toolkit is designed to answer, at a glance:
- *What can hurt me today?* (liquidation, out-of-range, leverage drift, concentration)
- *What is working?* (fees vs IL, carry vs price move, real net performance)
- *What should I do next?* (actionable alerts + prioritized checklist)

<div class="notice--info">
  <strong>TradFi bridge:</strong> Think of it as a lightweight “risk desk” for DeFi, built for CLMM LPs, lending/borrowing strategies, and on-chain market making.
</div>

<figure>
  <img src="/testDeFi/assets/images/framework-flow.png" alt="Project dashboard">
  <figcaption><em>Framework flow</em></figcaption>
</figure>

## What it covers

### 1. Position Monitoring (CLMM / LP)
Track the live state of active DeFi positions.
- In-range/out-of-range status
- Inventory composition (token0 / token1) and position value
- Lending/borrowing health: LTV monitoring, liquidation distance

*Designed to support day-to-day LP and CLMM position management.*

**Go deeper →** [Position Monitoring](/testDeFi/project/positions/)

### 2. Risk Overview
Agregates risk indicators for inactive positions.
- Opportunity cost
- Call-to-action indicator
- Lending/borrowing health preview

*Measures how inactive position improves risk.*

**Go deeper →** [Risk Overview](/testDeFi/project/risk/)

### 3. Performance Overview
Measures real LP performance beyond headline APR.
- Net performance over time (position value + fees).
- Fee management with harvest cadence per pool
- Daily and cumulative performance tracking

*Focuses on economic efficiency, not advertised yields.*

**Go deeper →** [Performance Overview](/testDeFi/project/performance/)

## Key metrics (the “risk desk” layer)

**Lending / Borrowing**
- Current LTV, liquidation LTV

**CLMM / LP**
- In-range status
- Inventory split (token0/token1) and drift
- Fee velocity (daily/weekly), volatility proxy
- Net PnL decomposition (fees vs IL)

**Portfolio**
- Exposure by token / protocol / chain


## Architecture (simple, reliable, extendable)
- **Storage**: Google Sheets (fast iteration) + optional exports
- **Logic**: formulas + scripts (Apps Script)
- **Outputs**: dashboards, alerts, and weekly reports

<div class="notice--success">
  <strong>Design rule:</strong> Every metric must lead to a decision: <em>hold / rebalance / deleverage / exit / add</em>.
</div>

## Roadmap
- [ ] V1: risk overview (LTV + CLMM range monitoring + exposure table)
- [ ] V2: performance attribution (fees/IL/carry) with weekly snapshots
- [ ] V3: alerting system (threshold + anomaly detection)
- [ ] V4: automated report + “playbook” per strategy
