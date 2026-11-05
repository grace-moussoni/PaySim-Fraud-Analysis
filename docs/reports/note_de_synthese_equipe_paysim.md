# PaySim — Note de synthèse pour l'équipe

**Projet PaySim Groupe 3 | AKIENY ACADEMY**  
*5 novembre 2026*

Cette note présente l'exploration des données, résume le nettoyage déjà effectué par la Cheffe de Projet, puis indique à chacun les KPI et les graphiques à construire dans Power BI. Les valeurs de référence ont été calculées sur le CSV complet : elles servent à vérifier que vos visuels affichent les bons chiffres.

---

## 1. Le jeu de données en bref

* **6 362 620 transactions** de mobile money simulées, sur 743 pas de temps ($1\text{ pas} = 1\text{ heure}$).
* **5 types de transactions :** `CASH_IN`, `CASH_OUT`, `DEBIT`, `PAYMENT`, `TRANSFER` (écrits avec un underscore dans le CSV, pas avec un tiret).
* Le CSV d'origine n'est **jamais modifié** : tout le nettoyage se fait dans Power Query.

---

## 2. Exploration et signification des colonnes

Le CSV contient 11 colonnes qui décrivent chaque transaction : qui paie, qui reçoit, combien, quand, et si la transaction est une fraude ou a été signalée par le système d'alerte.

### Ce que l'exploration a montré

| Élément | Constat |
| ----- | ----- |
| **Structure** | 6 362 620 lignes, 11 colonnes, aucune valeur manquante |
| **Période** | 743 pas de temps ($1\text{ pas} = 1\text{ heure}$), de `step 1` à `step 743`, sans pas manquant |
| **Types de transactions** | `CASH_OUT` : 2 237 500 \| `PAYMENT` : 2 151 495 \| `CASH_IN` : 1 399 284 \| `TRANSFER` : 532 909 \| `DEBIT` : 41 432 |
| **Comptes** | 6 353 307 émetteurs distincts (identifiants en `C`) et 2 722 362 destinataires distincts (identifiants en `C` ou `M`) |
| **Commerçants** | 2 151 495 destinataires en `M`, tous dans des transactions `PAYMENT` ; aucun émetteur n'est un commerçant |
| **Fraudes** | 8 213 lignes (0,129%), uniquement dans `CASH_OUT` (4 116) et `TRANSFER` (4 097) |
| **Système d'alerte** | 16 lignes signalées, toutes des `TRANSFER` et toutes de vraies fraudes ; le montant minimal signalé est 353 874 |
| **Montants** | De 0 à 92,4 M ; médiane d'environ 74 900 ; moyenne d'environ 179 900 |

### Dictionnaire des colonnes

