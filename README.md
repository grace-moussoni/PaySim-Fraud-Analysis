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
- Quels types de transactions sont principalement cibles ?
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
Dataset **PaySim** officiel disponible sur Kaggle : [Synthetic Financial Datasets for Fraud Detection](https://www.kaggle.com/datasets/ealaxi/paysim1).

Les données ont été générées à partir d'une simulation reproduisant des comportements observés dans un environnement de Mobile Money.

### Description

| Élément | Valeur |
|----------|---------|
| Nombre de lignes | 6 362 620 |
| Nombre de colonnes | 11 |
| Période simulée | 743 pas de temps (31 jours incomplets) |
| Type de données | Transactions financières synthétiques |

### Variables principales

| Variable | Description |
|-----------|-------------|
| `type` | Type de transaction (`CASH_IN`, `CASH_OUT`, `DEBIT`, `PAYMENT`, `TRANSFER`) |
| `amount` | Montant de l'opération |
| `isFraud` | Indicateur de fraude réelle (1 = Fraude, 0 = Normale) |
| `isFlaggedFraud` | Alerte générée par le système actuel (1 = Alerte, 0 = Non alerte) |

---

## 🧠 Méthodologie

Le projet combine :

### CRISP-DM
1. Compréhension métier
2. Compréhension des données
3. Préparation des données (Power Query M)
4. Analyse et modélisation
5. Évaluation (Matrice de confusion)
6. Restitution (Power BI)

### Scrumban
La gestion de projet est menée à travers :
- Sprints courts
- GitHub Project / Kanban
- Revues collaboratives & Pull Requests

---

## 🏗️ Architecture Power BI

Le projet utilise le format moderne **Power BI Project (.pbip)** permettant le versioning sous Git.

### Semantic Model
```text
sources_files/paysim_fraud_analysis.SemanticModel/
```
Contient :
- Script Power Query unifié (Langage M)
- Modèle de données et typage
- Mesures DAX
- Métadonnées TMDL

### Report
```text
sources_files/paysim_fraud_analysis.Report/
```
Contient :
- Visualisations graphiques
- Pages du rapport
- Thèmes graphiques et mises en page

---

## 📈 Structure du Dashboard Power BI

Le rapport Power BI s'organise selon les responsabilités définies dans la note de synthèse :

### 1. Synthèse & Indicateurs Clés (Page Principale)
- **KPI principaux :** Nombre de transactions (6,36 M), nombre de fraudes (8 213), taux de fraude (0,129%), montant total fraudé (~12,06 Mds).
- Segments interactifs par type, jour, heure et statut de fraude.

### 2. Axes 1 & 2 : Ampleur, Types et Montants *(Christ Roland)*
- Répartition des fraudes par type (exclusivité `CASH_OUT` et `TRANSFER`).
- Taux de fraude par type et par tranche de montant.
- Graphique du déséquilibre des classes et montants extrêmes.

### 3. Axe 3 : Analyse Temporelle *(Marthinet)*
- Évolution journalière (Jours 1 à 31) et horaire (Heures 0 à 23).
- Matrice Jour × Heure avec mise en forme conditionnelle.
- Mise en évidence de la sur-représentation des fraudes durant la nuit (0h - 5h).

### 4. Axe 4 : Évaluation du Système d'Alerte *(Sublime)*
- Matrice de confusion ($VP=16$, $FN=8197$, $FP=0$, $VN=6 354 407$).
- Analyse des défaillances de la règle métier du seuil des 200 000.
- Mesures du Rappel, Précision et estimation du montant fraudé non détecté (~11,98 Mds).

---

## 🔍 Principaux Insights

- **Concentration ciblée :** Les 8 213 fraudes surviennent exclusivement sur les transactions `CASH_OUT` (4 116) et `TRANSFER` (4 097).
- **Inefficacité du système d'alerte :** Le système de règles actuel n'a détecté que 16 fraudes sur 8 213 (Rappel de 0,19%).
- **Comportement nocturne :** Le taux de fraude s'envole entre 0h et 5h du matin (dépassant 22% vers 3h-4h), car le volume de transactions normales chute drastiquement alors que la fraude reste constante.
- **Tranches élevées :** Le taux de fraude atteint son sommet (2,07%) sur les montants supérieurs à 1 million.

---

## 💡 Recommandations

- **Refonte des règles métier :** Étendre les règles d'alerte aux retraits `CASH_OUT` et aux transferts inférieurs au seuil de 200 000.
- **Surveillance horaire renforcée :** Appliquer des contrôles de sécurité accrus (ex: validation 2FA systématique) sur la tranche horaire 0h - 5h.
- **Détection séquentielle :** Surveiller prioritairement les enchaînements rapides de `TRANSFER` vers un compte client immédiatement suivis d'un `CASH_OUT`.

---

## ⚠️ Limites du projet

- Dataset synthétique généré par simulation.
- Modèle simplifié pour optimiser les performances (identifiants uniques `nameOrig`/`nameDest` et soldes bruts retirés de la table principale).
- Le jour 31 contient 23 pas de temps au lieu de 24 (s'arrête au pas 743).

---

# 🚀 Reproduire le projet

## Prérequis

- **Windows 10 / 11** *(Power BI Desktop s'exécute nativement uniquement sous Windows)*.
- **Power BI Desktop** (dernière version compatible avec le format `.pbip`).
- **Git** & **Visual Studio Code** (optionnel pour l'édition de code TMDL/M).

## Configuration du Jeu de Données (Convention d'équipe)

1. Téléchargez le dataset `PS_20174392719_1491204439457_log.csv` depuis [Kaggle](https://www.kaggle.com/datasets/ealaxi/paysim1).
2. Créez un dossier **`C:\PaySim\`** à la racine de votre disque principal sous Windows.
3. Placez le fichier CSV dans ce dossier : `C:\PaySim\PS_20174392719_1491204439457_log.csv`.

> *Remarque : Le script Power Query unifié pointe automatiquement sur ce chemin absolu afin de garantir un chargement direct sans erreur de source sur tous les postes l'équipe.*

## Cloner et ouvrir le projet

```bash
git clone https://github.com/grace-moussoni/PaySim-Fraud-Analysis.git
cd PaySim-Fraud-Analysis
```

Ouvrez ensuite le fichier projet dans `sources_files` :
```text
sources_files/paysim_fraud_analysis.pbip
```

Power BI Desktop chargera automatiquement le modèle sémantique, appliquera le script Power Query et ouvrira le rapport.

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
git commit -m "feat(module): description des modifications"
git push origin feature/nom-tache
```

Puis ouvrir une Pull Request (PR) sur GitHub.

---

## 📂 Structure du dépôt

```text
PaySim-Fraud-Analysis/
├── .github/
│   └── PULL_REQUEST_TEMPLATE.md
├── docs/
│   ├── reports/
│   │   ├── compte_rendu_de_reunion_3_novembre_2026.md
│   │   └── note_de_synthese_equipe_paysim.md
│   ├── document_de_cadrage_paysim.md
│   └── note_d_arbitrage_technique.md
├── sources_files/
│   ├── paysim_fraud_analysis.Report/
│   ├── paysim_fraud_analysis.SemanticModel/
│   └── paysim_fraud_analysis.pbip
├── .gitignore
├── CONTRIBUTING.md
├── LICENSE
└── README.md
```

---

## 👥 Équipe Projet
### Groupe 3 - Akieny Academy

| Membre | Rôle |
|----------|---------|
| **Rosy Perine NGOMA IKAMA** | Cheffe de Projet / Lead Data |
| **MOUSSONI Grace** | Repository Administrator |
| **Christ Roland BIBILA-MANGAYI** | Data Analyst |
| **Marthinet Berthanie de Sagesse** | Data Analyst |
| **MBANDOU Sublime** | Data Analyst & Visualisation |

---

## 📜 Licence

Ce projet est distribué sous licence **MIT**. Voir le fichier [LICENSE](LICENSE) pour plus de détails.

---

## ⭐ Remerciements

- **Akieny Academy**
- **Kaggle & Edgar Lopez-Rojas** pour le jeu de données PaySim
- **Microsoft Power BI**

---

**Projet académique réalisé dans le cadre de la formation Data Analytics & IA d'Akieny Academy (Novembre 2026).**