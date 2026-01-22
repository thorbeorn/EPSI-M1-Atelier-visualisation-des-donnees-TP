# Rapport d’analyse – Conflit en Ukraine (2014–2022)

**Auteur : Dylan Llodra et Nicolas Greault**  
**Outil : Power BI Desktop**

Ce projet vise à analyser les conflits armés en Ukraine entre 2014 et 2022 à partir de données historiques structurées. L’approche repose sur une chaîne de traitement de données et une visualisation interactive via Power BI.

---
## 0. Contexte et objectifs
Suite aux événements survenus en Ukraine depuis 2014 et à l’escalade majeure de février 2022,
ce projet vise à analyser les conflits armés sur le territoire ukrainien afin d’éclairer
les décisions géopolitiques.

Objectifs :
- Analyser l’évolution temporelle des conflits
- Identifier les types d’événements majeurs
- Évaluer l’impact humain, notamment civil
- Mettre en évidence les régions les plus touchées

---

## 1. Données et méthodologie

### 1.1 Sources de données

* ACLED – événements de conflit
* UCDP – données de violence et de mortalité
* Données géographiques et administratives

### 1.2 Architecture des données (Medallion)

* **Raw (Bronze)** : données CSV brutes
* **Silver** : nettoyage, typage, enrichissement (dates, coordonnées, civils)
* **Gold** : consolidation multi-sources, harmonisation sémantique

👉 Cette architecture garantit **qualité, traçabilité et performance analytique**.

---

## 2. Indicateurs clés (KPI)

| Indicateur                | Valeur  |
| ------------------------- | ------- |
| Nombre total d’événements | ~39 492 |
| Nombre total de décès     | ~41 000 |
| Décès civils              | ~17 000 |
| Régions impactées         | 27      |

---

## 3. Analyse temporelle

L’analyse temporelle met en évidence :

* Une phase initiale (2014–2016) marquée par des combats localisés
* Une stabilisation relative (2017–2020)
* Une explosion du nombre d’événements et de décès en 2021–2022

---

## 4. Analyse géographique

Les cartes révèlent une **concentration spatiale forte** :

* Donetsk
* Luhansk
* Kharkiv
* Mariupol

Ces régions combinent :

* forte densité d’événements
* nombre élevé de victimes civiles

---

## 5. Analyse par type d’événement

Les événements dominants sont :

* **Battles**
* **Explosions / attaques à distance**
* **Violence against civilians**

Ces catégories représentent la majorité des décès.

---

## 6. Sources et acteurs

Les sources principales :

* OSCE SMM Ukraine
* Ministère de la Défense ukrainien
* Forces armées locales

La diversité et la récurrence des sources renforcent la **fiabilité analytique**.

---

## Conclusion générale

Ce projet démontre la capacité des outils BI à :

* structurer des données complexes de conflit,
* produire une analyse géopolitique robuste,
* soutenir la prise de décision stratégique.

Le dashboard Power BI constitue un **outil opérationnel et décisionnel** adapté aux institutions publiques.