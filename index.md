---
layout: default
title: "Why this project"
nav_order: 1
# Si tu veux que ce soit une sous-page d'un menu "Projets", décommente la ligne suivante :
# parent: Projects 
---

# Why this project
{: .no_toc }

<br>

With Uniswap V3 released, the new features such as capital efficiency and customized ranges reshaped how market making strategies are designed. 

But it came with a performance cost if price drifts from the selected range creating idle capital and asymmetric directional exposure.

The purpose is to understand what each situation can cost if it remains, focusing on: **monitoring risk to optimize performance.**

### Key cost indicators:
- **Time** (out-of-range)
- **Capital inefficiency** (impermanent loss, inventory drift)

---

## What we currently find
In CLMM (Concentrated Liquidity Market Making), existing interfaces are insufficient:
- They show pool and position details (TVL, estimated APR, range, inventory). 
- But they are fragmented and limited in quantifying risk in real time.

In this context, I developed a framework to measure CLMM strategies efficiency. 

{: .important }
> Ce framework apporte une approche disciplinée et orientée risque, inspirée des pratiques institutionnelles.

## Framework structure
- **Monitoring lending and borrowing positions** (LTV, liquidation buffers).
- **Tracking CLMM LP positions**:
  - in-range / out-of-range status
  - inventory exposure
  - fee generation
- **Following performance** over time with a **net PnL approach**.
- **Understanding portfolio-level exposure** across tokens and protocols.

## Last word
You can explore the project here: [DeFi Risk & Performance Framework]({{ site.baseurl }}/project/)

<br>
Feel free to reach out if you’re interested in **DeFi risk, market making, or portfolio analytics**.
