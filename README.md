# 🛍️ Segmentation des Clients d'un Site e-Commerce

**Projet de segmentation de clients pour un site e-commerce (OLIST)**  
Analyse comportementale et géographique des acheteurs afin d’identifier des profils types et d’adapter la stratégie marketing.

---

## 🎯 Objectif du projet  
L’objectif est de **segmenter les clients d’un site e-commerce brésilien** à partir de leurs comportements d’achat, de leur satisfaction et de leurs caractéristiques logistiques, afin de :
- mieux comprendre les différents profils de clients,  
- personnaliser les actions marketing,  
- et maintenir une segmentation évolutive dans le temps.

---

## 🧩 Contenu du projet  

Le dépôt contient :  

- **Notebooks Jupyter** regroupant :  
  1. **Préparation et Feature Engineering**  
     - Nettoyage et fusion des tables SQL : `customers`, `orders`, `order_items`, `products`, `sellers`, `order_reviews`, `geolocation`.  
     - Sélection de variables explicatives : `total_purchase`, `latest_purchase_numeric`, `average_score`, `total`.  
     - Variables descriptives : `latt`, `long`, `delay`, `delivery_time`, `shipping`.  
  2. **Analyses exploratoires**  
     - Distribution géographique des clients, comportement d’achat et score de satisfaction.  
  3. **Modélisation des clusters**  
     - Tests de modèles : **K-Means**, **Agglomerative Clustering**, **DBSCAN**.  
     - Évaluation via *Silhouette Score* et *Adjusted Rand Index (ARI)*.  
  4. **Analyse et interprétation des clusters**  
     - Description actionnable des segments (profils clients).  

- **Scripts SQL** utilisés pour extraire et transformer les données brutes.

- **Présentation PowerPoint** résumant les étapes du projet et les insights marketing associés.

---

## 🧠 Méthodologie  

1. **Préparation des données**  
   - Données issues de la base **OLIST (2016-09 → 2018-09)**  
   - 93 358 clients uniques, 99 441 opérations d’achat, 3 905 vendeurs.  
   - 97 % d’achats uniques, 75 % de livraisons anticipées.  

2. **Feature Engineering**  
   - Conversion des dates, agrégation par client, création de variables comportementales et monétaires.  

3. **Modélisation et comparaison**  
   - **K-Means** : 6 clusters retenus (Silhouette & ARI ≈ 0.93)  
   - **Agglomerative Clustering** : 5 clusters, bonne lisibilité mais moins flexible  
   - **DBSCAN** : robuste mais peu pertinent pour ce dataset  

4. **Clusterisation finale : K-Means**  
   - Simplicité, performance et scalabilité.  
   - Permet un recalcul régulier pour suivre les évolutions comportementales.  

---

## 📊 Résumé des segments (Clusters K-Means)

| Cluster | Profil | Description synthétique |
|----------|---------|--------------------------|
| 0 | 🆕 **Newcomers** | Nouveaux clients récents, peu d’achats mais bonne satisfaction. |
| 1 | 😠 **Déçus** | Clients peu satisfaits malgré plusieurs achats. |
| 2 | 🛒 **Serial-Shoppers** | Clients fidèles, satisfaction élevée, fréquence d’achat importante. |
| 3 | 😡 **Pas Contents** | Clients insatisfaits avec retards de livraison. |
| 4 | 🧾 **One-Shop** | Achat unique, pas de réachat identifié. |
| 5 | 🏬 **Grossistes** | Clients à très forte valeur monétaire et faible taux de livraison. |

---

## 🔄 Maintenance du modèle  

- **Resegmentation automatique** toutes les 6 semaines.  
- Suivi de la stabilité via le **ARI Score**.  
- Objectif : détecter les changements de comportement et adapter la stratégie marketing.

---

## 🛠️ Technologies utilisées  

- **Python** : Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn  
- **SQL** : extraction et jointure des tables (via scripts inclus)  
- **Clustering** : K-Means, Agglomerative, DBSCAN  
- **Évaluation** : Silhouette Score, Adjusted Rand Index  
- **Visualisation** : cartes géographiques, heatmaps, boxplots  

---

## 📂 Structure du dépôt  

```text
segmentation_clients
│
├── Notebooks/
│   ├── Feature_Engineering_and_Analysis.ipynb
│   ├── Clustering_Models_Comparison.ipynb
│   ├── Cluster_Description.ipynb
│
├── SQL/
│   └── queries.sql
│
├── Martineau_Alexandre_5_presentation_072024.pdf
└── README.md
```
