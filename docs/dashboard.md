# ✅ **3 — Tous les visuels détaillés (version finale basée sur ta table)**

Je te donne exactement **comment construire chaque visuel**, page par page, mis à jour pour la table `ukraine_2014_2022`.

---

# 📘 **PAGE 1 — Dashboard (Vue globale)**

### **Card 1 — Total Évènements**

* Visual : **Card**
* Value : `[Total Events]`

### **Card 2 — Total Fatalities**

* Value : `[Total Fatalities]`

### **Card 3 — Fatalités Civils**

* Value : `[Civil Fatalities]`

### **Card 4 — Fatalités Non Civils**

* Value : `[NonCivil Fatalities]`

---

### **Donut — Répartition des évènements par type**

* Visual : **Donut**
* Legend : `ukraine_2014_2022[event_type]`
* Values : `[Total Events]`

---

### **Bar chart — Top 5 pays (c’est souvent 1 seul, Ukraine, mais au cas où)**

* Axis : `ukraine_2014_2022[country]`
* Values : `[Total Fatalities]`
* Filter : Top N = 5 (By `[Total Fatalities]`)

---

### **Line Chart — Évolution dans le temps**

* Axis : `Date[Date]` (continuous)
* Values : `[Total Events]`

---

### **Carte (points) — Localisation des incidents**

* Latitude : `ukraine_2014_2022[latitude]`
* Longitude : `ukraine_2014_2022[longitude]`
* Size : `[Total Events]`
* Color : `[Total Fatalities]`
* Tooltip : id, date, event_type, location, fatalities

---

# 📅 **PAGE 2 — Analyse temporelle**

### **Line Chart — Évènements dans le temps**

* Axis : `Date[Date]`
* Values : `[Total Events]`

### **Area Chart — Fatalités par catégorie**

* Axis : `Date[Date]`
* Values :

  * `[Civil Fatalities]`
  * `[NonCivil Fatalities]`
  * `[Unknown Fatalities]`

---

### **Column Chart — Évènements par mois**

* Axis : `Date[Month]`
* Legend : `ukraine_2014_2022[event_type]`
* Values : `[Total Events]`

---

### **Slicer — Période**

* Field : `Date[Date]`
* Mode : **Between**

👉 Tous les visuels réagiront automatiquement grâce à la relation Date.

---

# 🌍 **PAGE 3 — Analyse géographique**

### **Filled Map — Fatalités par région (admin1)**

* Location : `ukraine_2014_2022[admin1]`
* Color : `[Total Fatalities]`

### **Map (points)**

* Lat/Long
* Size = `[Total Events]`
* Color = `[Total Fatalities]`

---

# 🎯 **PAGE 4 — Analyse par type d’évènement**

### **Bar Chart — Total Events by event_type**

* Axis : `ukraine_2014_2022[event_type]`
* Values : `[Total Events]`

### **Bar Chart — Sous-types**

* Axis : `ukraine_2014_2022[sub_event_type]`
* Values : `[Total Events]`

### **Line Chart — Fatalités par type dans le temps**

* Axis : `Date[Date]`
* Values : `[Total Fatalities]`
* Legend : `event_type`

---

# 📊 **PAGE 5 — Analyse avancée**

### **Scatter Plot — Fatalités vs Nombre d’évènements par region**

* X : `[Total Events]`
* Y : `[Total Fatalities]`
* Details : `ukraine_2014_2022[admin1]`
* Size : `[Avg Fatalities per Event]`

### **Heatmap — Fatalités par année et région**

* Rows : `ukraine_2014_2022[admin1]`
* Columns : `Date[Year]`
* Values : `[Total Fatalities]`
* Conditional formatting : color scale

---

# 📄 **PAGE 6 — Table complète**

Table avec colonnes :

* id
* year
* date_start
* date_end
* event_id_country
* event_type
* sub_event_type
* region
* country
* admin1 / admin2
* location
* latitude / longitude
* fatalities / fatalities_civilians / deaths_a/b/civilians/unknown
* source_ori / source_type_office

---

# 🔥 BONUS — Slicers globaux (à synchroniser entre pages)

👉 Ajoute ces slicers **et synchronise-les sur toutes les pages**
View → Sync Slicers

* Slicer 1 : `Date[Date]`
* Slicer 2 : `event_type`
* Slicer 3 : `country`
* Slicer 4 : `admin1`
* Slicer 5 : `region`

---

# 📌 Si tu veux aller encore plus loin :

Je peux maintenant te fournir :

### 🔧 Option A — **Le script Power Query** pour importer et nettoyer automatiquement ta table

### 🎨 Option B — **Un thème JSON Power BI** basé Ukraine (bleu marine + jaune)

### 📐 Option C — **Les formules DAX pour les KPI avancés (évolution, YoY, MoM, rolling 90 days)**

### 🗺 Option D — **Un layout de dashboard (fichier .json) compatible Power BI**

Dis-moi quelle option tu veux (A/B/C/D ou plusieurs), et je te la génère immédiatement.
