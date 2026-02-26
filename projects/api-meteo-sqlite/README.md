# Projet : API météo → SQLite → SQL (CTE)

Ce projet illustre un pipeline data complet et réaliste : récupération de données météo via API, stockage dans une base SQLite, puis analyse via SQL avancé (CTE, agrégations, comparaison temporelle).  
Il s’agit d’un cas typique de micro‑mission freelance : automatiser la collecte, structurer les données et produire des indicateurs fiables.

---

## 🎯 Objectifs du projet

- Récupérer les données météo via l’API Open‑Meteo  
- Transformer le JSON en DataFrame Pandas  
- Créer une base SQLite locale  
- Insérer les données dans une table dédiée  
- Réaliser des analyses SQL avancées avec CTE :  
  - calcul min / max / moyenne  
  - comparaison avec la veille  
  - comparaison avec la moyenne du mois  
  - détection de valeurs anormales  
- Produire un pipeline reproductible

---

## 🧱 Architecture du pipeline

1. **Extraction (API)**  
   Appel HTTP → JSON → DataFrame Pandas.

2. **Chargement (SQLite)**  
   Création d’une base locale `meteo.db`  
   Insertion des données dans une table `temperatures`.

3. **Transformation & Analyse (SQL)**  
   Requêtes SQL avec CTE pour structurer les étapes :  
   - nettoyage  
   - agrégations  
   - calculs intermédiaires  
   - comparaison temporelle

---

## 🛠️ Technologies et compétences

- **Python** : requests, Pandas, sqlite3  
- **SQL** : CTE, agrégations, window functions simples  
- **Data cleaning** : normalisation des dates, types, valeurs manquantes  
- **Data modeling** : création de table, insertion, structuration  
- **SQLite** : base légère, portable, idéale pour portfolio  
- **Notebook Jupyter** pour la présentation

---

## 📓 Structure du projet

api-meteo-sqlite/
│
├── notebook.ipynb        # Pipeline complet Python + SQL
├── requetes.sql          # Requêtes SQL (CTE, analyses)
├── meteo.db              # Base SQLite (optionnel, ou générée par le notebook)
├── README.md             # Documentation (ce fichier)
└── data/                 # Données sauvegardées

---

## 🧪 Analyses réalisées (SQL + CTE)

- Température minimale, maximale et moyenne du jour  
- Comparaison avec la veille  
- Comparaison avec la moyenne du mois  
- Calcul de moyennes glissantes (CTE + window functions)  
- Détection de valeurs aberrantes  
- Agrégations par heure, jour, semaine

---

## 📊 Exemple de CTE utilisé

```sql
WITH daily AS (
    SELECT 
        DATE(datetime) AS jour,
        MIN(temperature) AS temp_min,
        MAX(temperature) AS temp_max,
        AVG(temperature) AS temp_moy
    FROM temperatures
    GROUP BY DATE(datetime)
),
comparison AS (
    SELECT 
        d1.jour AS jour,
        d1.temp_moy AS moyenne_jour,
        d2.temp_moy AS moyenne_veille,
        d1.temp_moy - d2.temp_moy AS difference
    FROM daily d1
    LEFT JOIN daily d2 ON d2.jour = DATE(d1.jour, '-1 day')
)
SELECT * FROM comparison;

