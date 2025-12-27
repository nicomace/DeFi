---
title: "Positions"
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


**TL;DR**  
> This module treats CLMM LP positions as **market making strategies**, not yield farming.  
> It monitors:
> - **in-range / out-of-range status** and distance to bounds  
> - **liquidity allocation and inventory drift** between assets  
> - **operational signals** to rebalance, resize, or exit positions  
>
> The goal is to maintain capital efficiency and control inventory risk while optimizing fee generation.




The purpose is to get a quick view on the current active liquidity positions across Concentrated Liquidity Market Makers (CLMMs).
In order to maximize clarity, 2 different sheets are used to get:
- get a quick capture of important position metrics such as working capital, earned fees, risky LTV ratio and details per active positions
- all details per positions plus the computation of current liquidity value and inventory




<figure>
  <img src="/testDeFi/assets/images/positions/curr_positions.png" alt="Positions Dashboard">
  <figcaption><em>Current active liquidity positions</em></figcaption>
</figure>

**Active positions dashboard**

This dashboard aims to capture the principal information of active CLMM positions.

The first part is showing on a quickshot statistics of positions such as:
- Capital at Work: Capital of "In Range" positions based on the current value of each position
- Realized APR: Current APR based on harvest fees over active positions *active position means "In Range" and "Out of Range"*
- Expected APR: APR that can be earned. It is computed based on "In Range" positions and sumprod of Current Value and Yearly APR.
- Active Liquidity: how many active positions are "In Range"
- Harvest Fees: fees already earned *meaning harvested from the positions*
- LTV>40%: Snapshot to monitore the lend&borrow ratio that could become risky
- Fees over time: Graph to visualize harvest fees evolution

The second part gives details per active CLMM positions:
- Range: whether position is in or out, a colour code shows the current status of a pool
- Curr. Value: computed with Uniswap v3 CLMM algo, it is a dynamic data that reprices token1/token2 ratio in realtime
- APR: computed based on the weekly harvest fees (we'll talk about it later) and the time the position is active
- Tot. Perf: Realized APR per position
 
*Capturing realtime data from Sheet2, it aims to snapshot active CLMM positions*


<figure>
  <img src="/testDeFi/assets/images/positions/histo_positions.png" alt="Positions Dashboard">
  <figcaption><em>Create positions interface</em></figcaption>
</figure>

**Input for positions**

This sheet is where all comes from. When entering into a new AMM position, we input the details here:
- which DeFi app
- start date
- which crypto
- deposited amount
- range (inf and sup) and token1 & token2 quantities *needed to assess the current liquidity value*
- liquidity allocation *see screenshot behind*👇

these datas are then used in other sheets to compute sensitive metrics


<figure style="max-width: 820px; margin: 2rem auto; text-align: center;">
  <img
    src="/testDeFi/assets/images/positions/histo_positions1.png"
    alt="Positions Dashboard"
    style="width: 100%; height: auto;"
  >
  <figcaption><em>Liquidity allocation + compute inventory</em></figcaption>
</figure>

The Liquidity Allocation step was added recently as it is necessary to assess the current value of the CLMM position. 

*little reminder: in CLMM, depending of the value of the underlying crypto, the token1/token2 ratio will evolve dynamically. if token 1 increases, then the pool will automatically adjust by selling token1 for token2. For example, on WETH/USDC, we are locking some profits as WETH is rising*

Using "Curr. Price", it recompute token1 and token2 quantities so we can get "Curr. Value"
*here you'll find details regarding this Uniswap v3 computation process --> **LINK ATTACHED**


this part is the "core engine" of the DeFi Monitoring toolkit. From position details to important metrics, it gives a quick shot of how your active positions are healthy, wealthy and risky



<figure>
  <img src="/testDeFi/assets/images/positions/harvest_fees.png" alt="Positions Dashboard">
  <figcaption><em>Current active liquidity positions</em></figcaption>
</figure>

**Realized Fees Monitoring**

in this sheet, earned fees are easily tracked by pool and by week. As per the screenshot, in green active pools are highlighted.
In the parameter section (above "Add") button, you can pick week and pool. These 2 cells are drop-down lists. they are are dynamically built to show specifically active pools and existing week from the table.

*disclaimer: this is a V1 for realized fees monitoring. In V2, we will be able to put fees directly from the "Active positions dashboard", optimizing data integration and reducing risk of fat finger.*

- Add Button
Using Apps Script from GoogleSheets, this algorithm will add the selected fees to the specific week and pool attached. In the example above, the parameters would add 7$ to the pre existing fees of 6,70$.

In the tracker, this section is a must as it creates a dynamic environment to follow realized gains from AMM positions without noise.
