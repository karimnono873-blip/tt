# TP N°2 : Clustering avec K-Means - Maintenance Prédictive 🏭

[![Algorithme](https://img.shields.io/badge/Algorithme-K--Means-00f2ff.svg)](#)
[![Thème](https://img.shields.io/badge/Thème-Astronomic_Violet_Blue-8a2be2.svg)](#)
[![Langage](https://img.shields.io/badge/Langage-Python-3776ab.svg)](#)

## 📌 Présentation du Projet

Ce projet s'inscrit dans le cadre du module d'Intelligence Artificielle et explore l'**apprentissage non-supervisé**. L'objectif est d'analyser le dataset industriel **AI4I 2020** pour découvrir des profils de fonctionnement de machines (clusters) sans utiliser d'étiquettes de pannes préalables.

Le rendu est un **compte rendu interactif monolithique (HTML/CSS/JS)** au design "Astronomic Violet Blue", intégrant la théorie, le code complet et des visualisations dynamiques.

### 👥 Équipe de Réalisation
* **Auteurs :** Dahane Ahmed Lamine & Tabbi Meriem
* **Enseignante :** Mme. Fergani
* **Module :** Intelligence Artificielle / Analyse de Données

---

## 🧠 Notions Fondamentales

### L'Algorithme K-Means
Le K-Means est un algorithme de partitionnement qui divise les données en *K* groupes homogènes en minimisant la distance entre les points et le centre de leur groupe (centroïde).
* **Initialisation :** Placement aléatoire de *K* centroïdes.
* **Assignation (Distance Euclidienne) :** Chaque point est assigné au centroïde le plus proche.
* **Mise à jour :** Les centroïdes sont recalculés comme la moyenne des points de leur cluster.
* **Convergence :** Répétition jusqu'à stabilisation des centroïdes.

### Avantages et Limites
* **Avantages :** Simple, très rapide et scalable pour de grands jeux de données industrielles.
* **Limites :** Nécessite de définir *K* à l'avance, très sensible aux valeurs aberrantes (outliers) et aux différences d'échelle entre les variables.

---

## 📊 Analyse des Données (Dataset)

Le projet utilise le dataset **AI4I 2020 Predictive Maintenance** (10 000 enregistrements) :
* **Variables conservées (Features physiques) :** `Air temperature [K]`, `Process temperature [K]`, `Rotational speed [rpm]`, `Torque [Nm]`, `Tool wear [min]`.
* **Pré-traitement strict (Non-Supervisé) :** * Suppression des identifiants (`UDI`, `Product ID`) et de la catégorie (`Type`).
    * **Suppression absolue de toutes les cibles** (`Machine failure` et les types de pannes spécifiques : `TWF`, `HDF`, etc.) pour forcer l'algorithme à trouver la structure par lui-même.
* **Normalisation Obligatoire :** Utilisation de `StandardScaler` (moyenne = 0, variance = 1) pour éviter que des variables aux échelles élevées (comme la vitesse en milliers de RPM) ne dominent le calcul de la distance.

---

## 📈 Évaluation et Métriques (Non-Supervisé)

Contrairement à la classification (TP1), il n'y a pas de Matrice de Confusion ni de Précision. L'évaluation repose sur la géométrie des clusters :
1.  **Inertie (WCSS - Within-Cluster Sum of Squares) :** Mesure la compacité des clusters. Plus elle est faible, plus les points sont proches de leur centroïde.
2.  **Méthode du Coude (Elbow Method) :** Technique visuelle traçant l'Inertie en fonction de *K* pour trouver le nombre optimal de clusters.
3.  **Score de Silhouette :** (Optionnel dans le code mais utile) Évalue la séparation entre les clusters (-1 = mauvais, 1 = parfait).

---

## 🚀 Utilisation

1.  **Installation :** Clonez le dépôt et assurez-vous d'avoir le fichier `ai4i2020.csv` dans le même dossier.
2.  **Exécution Web :** Ouvrez simplement le fichier `tp2_kmeans_maintenance.html` dans n'importe quel navigateur web moderne.
3.  **Visualisations :** Le rapport inclut des graphiques interactifs (Plotly.js) pour visualiser la **Méthode du Coude** et la **Segmentation des Machines (Vitesse vs Couple)**.

---

## 📝 Conclusion Métier

L'application du K-Means a permis d'isoler des profils distincts de fonctionnement (ex: machines à haute vitesse, machines sous forte charge/couple). Dans un contexte d'Industrie 4.0, ces clusters permettent d'attribuer des plans de maintenance prédictive spécifiques à chaque groupe de machines sans intervention humaine préalable.

---
*Projet universitaire - 2026*
