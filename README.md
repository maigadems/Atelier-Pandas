# Atelier-Pandas

Atelier Pandas – analyse et nettoyage de mesures de capteurs IoT (température, humidité, pression, consommation) avant transmission à un futur système de Machine Learning de détection d'anomalies.

## Contexte

Une entreprise possède plusieurs bâtiments (B001 à B004) équipés de capteurs IoT relevant régulièrement
température, humidité, pression, consommation énergétique et état (`OK`, `ALERTE`, `ERREUR`). Le jeu de
données brut (`data/mesures_capteurs.csv`, 605 mesures) contient volontairement des valeurs manquantes,
des doublons et quelques valeurs aberrantes, à traiter avant toute exploitation.

## Structure

```
atelier_pandas_iot/
├── data/mesures_capteurs.csv
├── notebooks/atelier_pandas_iot.ipynb
└── exports/
    ├── donnees_nettoyees.csv
    └── donnees_nettoyees.json
```

## Vue d'ensemble du travail

Le notebook `atelier_pandas_iot.ipynb` suit 13 parties, chacune correspondant à une étape de prise en
main de Pandas puis de préparation du jeu de données réel.

| # | Partie | Contenu |
|---|--------|---------|
| 1 | Series | Création de Series de températures, indexation par défaut puis par heures (12h–15h), accès à la 1ère/dernière valeur, de deux façons différentes de construire l'index. |
| 2 | DataFrame | Création d'un DataFrame `df_test` à la main depuis un dictionnaire, puis import du dataset réel `mesures_capteurs.csv` dans `df` (605 lignes × 9 colonnes). |
| 3 | Exploration | Premières/dernières lignes, dimensions, noms de colonnes, `info()` et `describe()` pour un premier diagnostic du jeu de données. |
| 4 | Sélection | Sélection de colonnes simples et multiples, puis sélection de lignes/colonnes avec `loc` et `iloc`. |
| 5 | Manipulation des colonnes | Ajout d'une colonne `temperature_fahrenheit` (calculée puis supprimée), ajout de `niveau_temperature` (Élevée/Normale via `np.where`), renommage de `humidite` en `humidite_relative`. |
| 6 | Filtrage | Isolation des mesures à température > 30°C, puis combinées à une humidité > 70%. |
| 7 | Tri | Tris croissant/décroissant par température (`df_trie1`, `df_trie2`), top 10 des températures les plus élevées, tri combiné bâtiment/température. |
| 8 | Analyse | Agrégations par bâtiment (`groupby`) : consommation moyenne, statistiques de température (min/max/moyenne/écart-type), bâtiment le plus consommateur, nombre d'alertes par bâtiment. |
| 9 | Valeurs manquantes | Diagnostic (nombre, taux, lignes concernées), puis imputation : moyenne pour température/humidité, médiane pour la consommation, `"INCONNU"` pour l'état. |
| 10 | Doublons | Détection (5 doublons trouvés), affichage puis suppression avec vérification. |
| 11 | Statistiques descriptives | Statistiques complètes de la température (min, max, moyenne, médiane, écart-type, count), mode et répartition des états (OK/ALERTE/ERREUR). |
| 12 | Exportation | Export du DataFrame nettoyé vers `exports/donnees_nettoyees.csv` et `exports/donnees_nettoyees.json`. |
| 13 | Bonus | Ajout d'une colonne `anomalie` : repère les mesures de température ou de consommation s'écartant de plus de 2 écarts-types de la moyenne, en anticipation du futur système ML de détection d'anomalies. Ré-export des données incluant cette colonne. |

## Progression

- [x] Partie 1 – Series
- [x] Partie 2 – DataFrame
- [x] Partie 3 – Exploration
- [x] Partie 4 – Sélection
- [x] Partie 5 – Manipulation des colonnes
- [x] Partie 6 – Filtrage
- [x] Partie 7 – Tri
- [x] Partie 8 – Analyse
- [x] Partie 9 – Gestion des valeurs manquantes
- [x] Partie 10 – Gestion des doublons
- [x] Partie 11 – Statistiques descriptives
- [x] Partie 12 – Exportation
- [x] Partie 13 – Bonus
