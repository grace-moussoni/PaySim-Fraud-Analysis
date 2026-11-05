# AKIENY ACADEMY
**Projet d'évaluation S18 | Groupe 3**

## DOCUMENT DE CADRAGE — Projet PaySim
### Analyse des transactions financières et étude des comportements frauduleux
*Source : Kaggle (PaySim) | Outils : Power BI, GitHub | Version 1.1 — 03 novembre 2026*

---

## ÉQUIPE PROJET

| Membre | Rôle |
| :--- | :--- |
| **Rosy Perine NGOMA IKAMA** | Cheffe de Projet (CP) - Lead Data |
| **MOUSSONI Grace** | Lead Repo Admin |
| **Christ Roland BIBILA-MANGAYI** | Data Analyst |
| **Marthinet Berthanie de Sagesse** | Data Analyst |
| **MBANDOU Sublime** | Data Analyst / Visualisation |

---

## 1. Présentation du projet

| Élément | Description |
| :--- | :--- |
| **Intitulé** | Analyse des transactions financières et étude des comportements frauduleux (jeu de données PaySim) |
| **Nature** | Data analysis : exploration, nettoyage, analyse et restitution |
| **Source des données** | Kaggle — PaySim (transactions financières synthétiques) |
| **Outils** | Power BI (Power Query, DAX), GitHub |
| **Méthodologie** | Allégée (Scrumban) + cycle d'analyse CRISP-DM / Agile |
| **Livrable final** | Tableau de bord Power BI interactif, présentation et recommandations |
| **Échéance** | Vendredi 06/11/2026 (démarrage le mardi 03/11/2026) |

---

## 2. Contexte et problématique

Le paiement mobile facilite les transactions mais expose les utilisateurs et les institutions à la fraude. PaySim, issu de journaux de transactions réelles, permet d'étudier ces comportements et d'évaluer un système d'alerte existant.

* **Problématique :** Comment l'analyse des transactions permet-elle d'identifier les caractéristiques des comportements frauduleux et d'évaluer l'efficacité du système de détection existant ?
* **Objectif général :** Identifier les caractéristiques des fraudes, puis mesurer la capacité du système d'alerte à les détecter.
* **Objectifs spécifiques :** Explorer et nettoyer les données ; mesurer l'ampleur de la fraude ; analyser types et montants ; étudier l'évolution temporelle ; évaluer le système d'alerte.

---

## 3. Méthodologie de travail

Le projet dure quatre jours. Une méthode lourde (cycle en V, cascade) n'est pas adaptée : elle impose de tout figer d'avance. Nous retenons une approche agile allégée de type **Scrumban**, associée à **CRISP-DM** pour structurer l'analyse.

| Composante | Rôle dans le projet |
| :--- | :--- |
| **Agile / Scrumban** | **Pilotage :** un sprint unique de 4 jours, tableau Kanban (À faire / En cours / À valider / Terminé), livraison progressive du tableau de bord. |
| **CRISP-DM** | **Démarche d'analyse :** compréhension du problème, compréhension et préparation des données, analyse, évaluation, restitution. |

### Pourquoi ce choix ?
* **Rapidité :** Tâches menées en parallèle, sans lourdeur documentaire.
* **Visibilité :** L'avancement est lisible à tout moment sur le tableau Kanban.
* **Souplesse :** Les priorités peuvent être ajustées chaque jour.
* **Rigueur :** CRISP-DM garantit une analyse structurée, de la donnée brute à la recommandation.

### Rituels
| Rituel | Fréquence | Objet |
| :--- | :--- | :--- |
| **Point d'équipe** | Quotidien, 15 min | Avancement, blocages, priorités du jour |
| **Revue des livrables** | Fin de journée | Validation par la Cheffe de Projet et la Lead Repo Admin |
| **Recette finale** | Vendredi 06/11 | Validation du tableau de bord et de la présentation |

---

## 4. Organisation de l'équipe

| Membre | Rôle | Responsabilités |
| :--- | :--- | :--- |
| **Rosy Perine NGOMA IKAMA** | Cheffe de Projet (CP) / Lead Data | Pilotage global, coordination, suivi des échéances ; exploration et nettoyage ; validation de la cohérence analytique et des mesures DAX ; garante de la conduite du projet jusqu'à la restitution finale. |
| **MOUSSONI Grace** | Lead Repo Admin | Gouvernance du dépôt GitHub, versioning, centralisation et suivi des livrables ; documentation, recette et rapport final. |
| **Christ Roland BIBILA-MANGAYI** | Data Analyst | Axes 1 et 2 : ampleur de la fraude, types et montants ; préparation des variables. |
| **Marthinet Berthanie de Sagesse** | Data Analyst | Axe 3 : analyse temporelle ; participation au nettoyage ; recommandations. |
| **MBANDOU Sublime** | Data Analyst / Visualisation | Axe 4 : évaluation du système d'alerte (matrice de confusion) ; conception du tableau de bord. |

