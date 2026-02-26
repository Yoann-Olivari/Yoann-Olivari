# Projet : Analyse météo via API (Python)

Ce projet illustre un cas concret de micro‑mission data : récupérer automatiquement des données météo via une API, les nettoyer, les analyser et produire des indicateurs simples (min, max, moyenne), ainsi qu’une comparaison avec des valeurs antérieures.

---

## 🎯 Objectifs du projet

- Récupérer les données météo d’un jour précis via l’API Open‑Meteo  
- Transformer le JSON en DataFrame Pandas  
- Calculer les températures minimale, maximale et moyenne de la journée  
- Comparer la température moyenne avec celle de la veille  
- (Optionnel) Comparer avec la moyenne du mois en cours  
- Préparer un petit pipeline reproductible

---

## 🌦️ Données utilisées

Les données proviennent de l’API **Open‑Meteo**, gratuite et sans clé API.  
Format : JSON → conversion en DataFrame.

Variables utilisées :
- `temperature_2m` (température horaire)
- `time` (horodatage)

---

## 🛠️ Technologies et compétences

- **Python** : requests, Pandas, datetime  
- **Data cleaning** : parsing de dates, gestion des types  
- **Analyse** : min, max, moyenne, comparaison temporelle  
- **API** : requêtes HTTP, paramètres dynamiques  
- **Notebook Jupyter** pour la présentation

---

## 📓 Structure du projet

api-meteo-python/
│
├── notebook.ipynb        # Code complet du projet
├── README.md             # Documentation (ce fichier)
└── data/                 # (Optionnel) données sauvegardées

---

## 📊 Résultats obtenus

- Température minimale du jour  
- Température maximale du jour  
- Température moyenne  
- Comparaison avec la veille  
- (Optionnel) Comparaison avec la moyenne du mois  
- Visualisation simple (si ajoutée)

Ces résultats permettent de construire un mini‑pipeline reproductible, utile pour automatiser un reporting météo quotidien.

---

## 🔄 Améliorations possibles

- Stocker les données dans SQLite  
- Faire une version SQL avec CTE (projet suivant)  
- Automatiser l’exécution quotidienne  
- Ajouter des graphiques (matplotlib / seaborn)


