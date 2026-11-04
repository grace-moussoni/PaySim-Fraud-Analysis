# 💳 PaySim Fraud Analysis
### Analyse des transactions financières et détection des comportements frauduleux avec Power BI

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)
![CRISP-DM](https://img.shields.io/badge/Methodology-CRISP--DM-blue?style=for-the-badge)
![Scrumban](https://img.shields.io/badge/Agile-Scrumban-orange?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

---

## 📖 Contexte du projet

Le développement des services de **Mobile Money** a profondément transformé les usages financiers en facilitant les paiements, les transferts d'argent et les retraits de fonds.

Cependant, cette démocratisation s'accompagne d'une augmentation des risques de fraude, nécessitant des mécanismes de surveillance et de détection toujours plus performants.

Ce projet s'appuie sur le dataset **PaySim**, un ensemble de données synthétiques reproduisant des transactions financières réelles, afin d'étudier les comportements frauduleux et d'évaluer l'efficacité d'un système d'alerte automatisé.

---

## 🎯 Objectifs

Les objectifs principaux sont :

- Mesurer l'ampleur réelle de la fraude.
- Identifier les types de transactions les plus exposés.
- Analyser les tendances temporelles des activités frauduleuses.
- Évaluer les performances du système de détection existant.
- Produire un tableau de bord décisionnel interactif sous Power BI.

---

## ❓ Questions Business

### 1. Ampleur de la fraude
- Quelle est la proportion de transactions frauduleuses ?
- Quelle valeur financière représente cette fraude ?

### 2. Typologie des fraudes
- Quels types de transactions sont principalement ciblés ?
- Quels montants sont impliqués dans les activités frauduleuses ?

### 3. Analyse temporelle
- Existe-t-il des pics ou des tendances dans la survenance des fraudes ?
- Certains jours ou créneaux horaires présentent-ils davantage de risques ?

### 4. Performance du système d'alerte
- La règle métier actuelle permet-elle d'identifier efficacement les fraudes ?
- Quel est son niveau de faux positifs et de faux négatifs ?

---

## 📊 Présentation des données

### Source

Dataset **PaySim** disponible sur Kaggle.

Les données ont été générées à partir d'une simulation reproduisant des comportements observés dans un environnement de Mobile Money.

### Description

| Élément | Valeur |
|----------|---------|
| Nombre de lignes | ~6,3 millions |
| Nombre de colonnes | 11 |
| Période simulée | 744 heures (30 jours) |
| Type de données | Transactions financières |

### Variables principales

| Variable | Description |
|-----------|-------------|
| `type` | Type de transaction |
| `amount` | Montant de l'opération |
| `isFraud` | Indicateur de fraude réelle |
| `isFlaggedFraud` | Alerte générée par le système |

### Types de transaction

- CASH-IN
- CASH-OUT
- PAYMENT
- DEBIT
- TRANSFER

---

## 🧠 Méthodologie

Le projet combine :

### CRISP-DM

1. Compréhension métier
2. Compréhension des données
3. Préparation des données
4. Analyse et modélisation
5. Évaluation
6. Restitution

### Scrumban

La gestion de projet est menée à travers :

- Sprints courts
- Kanban GitHub
- Revues collaboratives
- Pull Requests

---

## 🏗️ Architecture Power BI

Le projet utilise le format moderne **Power BI Project (.pbip)** permettant le versioning Git.

### Semantic Model

```text
paysim_fraud_analysis.SemanticModel/
```

Contient :

- Power Query (ETL)
- Modèle de données
- Mesures DAX
- Relations

### Report

```text
paysim_fraud_analysis.Report/
```

Contient :

- Visualisations
- Pages du rapport
- Thèmes graphiques
- Mise en forme

---

## 📈 Dashboard

Le rapport Power BI est organisé autour de trois vues principales :

### Vue 1 : Indicateurs clés

- Nombre total de transactions
- Montant total traité
- Taux de fraude
- Répartition des transactions

### Vue 2 : Analyse temporelle

- Évolution horaire
- Évolution journalière
- Tendances de fraude

### Vue 3 : Évaluation du système d'alerte

- Matrice de confusion
- Faux positifs
- Faux négatifs
- Taux de détection

---

## 🔍 Principaux Insights

> À compléter après l'analyse finale.

Exemples d'insights attendus :

- Les fraudes sont fortement concentrées sur les opérations `TRANSFER` et `CASH_OUT`.
- Le dataset présente un fort déséquilibre de classes.
- La règle métier actuelle détecte seulement une partie des fraudes réelles.
- Plusieurs schémas transactionnels récurrents émergent avant les retraits frauduleux.

---

## 💡 Recommandations

> À compléter après l'analyse finale.

Pistes d'amélioration envisagées :

- Introduction de règles comportementales dynamiques.
- Renforcement de la surveillance des séquences `TRANSFER → CASH_OUT`.
- Mise en place de modèles de Machine Learning spécialisés.
- Réduction de la dépendance à un seuil fixe de 200 000 unités.

---

## ⚠️ Limites du projet

- Dataset synthétique.
- Scénario de fraude unique.
- Absence de contexte client détaillé.
- Résultats non directement transférables à un environnement bancaire réel.

---

# 🚀 Reproduire le projet

## Prérequis

- Power BI Desktop (version compatible `.pbip`)
- Git
- Visual Studio Code

## Cloner le dépôt

```bash
git clone https://github.com/grace-moussoni/PaySim-Fraud-Analysis.git

cd PaySim-Fraud-Analysis
```

## Ouvrir le projet

Ouvrez :

```text
paysim_fraud_analysis.pbip
```

Power BI Desktop chargera automatiquement :

- le modèle sémantique ;
- les transformations Power Query ;
- le rapport interactif.

---

## 🌿 Workflow Git

Créer une branche de travail :

```bash
git checkout main
git pull origin main
git checkout -b feature/nom-tache
```

Publier ses modifications :

```bash
git add .
git commit -m "Description des modifications"
git push origin feature/nom-tache
```

Puis ouvrir une Pull Request sur GitHub.

---

## 📂 Structure du dépôt

```text
PaySim-Fraud-Analysis/
│
├── .gitignore
├── README.md
│
├── paysim_fraud_analysis.pbip
│
├── paysim_fraud_analysis.Report/
│
├── paysim_fraud_analysis.SemanticModel/
│
├── source_files/
│
└── docs/
```

---

## 👥 Équipe Projet
### Groupe 3 - Akieny Academy

| Membre | Rôle |
|----------|---------|
| Rosy Perine NGOMA IKAMA | Cheffe de Projet / Lead Data |
| MOUSSONI Grace | Repository Administrator |
| Christ Roland BIBILA-MANGAYI | Data Analyst |
| Marthinet Berthanie de Sagesse | Data Analyst |
| MBANDOU Sublime | Data Analyst & Visualisation |

---

## 📜 Licence

Ce projet est distribué sous licence **MIT**.

Vous êtes libre de :

- utiliser ;
- modifier ;
- distribuer ;
- publier ;

le code du projet, sous réserve de conserver la licence MIT et les mentions de copyright.

Voir le fichier :

```text
LICENSE
```

pour plus de détails.

---

## ⭐ Remerciements

- Akieny Academy
- Kaggle
- Edgar Lopez-Rojas et collaborateurs
- Microsoft Power BI

---

**Projet académique réalisé dans le cadre de la formation Data Analytics & IA d'Akieny Academy.**