| Colonne | Signification | Dans le modèle Power BI |
| ----- | ----- | ----- |
| `step` | Unité de temps : 1 pas = 1 heure, de 1 à 743 | Conservée |
| `type` | Nature de l'opération : `CASH_IN` (dépôt d'espèces), `CASH_OUT` (retrait d'espèces), `DEBIT` (envoi vers un compte bancaire), `PAYMENT` (paiement à un commerçant), `TRANSFER` (envoi vers un autre utilisateur) | Conservée |
| `amount` | Montant de la transaction, en monnaie locale | Conservée |
| `nameOrig` | Identifiant du client qui initie la transaction (commence par C) | Retirée (trop lourde) |
| `oldbalanceOrg` | Solde de l'émetteur avant la transaction | Retirée |
| `newbalanceOrig` | Solde de l'émetteur après la transaction | Retirée |
| `nameDest` | Identifiant du destinataire : C pour un client, M pour un commerçant | Retirée (trop lourde) |
| `oldbalanceDest` | Solde du destinataire avant la transaction (aucune information pour les commerçants) | Retirée |
| `newbalanceDest` | Solde du destinataire après la transaction (aucune information pour les commerçants) | Retirée |
| `isFraud` | 1 si la transaction a été faite par un agent frauduleux de la simulation (prise de contrôle d'un compte, transfert vers un autre compte, puis retrait), 0 sinon ; c'est la réalité à prédire | Conservée |
| `isFlaggedFraud` | 1 si le système d'alerte a signalé la transaction : tentative de transfert de plus de 200 000 en une seule transaction, 0 sinon ; c'est la prédiction du système | Conservée |

### Colonnes créées lors du nettoyage

| Colonne | Signification |
| ----- | ----- |
| `Jour` | Jour du mois, de 1 à 31 : $\text{INT}((\text{step} - 1) / 24) + 1$ |
| `Heure` | Heure de la journée, de 0 à 23 : $\text{MOD}(\text{step} - 1, 24)$ |
| `Tranche_Montant` | Tranche de montant : `< 10 k`, `10 k - 50 k`, `50 k - 200 k`, `200 k - 1 M`, `> 1 M` |

> Les colonnes de soldes sont retirées car les transactions détectées comme fraude sont annulées dans la simulation : ces soldes ne reflètent pas la réalité et ne doivent pas servir à détecter la fraude. Les définitions des types de transaction viennent de la description Kaggle du jeu de données.

---

## 3. Nettoyage effectué

| Contrôle | Constat | Décision |
| ----- | ----- | ----- |
| **Valeurs manquantes** | 0 sur les 11 colonnes | Rien à corriger |
| **Doublons** | 0 (lignes complètes et clé `step`/`type`/`amount`/comptes) | Rien à supprimer |
| **Types de colonnes** | Montants en point décimal (format anglais) | Typage avec la culture `en-US` pour éviter les erreurs de lecture |
| **Montants nuls** | 16 lignes à montant 0, toutes des fraudes `CASH_OUT` | Conservées (ce sont des fraudes) |
| **Incohérences montants/soldes** | 5 077 691 lignes (environ 80%) | Conservées : elles font partie de la logique de la simulation, ce ne sont pas des erreurs |
| **Montants très élevés** | Jusqu'à 92,4 M | Conservés : valeurs réelles de la simulation |
| **Colonnes de soldes** | `oldbalanceOrg`, `newbalanceOrig`, `oldbalanceDest`, `newbalanceDest` | Retirées : les fraudes détectées sont annulées, donc ces colonnes faussent la détection |
| **Identifiants de comptes** | `nameOrig`, `nameDest` : plus de 6 M de valeurs uniques | Retirés pour alléger le modèle (6,3 M de lignes) |

* **Colonnes disponibles dans la table `Transactions` :** `step`, `type`, `amount`, `isFraud`, `isFlaggedFraud`, plus trois colonnes créées : `Jour` (1 à 31), `Heure` (0 à 23) et `Tranche_Montant` (`< 10 k`, `10 k - 50 k`, `50 k - 200 k`, `200 k - 1 M`, `> 1 M`).
* **Particularité à connaître :** Le CSV s'arrête au pas 743 et non 744. Le jour 31 est donc incomplet (heures 0 à 22).

---

## 4. KPI à afficher

Toutes les mesures se créent dans *Accueil > Nouvelle mesure*.

| KPI | Définition | Valeur attendue |
| ----- | ----- | ----- |
| **Nombre de transactions** | Nombre de lignes | 6 362 620 |
| **Nombre de fraudes** | Lignes avec `isFraud = 1` | 8 213 |
| **Taux de fraude** | Fraudes / transactions | 0,129% |
| **Montant total** | Somme de `amount` | environ 1 144 milliards |
| **Montant frauduleux** | Somme de `amount` des fraudes | environ 12,06 milliards |
| **Part du montant fraudé** | Montant frauduleux / montant total | environ 1,05% |
| **Montant moyen d'une fraude** | Moyenne de `amount` des fraudes | environ 1,47 M (contre ~178 000 pour une transaction normale) |
| **Fraudes signalées** | Lignes avec `isFlaggedFraud = 1` | 16 |
| **Rappel (taux de détection)** | $VP / (VP + FN)$ | environ 0,19% |
| **Précision** | $VP / (VP + FP)$ | 100% (aucun faux positif) |
| **Montant fraudé non détecté** | Somme de `amount` des fraudes non signalées | environ 11,98 milliards |

### Matrice de confusion (`isFraud` = réalité, `isFlaggedFraud` = prédiction du système)

| | Signalée | Non signalée |
| ----- | ----- | ----- |
| **Fraude** | $VP = 16$ | $FN = 8 197$ |
| **Non-fraude** | $FP = 0$ | $VN = 6 354 407$ |

---

## 5. Graphiques à construire, par axe

### Axes 1 et 2 — Ampleur, types et montants (Christ Roland)
* **Cartes KPI :** nombre de fraudes, taux de fraude, montant frauduleux.
* **Graphique en anneau fraude / normale :** montre le fort déséquilibre du jeu de données.
* **Histogramme du nombre de transactions par type.**
* **Histogramme du nombre de fraudes par type :** elles n'existent que dans `CASH_OUT` (4 116) et `TRANSFER` (4 097).
* **Taux de fraude par type :** `TRANSFER` 0,77%, `CASH_OUT` 0,18%, les trois autres types 0%.
* **Montants moyen, médian et maximum des fraudes par type** (médiane ~441 000, maximum 10 M).
* **Taux de fraude par tranche de montant :** passe de 0,02% sous 10 k à environ 2,07% au-dessus de 1 M.

### Axe 3 — Analyse temporelle (Marthinet)
* **Courbe du nombre de fraudes par jour** (entre 216 et 320 par jour).
* **Histogramme du nombre de fraudes par heure :** presque constant, autour de 340 par heure.
* **Courbe du taux de fraude par heure :** dépasse 22% vers 3 h et 4 h du matin, contre environ 0,05% en fin d'après-midi.
* **Matrice jour x heure** avec mise en forme conditionnelle sur le nombre de fraudes.
* **Point à signaler :** Les heures 0 à 5 concentrent 25% des fraudes pour moins de 1% des transactions.

### Axe 4 — Évaluation du système d'alerte (Sublime)
* **Matrice de confusion** (visuel Matrice, avec $VP, FN, FP, VN$).
* **Cartes :** rappel, précision, score F1, montant fraudé non détecté.
* **Comparaison des fraudes `TRANSFER`** au-dessus et en dessous du seuil de 200 000 : 2 740 au-dessus, 1 357 en dessous.
* **Message clé :** Le système ne signale presque rien. Le montant fraudé non détecté est de l'ordre de 12 milliards, contre environ 78 millions de fraudes signalées.

### Tableau de bord (Sublime, avec Christ et Marthinet)
* Une page de synthèse avec les cartes KPI principales.
* Segments (filtres) sur `type`, `jour`, `heure` et `statut de fraude`.
* Une page « À propos » avec les limites.

---

## 6. Points d'attention

1. Ne pas utiliser les colonnes de soldes pour détecter la fraude.
2. Utiliser les types avec underscore (`CASH_OUT`, `CASH_IN`) dans les filtres et les mesures.
3. Les données sont simulées : les résultats montrent des mécanismes, pas la réalité d'un opérateur précis.
4. Le scénario de fraude est unique (prise de contrôle d'un compte puis retrait) et le jeu de données est très déséquilibré.
5. Le jour 31 est incomplet : à signaler sur les graphiques par jour.

---

## 7. Pistes de recommandations (T10)

* Compléter la règle des 200 000 par des critères sur le type de transaction (`TRANSFER` et `CASH_OUT`) et sur le montant, car 1 357 fraudes `TRANSFER` passent sous le seuil.
* Renforcer la surveillance de nuit (de 0 h à 5 h), où le taux de fraude est très élevé.
* Surveiller les montants supérieurs à 1 M, où le taux de fraude est le plus fort.
* Alerter sur l'enchaînement `TRANSFER` puis `CASH_OUT`.

---

## 8. Contrôles avant de partager le `.pbix`

Vérifier que le fichier affiche bien :
* **6 362 620** transactions
* **8 213** fraudes
* **16** signalées
* $VP = 16, FN = 8 197, FP = 0, VN = 6 354 407$