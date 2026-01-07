---
layout: default
title: "Operational Risk"
parent: "DeFi Risk & Performance Framework"
nav_order: 2
---

# Operational Risk
{: .no_toc }

<br>

We introduce this module as an operational monitoring layer built to manage idle positions.

{: .note }
> This risk view is intentionally simple and action-oriented.

---

## Purpose
-	What is the status of the portfolio?
-	Do I have inactive positions?
-	What is the opportunity cost?
-	What action should I take NOW?

---

![Risk Monitoring Dashboard]({{ site.baseurl }}/assets/images/risk/risk.png)
{: .mx-auto }
*Operational Risk Monitoring*
{: .text-center .text-small }

---

## Scope of the module
As each position works differently (asset, range, volatility), this module aims to create an easy call-to-action (or not).

Thinking as an opportunity cost on out-of-range (OOR) position, restores control on what action perform to reduce non profitable but risky positions.

### Risk Logic: The "OOR Timer"
When talking about fast decision-making, the rules need to be forward: time-based OOR.

-> How much earnings am I losing while OOR?

| OOR duration | Status | Suggested action |
| :--- | :--- | :--- |
| **< 2 Days** | Acceptable | None (noise or volatility spike). |
| **3 to 5 Days** | To monitor | Opportunity cost increases. market structure change? |
| **5 Days+** | Critical | consider adapting strategy : **rebalance** or **exit**. |

---

## Limitations
This module deliberately excludes some risks such as:
- **Impermanent Loss**: Inherent to AMM structure. We especially focus on LP strategies here, so no need to compare with HODL.
- **Directional drawdowns**: Caused by inventory exposure, it is intentionally outside the current scope.

Hedging strategies for inventory drift are identified as a potential future extension of this risk framework.


## Complementary Risk Monitoring
In addition to LP operational risk, liquidation risk on lending positions is monitored through a dedicated LTV overview and automated alerts.

[Detailled here: Lend & borrow status]({{ site.baseurl }}/_pages/positions/#lend--borrow-status)
{: .btn .btn-outline }
