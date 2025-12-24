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


💧 Active DeFi Position Monitoring (CLMM & LP)

- Tracking of active liquidity positions across Concentrated Liquidity Market Makers (CLMMs)
(e.g. Uniswap v3-style mechanics)
- Detection of:
- In-range vs out-of-range status
- Capital currently productive vs idle
- Exposure asymmetry between base and quote assets
- Monitoring of inventory drift, critical for market making strategies

Particularly suited for range-based liquidity provision, delta-sensitive LP, and fee-driven market making.

<figure>
  <img src="/testDeFi/assets/images/positions/curr_positions.png" alt="Positions Dashboard">
  <figcaption><em>Current active positions</em></figcaption>
</figure>

<figure>
  <img src="/testDeFi/assets/images/positions/histo_positions.png" alt="Positions Dashboard">
  <figcaption><em>Create positions interface</em></figcaption>
</figure>

<figure style="text-align: center;">
  <img
    src="/testDeFi/assets/images/positions/histo_positions1.png"
    alt="Positions Dashboard"
    style="max-width: 400px; width: 100%; height: auto;"
  >
  <figcaption><em>Liquidity allocation + compute inventory</em></figcaption>
</figure>