*Tous les membres participent à l'exploration, à la synthèse et à la présentation finale. Les données brutes ne sont jamais modifiées.*

---

## 5. Outils et source de données

| Élément | Usage |
| :--- | :--- |
| **Kaggle - PaySim** | Source du jeu de données |
| **Power BI** | Modélisation, visualisation, tableau de bord interactif |
| **Power Query (M)** | Exploration, transformation et nettoyage |
| **DAX** | Mesures : taux de fraude, montants frauduleux, performance du système d'alerte |
| **GitHub** | Dépôt du projet, versioning par branches, travail collaboratif, centralisation des livrables |

---

## 6. Phases et planning

| Phase | Contenu | Période |
| :--- | :--- | :--- |
| **0 - Cadrage** | Document de cadrage, création du dépôt GitHub | Mar 03/11 |
| **1 - Exploration** | Structure, types, valeurs manquantes, distribution de `isFraud` | Mar 03 - Mer 04 |
| **2 - Nettoyage et préparation** | Doublons, incohérences montants/soldes, valeurs aberrantes, écarts `isFraud`/`isFlaggedFraud`, mesures DAX | Mer 04 - Jeu 05 |
| **3 - Analyse** | Axe 1 : ampleur / Axe 2 : types et montants / Axe 3 : temporel / Axe 4 : système de détection | Jeu 05 |
| **4 - Restitution** | Tableau de bord, recommandations, recette, présentation | Jeu 05 - Ven 06 |

*Les phases 3 et 4 se chevauchent : les analyses alimentent directement le tableau de bord.*

---

## 7. Tâches, responsabilités et jalons

### Tableau des tâches
| ID | Tâche | Responsable(s) | Période | Livrable |
| :--- | :--- | :--- | :--- | :--- |
| **T1** | Rédaction et validation du cadrage | Grace + équipe | 03/11 | Document de cadrage |
| **T2** | Création du dépôt GitHub et structure des dossiers | Grace | 03/11 | Dépôt + README |
| **T3** | Exploration de PaySim | Rosy + Christ | 03-04/11 | Fiche d'exploration |
| **T4** | Nettoyage des données | Rosy + Marthinet | 04/11 | Données nettoyées |
| **T5** | Variables et mesures DAX | Rosy + Christ | 04-05/11 | Modèle Power BI |
| **T6** | Axes 1 et 2 : ampleur, types et montants | Christ | 05/11 | Résultats axes 1 et 2 |
| **T7** | Axe 3 : analyse temporelle | Marthinet | 05/11 | Résultats axe 3 |
| **T8** | Axe 4 : évaluation du système d'alerte | Sublime | 05/11 | Résultats axe 4 |
| **T9** | Maquette et développement du tableau de bord | Sublime + Christ + Marthinet | 05-06/11 | Fichier `.pbix` |
| **T10** | Recommandations | Marthinet + Rosy | 05-06/11 | Recommandations |
| **T11** | Recette, rapport et présentation | Grace + équipe | 06/11 | Rapport + slides |
| **T12** | Dépôt final des livrables | Toute l'équipe | 06/11 | Livrables sur GitHub |

### Jalons
| Jalon | Date | Validation |
| :--- | :--- | :--- |
| **J1 — Cadrage validé, dépôt prêt** | Mar 03/11 | Document approuvé, GitHub opérationnel |
| **J2 — Données prêtes** | Mer 04/11 | Données nettoyées, mesures DAX en cours |
| **J3 — Analyses terminées** | Jeu 05/11 | Résultats des 4 axes obtenus |
| **J4 — Remise finale** | Ven 06/11 | Tableau de bord, présentation et recommandations déposés |

---

## 8. Livrables et risques

### Livrable final
Tableau de bord décisionnel Power BI interactif (cartes KPI, graphiques, matrice de confusion, filtres), accompagné d'une présentation et de recommandations pour améliorer la surveillance des transactions.

### Matrice des risques
| Risque | Mesure |
| :--- | :--- |
| **Délai très court (4 jours)** | Tâches en parallèle, point quotidien, priorité aux indicateurs essentiels. |
| **Gros volume ralentissant Power BI** | Charger uniquement les colonnes utiles, mesures DAX légères. |
| **Conflits de versions** | Travail par branches GitHub, revue par la Lead Repo Admin. |