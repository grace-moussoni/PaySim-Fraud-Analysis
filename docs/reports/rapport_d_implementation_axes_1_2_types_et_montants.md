# 📊 Rapport d'Implémentation — Axes 1 & 2 : Ampleur, Types et Montants

**Projet PaySim Groupe 3 | AKIENY ACADEMY**

**Auteur :** Christ Roland BIBILA-MANGAYI (Data Analyst)

**Revue & Validation :** Grace MOUSSONI (Repository Administrator)

**Date :** Novembre 2026

## 📖 1. Contexte & Objectifs

L'objectif des **Axes 1 et 2** est d'évaluer l'ampleur globale de la fraude dans le jeu de données PaySim (6,36 millions de transactions) et de caractériser les typologies d'opérations ainsi que les tranches de montants les plus exposées au risque.

Ce document retrace la méthodologie technique, les formules DAX construites, l'agencement visuel et les enseignements analytiques tirés lors de la réalisation de cette page du rapport Power BI.

## 🛠️ 2. Mise en Place des Mesures DAX

Afin d'alimenter les visuels sans altérer les performances du rapport, quatre mesures DAX fondamentales ont été créées et typées au niveau du modèle sémantique (`Transactions`) :

### 2.1. Volume Total de Transactions

```
Nombre de Transactions = COUNTROWS(Transactions)

```

### 2.2. Volume Brut de Fraudes

```
Nombre de Fraudes = CALCULATE(COUNTROWS(Transactions), Transactions[isFraud] = 1)

```

### 2.3. Taux de Fraude (%)

```
Taux de Fraude = DIVIDE([Nombre de Fraudes], [Nombre de Transactions], 0)

```

*Note : Formaté en pourcentage avec 2 décimales (`Percentage`, `2 decimal places`).*

### 2.4. Montant Global Fraudé

```
Montant Frauduleux = CALCULATE(SUM(Transactions[amount]), Transactions[isFraud] = 1)

```

## 📐 3. Conception et Ergonomie Visuelle

La mise en page a été conçue pour respecter la charte graphique globale définie par l'équipe :

### 3.1. En-tête & Contrôles

* **Bandeau d'en-tête unifié :** Un rectangle bleu foncé recouvrant le haut de la page intégrant le titre `PaySim - Analyse des fraudes | Types et montants` et la pagination `Page 2 sur 5 : axes 1 et 2`.

* **Barre de Segments (Slicers) :** Alignement horizontal de 4 filtres sous forme de menus déroulants compacts (`Type`, `Jour`, `Heure`, `Tranche_Montant`).

### 3.2. Grille de Visualisation (4 Visuels Clés)

1. **Graphique 1 — Nombre de transactions par type (Haut-Gauche) :**

   * *Visuel :* Historigramme groupé (`Clustered column chart`).

   * *Axe X :* `type` (`CASH_OUT`, `PAYMENT`, `CASH_IN`, `TRANSFER`, `DEBIT`).

   * *Axe Y :* `[Nombre de Transactions]`.

2. **Graphique 2 — Nombre de fraudes par type (Haut-Droite) :**

   * *Visuel :* Historigramme groupé avec surbrillance rouge alerte.

   * *Axe X :* `type` (avec activation de l'option *"Afficher les éléments sans données"* pour faire apparaître les types à zéro).

   * *Axe Y :* `[Nombre de Fraudes]`.

3. **Graphique 3 — Taux de fraude par type % (Bas-Gauche) :**

   * *Visuel :* Historigramme groupé.

   * *Axe X :* `type`.

   * *Axe Y :* `[Taux de Fraude]`.

4. **Graphique 4 — Taux de fraude par tranche de montant % (Bas-Droite) :**

   * *Visuel :* Historigramme groupé trié dans l'ordre chronologique des tranches (`< 10 k` à `> 1 M`).

   * *Axe X :* `Tranche_Montant`.

   * *Axe Y :* `[Taux de Fraude]`.

## 🔍 4. Principaux Insights Extraits

* **Concentration exclusive :** Sur les 5 types de transactions disponibles dans le Mobile Money, les 8 213 fraudes répertoriées se concentrent **exclusivement** sur deux types d'opérations :

  * `CASH_OUT` : 4 116 fraudes

  * `TRANSFER` : 4 097 fraudes

  * Les types `CASH_IN`, `PAYMENT` et `DEBIT` ne présentent **aucune** fraude (0 %).

* **Différence de risque par type :** Bien que les volumes bruts soient quasiment identiques entre `CASH_OUT` et `TRANSFER`, le **taux de fraude** est nettement plus élevé sur les transferts (**0,77 %**) que sur les retraits de fonds (**0,18 %**), car le volume global de transferts est plus faible.

* **Explosion du risque sur les hauts montants :** Le taux de fraude suit une croissance exponentielle avec la valeur de la transaction :

  * Transactions $< 10\text{ k}$ : **0,02 %** de risque

  * Transactions $> 1\text{ M}$ : **2,07 %** de risque (soit un taux de fraude 100 fois supérieur).

## 🎯 5. Conclusion & Recommandations Métier

L'analyse combinée des types et des montants montre que l'effort de surveillance de l'établissement financier doit se focaliser en priorité sur la boucle **`TRANSFER`** $\rightarrow$ **`CASH_OUT`** pour tout montant dépassant 200 000 unités financières, en abaissant les seuils d'alerte automatiques sur le type `TRANSFER`.