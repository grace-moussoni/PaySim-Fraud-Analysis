# 🛠️ Note d'Orientation et Gouvernance Git — Repository Administrator

**Projet PaySim Groupe 3 | AKIENY ACADEMY**  
**Date :** Novembre 2026  

---

## 📖 1. Contexte & Démarche de l'Admin Repo

**La mission principale** a été d'établir un cadre de collaboration fluide, traçable et structuré pour l'équipe (Groupe 3). Face aux contraintes d'un projet court (4 jours) impliquant un volume massif de données (6,3 millions de lignes), des arbitrages techniques et organisationnels stricts ont été mis en place.

Cette note retrace la méthode, les choix d'architecture sous Git/GitHub et les règles de contribution adoptées tout au long du projet.

---

## 🏛️ 2. Choix d'Architecture & Rationalisation

### 2.1. Transition d'Azure DevOps vers GitHub
- **Motivation :** Prise en main plus rapide, gestion visuelle du Kanban centralisé et intégration native du Markdown pour la documentation.
- **Livrables :** Rédaction et validation de la note d'arbitrage technique (`docs/note_d_arbitrage_technique.md`).

### 2.2. Adoption du Format Modernisé Power BI (`.pbip` / TMDL)
- **Problématique :** Les fichiers binaires `.pbix` classiques se prêtent très mal au versioning avec Git (conflits indémêlables).
- **Solution :** Utilisation du format **Power BI Project (`.pbip`)** séparant le rapport (`.Report/`) et le modèle sémantique (`.SemanticModel/`). Les transformations Power Query et les métadonnées sont stockées au format lisible **TMDL**, permettant de suivre l'historique précis des modifications du modèle.

---

## 📂 3. Standardisation de la Documentation (.md)

Pour garantir une lisibilité optimale directement depuis l'interface GitHub, l'ensemble des livrables textuels et des comptes-rendus a été systématiquement converti au format **Markdown (`.md`)** et organisé dans une arborescence claire :

- `docs/document_de_cadrage_paysim.md` : Document de cadrage et méthodologie CRISP-DM / Scrumban.
- `docs/note_d_arbitrage_technique.md` : Justification de l'abandon d'Azure DevOps au profit de GitHub.
- `docs/reports/compte_rendu_de_reunion_3_novembre_2026.md` : Répartition des rôles et des colonnes de données.
- `docs/reports/note_de_synthese_equipe_paysim.md` : Guide des KPI de référence et des visuels à construire.
- `README.md` & `CONTRIBUTING.md` : Guide d'accueil, lien vers Kaggle et règles de contribution.

---

## ⚙️ 4. Stratégie Git & Gestion des Flux de Travail (Workflow)

### 4.1. Interdiction des Push Directs sur `main`
Afin de protéger la stabilité de la branche principale :
- Tout développement de fonctionnalité ou ajout documentaire doit **impérativement** passer par une branche dédiée (`feature/` ou `docs/`).
- La fusion vers `main` s'effectue exclusivement par **Pull Request (PR)**.

### 4.2. Convention de Nommage des Branches & Commits
Mise en place de la convention **Conventional Commits** pour maintenir un historique Git propre :
- `feat(...)` : Ajout d'une fonctionnalité ou script (ex: Power Query).
- `docs(...)` : Mise à jour de la documentation.
- `fix(...)` : Correction de bogues ou d'erreurs de script.

### 4.3. Gestion du Fichier CSV (6,3 Millions de lignes)
- **Contrainte :** GitHub limite les fichiers joints à 100 Mo (le CSV PaySim pèse ~500 Mo).
- **Décision d'Admin :** Exclusion du CSV du versioning Git via le fichier `.gitignore`.
- **Convention locale d'équipe :** Unification du chemin d'accès local sur le disque `C:\PaySim\PS_20174392719_1491204439457_log.csv` pour l'ensemble des membres Windows, garantissant l'exécution immédiate du script Power Query partagé sans rupture de source.

---

## 🤝 5. Fluidification de la Collaboration

- **Template de PR (`.github/PULL_REQUEST_TEMPLATE.md`) :** Standardisation des demandes de fusion pour obliger la vérification des checklists avant validation.
- **Ajustement de la Politique de Review :** Pour éviter les blocages liés à la réactivité variable de l'équipe et préserver le rythme de livraison, l'Admin Repo s'est réservé le droit de contourner l'approbation obligatoire par un tiers sur les branches documentaires, tout en maintenant l'exigence de la Pull Request.

---

## 🎯 Conclusion

Cette approche rigoureuse d'administration a permis de transformer un simple projet d'analyse de données en un dépôt logiciel maintenable, documenté et conforme aux standards de l'ingénierie moderne.