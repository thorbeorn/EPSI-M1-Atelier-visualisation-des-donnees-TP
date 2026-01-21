# Rapport Technique – Pipeline de Données et Visualisation du Conflit en Ukraine (2014–2022)

**Auteur : Dylan Llodra et Nicolas Gréault**  
**Outil principal : Power BI Desktop**  
**Technologies : Power Query (M), CSV, Modèle tabulaire Power BI**

---

## 1. Introduction

Ce projet vise à analyser les conflits armés en Ukraine entre 2014 et 2022 à partir de plusieurs sources ouvertes. L'objectif est de concevoir une chaîne de traitement robuste permettant :

- L'intégration de données hétérogènes,
- Leur nettoyage et enrichissement,
- La consolidation multi-sources,
- La visualisation interactive à destination des décideurs.

L’architecture adoptée suit le modèle **Medallion Architecture (Bronze / Silver / Gold)** afin de garantir la qualité, la traçabilité et la performance analytique.

---

## 2. Architecture globale du projet

### 2.1 Organisation des couches

Le projet est structuré en trois niveaux :

### Bronze (Raw)

- Fichiers CSV sources
- Données non modifiées
- Conservation du format original

Sources principales :

- ACLED (événements de conflits)
- UCDP (données de violence et mortalité)

### Silver (Nettoyage et enrichissement)

- Typage strict des colonnes
- Harmonisation des noms
- Nettoyage des valeurs manquantes
- Enrichissement temporel
- Normalisation géographique

Tables Silver :

- `[SILVER]2019-07-16-2022-07-24-Ukraine`
- `[SILVER]conflict_data_ukr`

### Gold (Modèle analytique)

- Fusion multi-sources
- Normalisation sémantique
- Suppression des colonnes inutiles
- Création de mesures métiers

Tables Gold :

- `[GOLD]ukraine_2014_2022`
- `[GOLD]Mesures_Globales`

---

## 3. Pipeline ETL – Source ACLED

### 3.1 Chargement

Chargement du fichier CSV contenant les événements :

- Délimiteur : ","
- Encodage : Windows-1252
- 31 colonnes

### 3.2 Promotion des en-têtes

Les premières lignes sont converties en noms de colonnes afin d'obtenir un schéma exploitable.

### 3.3 Typage des données

Typage strict des colonnes critiques :

- Dates → type `date`
- Coordonnées → `number`
- Identifiants → `Int64`

Cela permet :

- d'éviter les erreurs de calcul,
- d'améliorer les performances,
- d'assurer la cohérence analytique.

### 3.4 Harmonisation des noms

Standardisation des colonnes :

- `data_id` → `id`
- `iso` → `code_ISO_country`
- `event_date` → `start_event_date`

Objectif : aligner les noms entre sources.

### 3.5 Nettoyage des valeurs manquantes

Remplacement des valeurs vides par :

```
"no information"
```

Sur les colonnes textuelles sensibles :

- acteurs
- zones administratives

### 3.6 Enrichissement métier

#### Calcul des morts civiles

Création d'une colonne calculée :

- Analyse des champs `actor1` et `actor2`
- Si présence du mot `civilians`
- Attribution des fatalities à `fatalities_civilians`

Cela permet une analyse différenciée :

- pertes civiles
- pertes militaires

### 3.7 Conversion du timestamp Unix

Transformation du timestamp en date réelle :

- Base : 01/01/1970
- Ajout de la durée en secondes

Résultat :

- `end_event_date`

---

## 4. Pipeline ETL – Source UCDP

### 4.1 Chargement et nettoyage initial

- Encodage UTF-8
- Suppression de la première ligne parasite
- Suppression des lignes en erreur

### 4.2 Typage et normalisation

Colonnes critiques :

- années
- coordonnées
- dates début/fin

Conversion des formats américains vers standards Power BI.

### 4.3 Enrichissement sémantique

Création d'une colonne `event_type` à partir du code `type_of_violence` :

| Code | Traduction |
------|------
1 | State armed conflict
2 | Non-state violence
Autre | Not specified

### 4.4 Nettoyage texte

Uniformisation des libellés administratifs et géographiques.

---

## 5. Consolidation Gold – Ukraine 2014–2022

### 5.1 Fusion multi-sources

Utilisation de :

```
Table.Combine()
```

Objectif :

- agréger ACLED + UCDP
- produire une table analytique unique

### 5.2 Suppression des colonnes inutiles

Optimisation du modèle :

- suppression des colonnes techniques
- retrait des métadonnées inutiles
- réduction mémoire

### 5.3 Harmonisation géographique

Normalisation manuelle des régions :

- Kyiv City → Kyiv
- Odessa Oblast → Odesa
- Autonomous Republic of Crimea → Crimea

### 5.4 Normalisation régionale

Correction automatique :

- valeurs nulles remplacées par `Europe`

---

## 6. Modèle analytique Power BI

### 6.1 Tables principales

- Ukraine_2014_2022
- Mesures_Globales

### 6.2 Mesures calculées

Principaux KPI :

- Nombre total d'événements
- Total fatalities
- Décès civils
- Décès militaires
- Nombre de régions impactées

### 6.3 Relations

Relations basées sur :

- Dates
- Régions
- Types d'événements

---

## 7. Visualisations du Dashboard

### 7.1 Analyse temporelle

- évolution annuelle
- évolution mensuelle
- pics de violence

### 7.2 Analyse géographique

- Carte Azure Maps
- densité d'événements
- concentration des décès

### 7.3 Analyse par type

- Battles
- Explosions
- Violence against civilians

### 7.4 Analyse avancée

- corrélation durée / décès
- comparaison inter-annuelle
- analyse multi-dimensionnelle

---

## 8. Performance et optimisation

### 8.1 Bonnes pratiques appliquées

- typage en amont
- suppression colonnes inutiles
- calculs déplacés dans Power Query
- réduction cardinalité texte

### 8.2 Avantages obtenus

- modèle plus léger
- temps de chargement réduit
- meilleure réactivité dashboard

---

## 9. Limites du projet

- dépendance aux sources ouvertes
- possibles biais de déclaration
- données incomplètes pour certaines régions

---

## 10. Perspectives d'amélioration

- ajout de données ONU
- intégration temps réel
- modèle prédictif
- segmentation par acteurs
- analyse de corrélation économique

---

## Conclusion

Ce projet démontre :

- la robustesse d'une architecture Medallion
- l'efficacité de Power Query pour l'ETL
- la valeur stratégique d'un dashboard décisionnel

Il constitue une base solide pour des analyses géopolitiques avancées et une aide à la décision institutionnelle.

