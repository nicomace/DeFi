---
layout: default
title: "Performance Attribution"
parent: "DeFi Risk & Performance Framework"
nav_order: 3
---

# Performance Attribution & Fee Management
{: .no_toc }

<br>

{: .important }
> Liquidity provision is not about chasing APR.
>
> It is about **managing inventory risk** and **extracting fees efficiently**.

---


## Objective

In [Operational Risk]({{ site.baseurl }}/_pages/risk/), returns are estimated with weekly harvest fees. 
As LP are highly dynamic, we can only assume an estimated return, while realized return is computed when position is closed.

To summarize:
-	Expected return -> decision support
-	Realized return -> performance measurement

---

## Fee Management Process

![Harvested Fees screen]({{ site.baseurl }}/assets/images/performance/harvest_fees.png)
{: .mx-auto }
*Harvested Fees tracking interface*
{: .text-center .text-small }

This layer aims to track all harvested fees. It records fees from active/inactive pools by weeks -> realized fees.

All the fees-related data in the Dashboard comes from this layer.
### Workflow
* **Cadence**: Weekly harvest (optimizing transaction costs + earnings start to be valuable)
* **Simplicity** : Fast input (Week, Pool, Amount). Then, It is automatically added in the table.
* **Control** : Only active pools and existing weeks are selectable.

---

## Performance Measurement Framework

![Performance per ended pool]({{ site.baseurl }}/assets/images/performance/performance.png)
{: .mx-auto }
*Net performance analysis for closed positions*
{: .text-center .text-small }

To compute the overall realized return, positions must be closed.

This module shows us if the position was sufficiently compensated for the associated risk. Here is how it works:
1. Captured fees (through the *Fees layer*).
2. Inventory drift (difference between open / close).

Meanwhile Duration is used to measure the daily performance of the position. 
<br>
-> Daily return allows performance comparison across positions with different lifetimes.

This module answer the crucial question: *Is the compensation enough for the associated risk taken?*

---

## Why this matters

-	**Fees vs Management**: Fees do not compensate poor range management
-	**Asset Selection**: Picking wisely underlying crypto is essential (beware of too much vol)
-	**Time Sensitivity**: Time matters more than expected APR

<br>

{: .highlight }
**Performance without risk context is noise. This toolkit links both.**
