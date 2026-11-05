# AKIENY ACADEMY
**PROJET PAYSIM | GROUPE 3 (S18)**

## Note d'Orientation Technique

* **Date :** 04 Novembre 2026
* **Auteur :** Grace MOUSSONI (Lead Repo Admin)
* **Avenant au Document de Cadrage (v1.1)**

---

### Choix de la plateforme de gestion de code : Transition d'Azure DevOps vers GitHub

Dans le cadre du projet d'analyse des transactions financières PaySim, l'équipe a initialement prévu d'utiliser Microsoft Azure DevOps pour centraliser le code et gérer le versionnement des rapports Power BI. Ce document explique de façon simple et transparente les raisons opérationnelles qui nous amènent à choisir GitHub comme solution finale.

---

### 1. Le constat et le blocage sur Azure DevOps

Lors de la phase de création de l'organisation et du dépôt sur Azure DevOps, nous avons rencontré une contrainte administrative bloquante :

* **Exigence de Carte Bancaire :** Pour valider l'inscription et activer la capacité d'exécuter des traitements automatisés ou d'initialiser certains services de stockage dans Azure, la plateforme impose l'enregistrement préalable d'une carte de crédit, même lors de l'utilisation d'offres dites « gratuites ».

Pour un projet académique d'une durée restreinte (4 jours), cette contrainte pose deux problèmes majeurs :
* **Accessibilité financière :** Tous les membres du groupe ne disposent pas ou ne souhaitent pas engager leurs moyens de paiement personnels.
* **Risque d'échéance :** La vérification bancaire crée un délai d'attente inadapté à notre planning court (livraison finale le 06/11/2026).

---

### 2. Pourquoi GitHub est la solution parfaite

GitHub est la plateforme de gestion de code la plus utilisée au monde et appartient également au groupe Microsoft. Elle répond à 100% à nos besoins, sans aucune contrainte d'accès :

* **100% Gratuit et sans carte bancaire :** La création de compte et de dépôts privés se fait immédiatement avec une simple adresse email.

---

### 3. Tableau comparatif synthétique

| Critères | Azure DevOps (Repos) | GitHub |
| :--- | :--- | :--- |
| **Inscription** | Carte bancaire obligatoire | Gratuite & Instantanée (Simple email) |
| **Support Power BI (`.pbip`)** | Excellence (Format texte/JSON) | Identique (Excellence pour `.pbip`) |
| **Gestion de projet (Kanban)** | Azure Boards | GitHub Projects (Boards Kanban intégres) |
| **Travail en équipe** | Branches et Pull Requests | Branches et Pull Requests (Très simple) |

---

### 4. Impact sur le travail de l'équipe et conclusion

Ce changement de plateforme n'impacte en rien le planning ni les livrables du projet PaySim :

* Le dépôt GitHub privé est déjà opérationnel pour recevoir les projets Power BI (format `.pbip`).
* Chaque membre peut créer ses branches de fonctionnalités (`feature/xxx`) et proposer ses avancées via des Pull Requests.
* Le suivi des tâches en mode Scrumban s'effectue directement via l'outil GitHub Projects.

**En résumé :** GitHub nous offre exactement la même puissance technique qu'Azure, tout en garantissant un accès gratuit, immédiat et sans contrainte financière pour l'ensemble du Groupe 3.