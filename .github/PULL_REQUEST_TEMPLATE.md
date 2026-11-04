# 🔀 Pull Request - PaySim Fraud Analysis

## 📌 Résumé

<!-- Décrivez brièvement l'objectif de cette Pull Request et le problème qu'elle résout. -->

### Type de contribution

- [ ] ✨ Nouvelle fonctionnalité (visuel, page, mesure, table)
- [ ] 🐛 Correction de bug (DAX, modèle, relation, Power Query)
- [ ] 📚 Documentation (`README.md`, `CONTRIBUTING.md`, etc.)
- [ ] ♻️ Refactoring (sans modification fonctionnelle)
- [ ] 🔧 Maintenance / configuration (`.gitignore`, structure du projet, etc.)

### Issue associée

```text
#<numéro>
```

ou

```text
Aucune
```

---

# 🛠️ Modifications réalisées

## 🧠 Modèle sémantique (`.SemanticModel`)

### Éléments concernés

- [ ] Nouvelle table ajoutée
- [ ] Table modifiée
- [ ] Relation créée
- [ ] Relation modifiée
- [ ] Requête Power Query ajoutée
- [ ] Requête Power Query modifiée
- [ ] Colonne calculée ajoutée
- [ ] Colonne calculée modifiée

### Détails

```text
Exemple :
Ajout de la table DimDate et création d'une relation active avec FactTransactions.
```

---

## 📊 Mesures DAX

### Actions réalisées

- [ ] Nouvelle mesure
- [ ] Mesure modifiée
- [ ] Mesure supprimée

### Mesures concernées

| Mesure | Action | Description |
|----------|----------|----------|
| m_FraudRate | Ajoutée | Calcul du taux global de fraude |
| m_TotalTransactions | Modifiée | Ajustement du filtre temporel |

---

## 📈 Rapport Power BI (`.Report`)

### Éléments concernés

- [ ] Nouvelle page de rapport
- [ ] Page modifiée
- [ ] Nouveau visuel
- [ ] Visuel modifié
- [ ] Mise à jour du thème
- [ ] Mise à jour de la charte graphique

### Pages concernées

```text
Exemple :
Page "Vue d'ensemble" :
- Ajout d'un KPI de taux de fraude
- Ajout d'un graphique de répartition des montants frauduleux
```

---

## 📚 Documentation

### Documents mis à jour

- [ ] README.md
- [ ] CONTRIBUTING.md
- [ ] Dictionnaire de données
- [ ] Notes de cadrage
- [ ] Autre

### Détails

```text
Décrire les modifications apportées à la documentation.
```

---

# 📸 Captures d'écran

## Avant

<!-- Insérer capture -->

---

## Après

<!-- Insérer capture -->

---

# 📈 Impact attendu

## Modèle de données

```text
Décrire l'impact sur la structure du modèle.
```

## Mesures et indicateurs

```text
Décrire l'impact sur les KPIs ou calculs métier.
```

## Rapport utilisateur

```text
Décrire l'impact sur l'expérience utilisateur.
```

## Performance

```text
Décrire l'impact éventuel sur les performances.
```

---

# 🧪 Tests effectués

```text
Exemple :

- Vérification de la mesure m_FraudRate
- Contrôle des relations du modèle
- Actualisation des données sans erreur
- Validation des filtres croisés
- Vérification des visuels sur toutes les pages
```

---

# ✅ Checklist avant validation

## Fonctionnel

- [ ] Le projet s'ouvre correctement via `paysim_fraud_analysis.pbip`
- [ ] Les données s'actualisent sans erreur
- [ ] Les mesures DAX ont été testées
- [ ] Les transformations Power Query fonctionnent correctement
- [ ] Les visuels affichent des résultats cohérents

## Modèle de données

- [ ] Les relations ont été vérifiées
- [ ] Les cardinalités sont correctes
- [ ] Les sens de filtrage ont été vérifiés

## Git & Qualité

- [ ] Les conflits avec `main` ont été résolus
- [ ] Aucun fichier temporaire n'est versionné
- [ ] Aucun fichier sensible n'est inclus
- [ ] Le `.gitignore` fonctionne correctement
- [ ] La documentation a été mise à jour si nécessaire

## Revue

- [ ] Au moins un membre de l'équipe a relu cette Pull Request
- [ ] Les commentaires de revue ont été traités

---

# 📝 Notes pour le reviewer

```text
Exemple :

Merci de porter une attention particulière à la mesure DAX m_FraudRate ainsi qu'à la nouvelle relation entre FactTransactions et DimDate.
```