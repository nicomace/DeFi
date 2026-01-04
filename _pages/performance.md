---
title: "Performance Attribution & Fee Management"
permalink: /project/performance/
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
Liquidity provision is not about chasing APR.
It is about managing inventory risk and extracting fees efficiently.

## Objective
In [Risk Overview](/testDeFi/project/risk/), returns are estimated with weekly harvest fees. 
As LP are highly dynamic, we can only assume an estimated return, while realized return is computed when position is closed.

To summarize:
-	Expected return -> decision support
-	Realized return -> performance measurement


## Fee Management Process
<figure>
  <img src="/testDeFi/assets/images/performance/performance.png" alt="Perf Dashboard">
  <figcaption><em>Performance per ended pool</em></figcaption>
</figure>

This layer aims to track all harvested fees. It records fees from active/inactive pools by weeks -> realized fees.

I choose harvest Fees once per week. It makes sense as earnings start to be valuable.

To keep the process simple, we input: Week, Pool and Fees. Then, It is automatically added in the table.
*nb: only active pools and existing weeks are selectable*

All the fees-related data in the Dashboard comes from this layer.


## Performance Measurement Framework

<figure>
  <img src="/testDeFi/assets/images/performance/harvest_fees.png" alt="Perf Dashboard">
  <figcaption><em>Harvested Fees screen</em></figcaption>
</figure>

To compute the overall realized return, positions must be closed.
Capturing fees from the Fees layer and processing the inventory drift between open / close, we can finally compute the net outcome of this position.

Meanwhile Duration is used to measure the daily performance of the position. 
<br>
-> Daily return allows performance comparison across positions with different lifetimes.

This module shows us if the position was sufficiently compensated for the associated risk.


## Why this matters
-	Fees do not compensate poor range management
-	Picking wisely underlying crypto is essential (beware of too much vol)
-	Time matters more than expected APR

<br>
**Performance without risk context is noise. This toolkit links both.**
