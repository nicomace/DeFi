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
> **TL;DR**
> This module treats CLMM LP positions as **market making strategies**, not yield farming.
> It monitors:
> - **in-range / out-of-range status** and distance to bounds  
> - **liquidity allocation and inventory drift** between assets  
> - **operational signals** to rebalance, resize, or exit positions
> - **lend & borrow status** with alerts for risky LTV
>
> The goal is to maintain capital efficiency and control inventory risk while optimizing fee generation.

---

## What this module monitors
This module aims to capture all the data from the CLMM positions. Based on 3 modules, it covers all the aspects required to better monitor market making positions such as active positions, idle liquidity, captured fees, or liquidity allocation.

### Key operational signals
- **Out of range** → Capital stops working (Opportunity cost).
- **Inventory drift** → Directional exposure increases.
- **LTV Increase** → Liquidation risk dominates returns.

---

## Position status (active vs idle)
In the capture below, this portfolio status quickshot provides a healthy check of the current activity:
-	How much liquidity is working
-	What is the current APR and what would it be if all positions remain “in range”
-	Which lend & borrow positions are getting riskier
-	Position details (Range, start date, current value, earned fees, estimated APR) + active colors to identify easily out of range positions

![Current active liquidity positions]({{ site.baseurl }}/assets/images/positions/curr_positions.png)
{: .mx-auto }
*Current active liquidity positions*
{: .text-center .text-small }

---

## Inventory & liquidity allocation
The above dashboard is developped from the module 2, where all the positions data are logged (as per below). It can be used to get more details such as price range of a position, deposited amount, entry price, and even check inactive positions.

![Create positions interface]({{ site.baseurl }}/assets/images/positions/histo_positions.png)
{: .mx-auto }
*Create positions interface*
{: .text-center .text-small }

This module also provides the Uniswap V3 computation method for liquidity allocation. It gives the current value and inventory of the position (tk0_new, tk1_new).
*Algo will be later implemented in code*

![Liquidity allocation + compute inventory]({{ site.baseurl }}/assets/images/positions/histo_positions1.png)
{: .mx-auto }
*Liquidity allocation + compute inventory*
{: .text-center .text-small }

This realtime inventory will be later used to adjust hedge.

*Why inventory matters: in CLMM, inventory naturally shifts with price. if token1 increases, then the pool will automatically adjust by selling token1 for token2. For example, on WETH/USDC, we are locking some profits as WETH is rising.*

---

## Lend & borrow status
Due to inherent risks to CLMM (covered here: [Operational Risk](/testDeFi/project/risk/)), I chose to leverage my capital borrowing stablecoins on Aave for example. Excepts protocol risk (small as Aave is a well-audited, structured and large protocol), the major risk that can occurs is liquidation. A healthy LTV would prevent major liquidations as we faced early on the 10th of October. 

Rather than checking manually borrowing protocols, the following view aims to centralize all borrowing positions.

![Lend & Borrow status]({{ site.baseurl }}/assets/images/positions/lend_borrow.png)
{: .mx-auto }
*Centralized lending/borrowing view*
{: .text-center .text-small }

In addition, by implementing automated mailing alert, we can forestall any risky ltv that can lead to a liquidation.

These alerts are concise and designed to get the info quickly:

![Email alerts]({{ site.baseurl }}/assets/images/positions/mail_ltv.png)
{: .mx-auto }
*Automated LTV risk alerts*
{: .text-center .text-small }

---

## Why this matters
This is the core structure of this CLMM monitoring tool. these metrics are very important to assess efficiently the portfolio health:
-	Do I have hidden liquidation risk?
-	Is my capital fully deployed?
-	Are returns compensating the risk taken?
-	Is my portfolio unintentionally directional?
