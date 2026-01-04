---
title: "Risk Overview"
permalink: /project/risk/
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


We introduce this module as an operational monitoring layer built to manage idle positions.

-> This risk view is intentionally simple and action-oriented.

<figure>
  <img src="/testDeFi/assets/images/risk/risk.png" alt="Risk Dashboard">
  <figcaption><em>Risk monitoring</em></figcaption>
</figure>

## Purpose
-	What is the status of the portfolio?
-	Do I have inactive positions?
-	What is the opportunity cost?
-	What action should I take NOW?

## Scope of the module
As each position works differently (asset, range, volatility), this module aims to create an easy call-to-action (or not).

Thinking as an opportunity cost on out-of-range (OOR) position, restores control on what action perform to reduce non profitable but risky positions.

## Risk Logic
When talking about fast decision-making, the rules need to be forward: time-based OOR.

-> How much earnings am I losing while OOR?

-	2D: Acceptable as market conditions could interfere (ex: volatility spike).
-	3D to 5D: Opportunity cost that needs to be **monitored**. Perhaps market structure is changing.
-	5D+: Enough to consider adapting strategy: **rebalance** or **exit** depending on the market structure.

## Limitations
This module deliberately excludes some risks such as Impermanent Loss (inherent to AMM structure). We especially focus on LP strategies here, so no need to compare with HODL.

Directional drawdowns caused by inventory exposure are intentionally outside the current scope.
Hedging strategies for inventory drift are identified as a potential future extension of this risk framework.

#### ---- Complementary Risk Monitoring ----
In addition to LP operational risk, liquidation risk on lending positions is monitored through a dedicated LTV overview and automated alerts.

Detailed [HERE]


