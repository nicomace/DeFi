---
layout: default
title: "Positions Monitoring"
parent: "DeFi Risk & Performance Framework"
nav_order: 1
---

# Positions Monitoring
{: .no_toc }

<br>

{: .note }
> **TL;DR** > Ce module traite les positions LP CLMM comme des **stratégies de market making**, et non du simple yield farming. Il surveille l'efficacité du capital et le risque d'inventaire.

---

## What this module monitors
This module aims to capture all the data from the CLMM positions. Based on 3 modules, it covers all the aspects required to better monitor market making positions such as active positions, idle liquidity, captured fees, or liquidity allocation.

### Key operational signals
- **Out of range** → Capital stops working (Opportunity cost).
- **Inventory drift** → Directional exposure increases.
- **LTV Increase** → Liquidation risk dominates returns.

---

## Position status (active vs idle)
This portfolio status quickshot provides a healthy check of the current activity:
- How much liquidity is working.
- Current APR vs. Potential APR (if all remained "in range").
- Risk level of lend & borrow positions.

![Current active liquidity positions]({{ site.baseurl }}/assets/images/positions/curr_positions.png)
{: .mx-auto }
*Current active liquidity positions*
{: .text-center .text-small }

---

## Inventory & liquidity allocation
The dashboard below is developed to log all position data, including price range, deposited amount, and entry price. It also provides the Uniswap V3 computation method for liquidity allocation.

![Create positions interface]({{ site.baseurl }}/assets/images/positions/histo_positions.png)
{: .mx-auto }
*Create positions interface*
{: .text-center .text-small }

### Why inventory matters
In CLMM, inventory naturally shifts with price. If token1 increases, the pool automatically sells token1 for token2. For example, on WETH/USDC, we are locking some profits as WETH is rising.

![Liquidity allocation + compute inventory]({{ site.baseurl }}/assets/images/positions/histo_positions1.png)
{: .mx-auto style="max-width: 450px;" }
*Liquidity allocation + compute inventory*
{: .text-center .text-small }

---

## Lend & borrow status
To leverage capital, I borrow stablecoins (e.g., on Aave). The major risk here is **liquidation**. Rather than checking protocols manually, this view centralizes all borrowing positions.

![Lend & Borrow status]({{ site.baseurl }}/assets/images/positions/lend_borrow.png)
{: .mx-auto }
*Centralized lending/borrowing view*
{: .text-center .text-small }

{: .important }
> By implementing automated email alerts, we can forestall any risky LTV that could lead to a liquidation.

![Email alerts]({{ site.baseurl }}/assets/images/positions/mail_ltv.png)
{: .mx-auto }
*Automated LTV risk alerts*
{: .text-center .text-small }

---

## Why this matters
This is the core structure of the monitoring tool. These metrics assess portfolio health:
- **Hidden risks**: Do I have liquidation exposure?
- **Deployment**: Is my capital fully active?
- **Efficiency**: Are returns compensating for the risk?
- **Directionality**: Is the portfolio unintentionally exposed to one asset?
