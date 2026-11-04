# 🤝 CONTRIBUTING.md  
# Guide de contribution — Projet PaySim Fraud Analysis

Bienvenue sur le dépôt du projet **PaySim Fraud Analysis**, réalisé par le **Groupe 3 — Akieny Academy**.

Ce guide présente les règles de collaboration, les conventions de nommage et les bonnes pratiques à respecter afin de garantir :

- une collaboration efficace ;
- une structure Power BI cohérente ;
- un historique Git propre ;
- une documentation maintenable ;
- une qualité homogène des livrables.

---

# 📂 Structure du projet

Le projet utilise le format **Power BI Project (`.pbip`)** afin de faciliter le versioning Git et le travail collaboratif.

```text
PaySim-Fraud-Analysis/
│
├── sources_files/
│   ├── paysim_fraud_analysis.Report/
│   │   └── Couche visuelle Power BI (pages, graphiques, thèmes)
│   │
│   ├── paysim_fraud_analysis.SemanticModel/
│   │   └── Modèle de données (Power Query, DAX, relations)
│   │
│   └── paysim_fraud_analysis.pbib
│       └── Point d’entrée du projet Power BI
│
├── .gitignore
│   └── Fichiers exclus du versioning
│
├── LICENSE
│   └── Licence MIT
│
├── README.md
│   └── Documentation principale
│
└── CONTRIBUTING.md
    └── Guide de contribution
```

> ⚠️ **Important :** le fichier à ouvrir dans Power BI Desktop est `sources_files/paysim_fraud_analysis.pbib`.

---

# 1. Conventions de nommage

## Fichiers et dossiers Power BI

- **Projet principal :** `PaySim-Fraud-Analysis`
- **Dossier des sources :** `sources_files`
- **Modèle sémantique :** `paysim_fraud_analysis.SemanticModel`
- **Rapport Power BI :** `paysim_fraud_analysis.Report`
- **Projet Power BI :** `paysim_fraud_analysis.pbib`

## Tables et colonnes

### Tables de faits

Utiliser le préfixe `Fact` :

```text
FactTransactions
FactFraudEvents
```

### Tables de dimensions

Utiliser le préfixe `Dim` :

```text
DimTransactionType
DimDate
DimCustomer
```

### Colonnes

Conserver la nomenclature d’origine du dataset lorsque cela a du sens, ou utiliser le format `PascalCase`.

Exemples acceptés :

```text
amount
oldbalanceOrg
isFraud
isFlaggedFraud
```

ou :

```text
TransactionAmount
FraudRate
TransactionType
```

Éviter les espaces, les accents et les noms ambigus.

## Mesures DAX

Toutes les mesures doivent commencer par le préfixe `m_`.

### ✅ Correct

```text
m_TotalTransactions
m_TotalFraudAmount
m_FraudRate
m_AverageTransactionAmount
m_DetectionRate
```

### ❌ Incorrect

```text
Measure1
Calcul2
Test
NouvelleMesure
```

Les noms doivent être explicites et compréhensibles par l’ensemble de l’équipe.

---

# 2. Conventions Git et branches

⚠️ Ne travaillez jamais directement sur la branche `main`.

Avant toute modification :

```bash
git checkout main
git pull origin main
git checkout -b feature/ma-tache
```

## Nommage des branches

### Nouvelle fonctionnalité

```text
feature/<sujet>
```

Exemples :

```text
feature/dax-fraud-rate
feature/time-analysis
feature/dashboard-overview
```

### Correction

```text
fix/<sujet>
```

Exemples :

```text
fix/relationship-cardinality
fix/fraud-measure
```

### Documentation

```text
docs/<sujet>
```

Exemples :

```text
docs/readme-update
docs/contributing-update
```

---

# 3. Messages de commit

Utiliser le format **Conventional Commits** :

```text
<type>(<scope>): <description concise>
```

## Types autorisés

### `feat`

Ajout d’une fonctionnalité :

```text
feat(dax): add m_FraudRate measure
```

### `fix`

Correction :

```text
fix(model): correct relationship between tables
```

### `docs`

Documentation :

```text
docs(readme): update project structure
```

### `refactor`

Réorganisation sans changement fonctionnel :

```text
refactor(dax): simplify fraud calculations
```

### `chore`

Maintenance technique :

```text
chore(git): update gitignore
```

---

# 4. Gestion des fichiers et du cache

Le fichier `.gitignore` exclut les fichiers temporaires Power BI, les fichiers de cache locaux et les informations sensibles.

Exemples de règles attendues :

```gitignore
**/.pbi/localSettings.json
**/.pbi/cache.abf
*.tmp
.tmp/
*.user.json
.env
```

## Règles importantes

❌ Ne jamais ajouter au dépôt :

- les fichiers de cache Power BI ;
- les fichiers temporaires ;
- les mots de passe, clés API ou secrets ;
- les données personnelles ou sensibles.

❌ Ne jamais utiliser :

```bash
git add -f
```

pour contourner le `.gitignore`.

## Fichiers volumineux

GitHub limite la taille des fichiers à 100 Mo.

Les jeux de données volumineux doivent :

- être référencés dans la documentation ;
- ou être stockés sur une plateforme externe adaptée.

---

# 5. Pull Requests (PR)

Toute modification doit être intégrée via une **Pull Request**.

Aucun merge direct sur `main` n’est autorisé.

## Contenu attendu

Chaque Pull Request doit inclure :

### Résumé

Description rapide de la contribution.

### Modifications réalisées

- Mesures DAX ajoutées ou modifiées.
- Requêtes Power Query modifiées.
- Visuels créés ou mis à jour.
- Documentation mise à jour.

### Impact

Description des éventuels impacts sur :

- le modèle de données ;
- le rapport ;
- les indicateurs métiers.

---

# ✅ Checklist avant validation

Avant de demander la fusion de la Pull Request :

- [ ] Le projet s’ouvre correctement via `sources_files/paysim_fraud_analysis.pbib`.
- [ ] Les mesures DAX ont été testées.
- [ ] Les transformations Power Query fonctionnent correctement.
- [ ] Aucun fichier de cache Power BI n’est versionné.
- [ ] Aucun fichier sensible n’est présent dans le commit.
- [ ] La documentation a été mise à jour si nécessaire.
- [ ] Les conflits Git ont été résolus.
- [ ] Au moins un membre de l’équipe a relu la Pull Request.

---

# 📜 Licence

Ce projet est distribué sous licence **MIT**.

En contribuant à ce dépôt, vous acceptez que vos contributions soient publiées selon les termes de cette licence.

Consultez le fichier [`LICENSE`](./LICENSE) pour plus d’informations.