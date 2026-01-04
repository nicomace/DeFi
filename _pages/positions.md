---
title: "Positions Monitoring"
permalink: /project/positions/
layout: single
classes: wide
author: false
author_profile: false
sidebar: false
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

<br>
**<u>TL;DR</u>**  
> This module treats CLMM LP positions as **market making strategies**, not yield farming.  
> It monitors:
> - **in-range / out-of-range status** and distance to bounds  
> - **liquidity allocation and inventory drift** between assets  
> - **operational signals** to rebalance, resize, or exit positions
> - **lend & borrow status** with alerts for risky LTV
>
> The goal is to maintain capital efficiency and control inventory risk while optimizing fee generation.




## What this module monitors
This module aims to capture the all the data from the CLMM positions. Based on 3 modules, It covers all the aspects required to better monitore market making positions such as active positions, idle liquidity, captured fees or liquidity allocation.

## Key operational signals
-	When positions go out of range → capital stops working
-	When inventory drifts → directional exposure increases
-	When LTV increases → liquidation risk dominates returns

## Position status (active vs idle)
In the capture below, this portfolio status quickshot provides a healthy check of the current activity:
-	How much liquidity is working
-	What is the current APR and what would it be if all positions remain “in range”
-	Which lend & borrow positions are getting riskier
-	Position details (Range, start date, current value, earned fees, estimated APR) + active colors to identify easily out of range positions

<figure>
  <img src="/testDeFi/assets/images/positions/curr_positions.png" alt="Positions Dashboard">
  <figcaption><em>Current active liquidity positions</em></figcaption>
</figure>


## Inventory & liquidity allocation
The above dashboard is developped from the module 2, where all the positions data are logged (as per below). It can be used to get more details such as price range of a position, deposited amount, entry price, and even check inactive positions.

<figure>
  <img src="/testDeFi/assets/images/positions/histo_positions.png" alt="Positions Dashboard">
  <figcaption><em>Create positions interface</em></figcaption>
</figure>

This module also provides the Uniswap V3 computation method for liquidity allocation. It gives the current value and inventory of the position (tk0_new, tk1_new).
*Algo will be later implemented in code*

<figure class="img-medium">
  <img
    src="/testDeFi/assets/images/positions/histo_positions1.png" alt="Positions Dashboard">
  <figcaption><em>Liquidity allocation + compute inventory</em></figcaption>
</figure>

This realtime inventory will be later used to adjust hedge.

*Why inventory matters: in CLMM, inventory naturally shifts with price. if token1 increases, then the pool will automatically adjust by selling token1 for token2. For example, on WETH/USDC, we are locking some profits as WETH is rising.*


## Lend & borrow status
Due to inherent risks to CLMM (covered here: [Risk Overview](/testDeFi/project/risk/)), I chose to leverage my capital borrowing stablecoins on Aave for example. Excepts protocol risk (small as Aave is a well-audited, structured and large protocol), the major risk that can occurs is liquidation. A healthy LTV would prevent major liquidations as we faced early on the 10th of October. 

Rather than checking manually borrowing protocols, the following view aims to centralize all borrowing positions.

<figure>
  <img src="/testDeFi/assets/images/positions/lend_borrow.png" alt="Positions Dashboard">
  <figcaption><em>Create positions interface</em></figcaption>
</figure>

In addition, by implementing automated mailing alert, we can forestall any risky ltv that can lead to a liquidation.

These alerts are concise and designed to get the info quickly:

<figure>
  <img src="/testDeFi/assets/images/positions/mail_ltv.png" alt="Positions Dashboard">
  <figcaption><em>Create positions interface</em></figcaption>
</figure>


## Why this matters
This is the core structure of this CLMM monitoring tool. these metrics are very important to assess efficiently the portfolio health:
-	Do I have hidden liquidation risk?
-	Is my capital fully deployed?
-	Are returns compensating the risk taken?
-	Is my portfolio unintentionally directional?
