# Olist E-Commerce Analytics - Projet Data & BI de bout en bout

[🇬🇧 English version](README.en.md) · [📅 Réserver un échange](https://cal.clixius.com/simon/echange)

## 🎯 Résumé exécutif

**Projet d'analyse de données de bout en bout** démontrant le pipeline complet, des données brutes jusqu'aux **dashboards Power BI** prêts pour la décision. Basé sur le jeu de données public [Olist Brazilian E-Commerce Dataset (Kaggle)](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce), ce projet couvre la **préparation des données** (Python), la **conception de KPI**, la **modélisation en star-schema**, et le **storytelling métier** au travers de dashboards interactifs.

> **Enseignement clé : les livraisons dépassant 30 jours génèrent 64% des avis négatifs.** Les livraisons rapides (≤7 jours) représentent 86% des avis positifs.

📥 **[Ouvrir le dashboard dans Power BI](https://raw.githubusercontent.com/SimonNC/olist-data-analysis/main/exports/olist_dashboard.pbix)** — fichier `.pbix` prêt à l'emploi, sans configuration.

---

## 🧠 Questions métier traitées

- Comment évolue la performance commerciale dans le temps, par catégorie et par région ?
- Quelle est l'efficacité de la performance de livraison au regard des engagements de SLA ?
- Quelle est la relation entre les retards de livraison et la satisfaction client ?
- Où l'entreprise devrait-elle prioriser ses efforts pour réduire les avis négatifs ?

---

## 📸 Dashboards

### Avis clients & satisfaction

**Objectif** : Identifier les leviers de la satisfaction client et quantifier l'impact de la performance de livraison sur les notes d'avis.

[![Reviews Dashboard](screenshots/reviews_dashboard.jpg)](screenshots/reviews_dashboard.jpg)

**KPIs** : Distribution des notes d'avis, répartition des avis dans le temps, corrélation entre retard de livraison et satisfaction.

---

### Performance commerciale

**Objectif** : Suivre la performance commerciale, les tendances de chiffre d'affaires, et identifier les catégories et régions les plus performantes.

[![Sales Dashboard](screenshots/sales_dashboard.jpg)](screenshots/sales_dashboard.jpg)

**KPIs** : Chiffre d'affaires total, volume de commandes, panier moyen (AOV), tendances mensuelles, principales catégories et états.

---

### Livraison & Logistique

**Objectif** : Suivre la performance opérationnelle, la fiabilité des SLA, et identifier les points de blocage de la livraison.

[![Delivery Dashboard](screenshots/delivery_dashboard.jpg)](screenshots/delivery_dashboard.jpg)

**KPIs** : Taux de livraison dans les délais, distribution des SLA, performance de livraison cumulée, seuils de bascule des SLA.

---

## 🏗️ Architecture du projet

```
.
├── data_cleaned/              # Données prêtes pour l'analyse (CSV + Parquet)
├── docs/
│   ├── data_models.md         # Documentation du modèle de données analytique
│   └── metrics.md             # Métriques métier & définitions des KPI
├── notebooks/
│   └── main.ipynb             # Pipeline Python de préparation des données
├── powerbi/                   # Projet Power BI (format PBIP)
├── screenshots/               # Captures d'écran des dashboards
├── README.en.md
├── README.md
└── .gitignore
```

---

## 🛠️ Stack technique

| Couche | Outils & approche |
|---|---|
| **Préparation des données** | Python (Pandas, NumPy), Jupyter Notebook |
| **Qualité des données** | Contrôles automatisés : unicité des clés primaires, champs obligatoires, règles métier (prix ≥ 0, notes 1-5), intégrité référentielle. Le pipeline s'arrête en cas d'échec. |
| **Stockage des données** | Parquet (principal, performance), CSV (secours, compatibilité) |
| **Modélisation des données** | Star-schema (faits/dimensions), dimension Date explicite, relations à sens unique |
| **BI & Visualisation** | Power BI (mode Import), mesures DAX centralisées par domaine, chemin de dossier paramétré |

---

## 📊 Modèle de données Power BI

[![Data Model](screenshots/data_model.jpg)](screenshots/data_model.jpg)

- Modèle inspiré du **star-schema**, optimisé pour le découpage et l'agrégation
- Dimension **Date** explicite pour l'intelligence temporelle
- Relations à sens unique pour un contexte de filtre prévisible
- **Mesures DAX** centralisées par domaine métier (Sales, Delivery, Reviews)

---

## 🧪 Pipeline Python de préparation des données

Chaque jeu de données suit un pipeline structuré et reproductible :

1. **Profilage des données** - Schéma, types de données, analyse des valeurs manquantes, filtrage par pertinence métier
2. **Nettoyage des données** - Normalisation des dates, harmonisation des statuts, validation numérique, calcul des SLA (tranches de délai de livraison)
3. **Contrôles qualité des données** - Contrôles automatisés avec arrêt du pipeline en cas d'échec
4. **Export** - Jeux de données propres en Parquet (principal) et CSV (secours)

---

## 💡 Enseignements clés

| Constat | Impact métier |
|---|---|
| La satisfaction chute fortement après ~25-30 jours de délai de livraison | Seuil de SLA critique identifié |
| Les livraisons >30 jours génèrent **64% des avis négatifs** | Cause racine claire de l'insatisfaction |
| Les livraisons ≤7 jours génèrent **86% des avis positifs** | La livraison rapide est un puissant levier de satisfaction |
| Ventes concentrées sur un petit nombre d'états & de catégories | Opportunité de priorisation pour la logistique |

---

## 💼 Recommandations métier

Sur la base de l'analyse de la performance commerciale, des SLA de livraison et des avis clients :

- **Signaler les commandes approchant les 20 jours** de délai de livraison et agir avant le seuil critique de 25-30 jours
- **Ajuster les engagements de SLA par région** - aligner les attentes des clients sur la performance de livraison réelle en dehors des grands hubs
- **Enquêter sur les catégories structurellement lentes** (articles volumineux, meubles) au niveau des fournisseurs et de la préparation des commandes
- **Déclencher une communication client proactive** pour les commandes retardées au-delà de 25 jours
- **Utiliser la performance de livraison comme indicateur avancé de l'expérience client** - surveiller les KPI logistiques aux côtés des notes d'avis comme signaux d'alerte précoce

---

## 🎯 Compétences démontrées

Ce projet démontre les compétences suivantes, alignées sur les exigences du marché pour un **Data Analyst** :

| Compétence | Comment elle est démontrée |
|---|---|
| **Power BI** (DAX, Power Query, star-schema) | Suite complète de dashboards avec modèle paramétré |
| **Conception de KPI & dashboarding** | KPI de chiffre d'affaires, de livraison et de satisfaction structurés par domaine |
| **Visualisation de données & storytelling** | Dashboards orientés enseignements, conçus pour les décideurs |
| **Préparation de données Python** | Pipeline reproductible avec contrôles qualité automatisés |
| **Modélisation de données prête pour SQL** | Star-schema avec granularités maîtrisées et intégrité référentielle |
| **Analyse des besoins métier** | Questions formulées du point de vue opérationnel, et non de l'outil |

---

## 🔗 Projets liés

Ce projet complète le portfolio aux côtés de :

- 👉 [Olist Analytics Engineering Pipeline](https://github.com/SimonNC/olist-dbt-duckdb) (SQL + dbt)
- 👉 [Customer Churn Prediction - Telco](https://github.com/SimonNC/telco-customer-churn-prediction) (Python + ML + Streamlit)

---

## 👤 Auteur

**Simon Jorite**
Data Analyst - [Certifié Microsoft Power BI Data Analyst (PL-300)](https://learn.microsoft.com/en-us/users/simonjorite-4846/credentials/b2cc3310a92a9302)

15 ans d'expérience en finance, opérations et e-commerce. Je transforme des jeux de données complexes en KPI fiables et en tableaux de bord prêts pour la décision.

- GitHub : [github.com/SimonNC](https://github.com/SimonNC)
- LinkedIn : [linkedin.com/in/simonjorite](https://www.linkedin.com/in/simonjorite)
- Email : simon.jorite@gmail.com
- Localisation : Lyon, France (Ouvert à un poste hybride ou en télétravail)
- Prise de RDV : [Réserver un échange de 30 min](https://cal.clixius.com/simon/echange)
