---
layout: default
title: "Operational Risk"
parent: "DeFi Risk & Performance Framework"
nav_order: 2
---

# Operational Risk
{: .no_toc }

<br>

Ce module constitue une couche de surveillance opérationnelle conçue spécifiquement pour gérer les **positions inactives** (idle positions). 

{: .note }
> Cette vue est intentionnellement simple et orientée vers l'action immédiate.

---

## Purpose
{: .no_toc .text-delta }

- Quel est le statut global du portefeuille ?
- Ai-je des positions inactives ?
- Quel est le **coût d'opportunité** ?
- Quelle action dois-je entreprendre **MAINTENANT** ?

---

![Risk Monitoring Dashboard]({{ site.baseurl }}/assets/images/risk/risk.png)
{: .mx-auto }
*Operational Risk Monitoring Dashboard*
{: .text-center .text-small }

---

## Scope of the module
Chaque position fonctionnant différemment (actifs, range, volatilité), ce module vise à créer un **appel à l'action** (Call-to-Action) simple.

En pensant en termes de coût d'opportunité pour les positions hors-range (Out-of-Range - OOR), on redonne le contrôle sur les décisions nécessaires pour réduire les positions non rentables mais risquées.

### Risk Logic: The "OOR Timer"
Pour une prise de décision rapide, les règles doivent être claires et basées sur le temps passé hors-range :

| Temps OOR | Statut | Action suggérée |
| :--- | :--- | :--- |
| **< 2 Jours** | Acceptable | Aucune (bruit de marché ou pic de volatilité). |
| **3 à 5 Jours** | À surveiller | Le coût d'opportunité augmente. Changement de structure ? |
| **5 Jours +** | Critique | Envisager d'adapter la stratégie : **rebalance** ou **exit**. |

---

## Limitations
Ce module exclut délibérément certains risques pour rester focalisé sur l'opérationnel :
- **Impermanent Loss** : Considéré comme inhérent à la structure AMM. Nous comparons ici l'efficacité de la stratégie LP, pas par rapport au HODL.
- **Drawdowns Directionnels** : L'exposition de l'inventaire est gérée séparément.
- **Hedging** : Les stratégies de couverture pour le drift d'inventaire sont identifiées comme une extension future du framework.

#### Complementary Risk Monitoring
En plus du risque opérationnel LP, le risque de liquidation sur les positions de prêt (Lending) est surveillé via une vue LTV dédiée et des alertes automatisées.

[Détails ici : Lend & borrow status]({{ site.baseurl }}/project/positions/#lend--borrow-status)
{: .btn .btn-outline }
