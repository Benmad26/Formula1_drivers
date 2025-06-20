
<!-- page1_distribution_temporelle.md -->

# Question 1 : Distribution des naissances dans le temps

## 1. Contexte et objectif  
Nous souhaitons analyser l’évolution annuelle du nombre de naissances issues de Wikidata.  
**Enjeu** : identifier pics, creux et périodes charnières (guerres, baby-boom, etc.).

## 2. Méthodologie de production  
- **Extraction des données** : exécuter les cellules 2 à 5 du notebook `wdt_distribution_naissances_triplestore.ipynb` (requête SPARQL et chargement dans un DataFrame).  
- **Nettoyage et filtrage** : exécuter les cellules 6 à 8 (filtre années 1800–2020, tri).  
- **Organisation** : format “année / effectif” prêt à tracer.

## 3. Graphique principal  
![Répartition des naissances par genre et décennie](../../Notebooks_jupyther/wikidata_exploration/images/distrib_naissance.png)




## 4. Interprétation  
- **Pic majeur** : autour de 1946–1964 (baby-boom).  
- **Creux** : périodes de guerre (1914–1918, 1939–1945).  
- **Tendance générale** : croissance nette après 1950, plateau depuis les années 2000.

---

<!-- page2_distribution_continents.md -->

# Question 2 : Répartition des naissances par continent

## 1. Contexte et objectif  
Objectif : visualiser la distribution géographique des naissances selon les continents.  
**Enjeu** : repérer les disparités (population vs. couverture Wikidata).

## 2. Méthodologie de production  
- **Requête et extraction** : exécuter les cellules 3 à 6 du notebook `wdt_distribution_continents_triplestore.ipynb` (récupération des effectifs par continent).  
- **Jointure géospatiale** : exécuter les cellules 7 à 9 (chargement du GeoJSON et fusion avec les comptes).  
- **Préparation** : DataFrame “continent / effectif” et GeoDataFrame prêt à tracer.

## 3. Graphiques  

### 3.1 Distribution des naissances par génération et continent
![Distribution par génération et continent](../../Notebooks_jupyther/wikidata_exploration/images/Distributiondesnaissancespargénérationetcontinent.jpg)





## 4. Interprétation  
- **Continent dominant** : Europe.  
- **Écarts relatifs** : Afrique sous-représentée (biais de couverture).  
- **Facteurs** : population, priorité éditoriale de Wikidata.

---


<!-- page3_spatio_temporelle.md -->

# Question 3 : Évolution spatio-temporelle des naissances

## 1. Contexte et objectif  
Étudier comment la part de chaque continent évolue au fil des années.  
**Enjeu** : voir les dynamiques relatives (rattrapage, convergence/divergence).

## 2. Méthodologie de production  
- **Extraction conjointe** : exécuter les cellules 4 à 8 de `wdt_distribution_naissances_triplestore.ipynb` modifiées pour inclure le continent.  
- **Pivot temporel** : exécuter la cellule 9 pour obtenir une table “année × continent”.  
- **Préparation des small multiples** : cellules 10 à 12 pour tracer un graphique par continent (ou créer une animation).

## 3. Illustrations  

![Heatmap](../../Notebooks_jupyther/wikidata_exploration/images/heatmap.jpg)

## 4. Interprétation  
- **Points de bascule** : années où l’Afrique dépasse l’Europe (ex. 1980).  
- **Trajectoires** : croissance plus rapide en Asie et Afrique 1950–2000.  
- **Limites** : biais de complétude, décalage d’enregistrement.

---
# Question 4 : Types d'organisations associées aux pilotes de F1 selon les périodes

## 1. Contexte et objectif

Analyser l'évolution des types d’organisations (employeurs, équipes, sponsors) associées aux pilotes de Formule 1 selon les périodes historiques.

**Enjeu** : comprendre la professionnalisation du sport automobile et l'évolution de ses acteurs institutionnels.

## 2. Méthodologie de production

- **Données** : issue de Wikidata via SPARQL, extraction des entités liées aux pilotes.
- **Regroupement temporel** : les périodes ont été regroupées en grands intervalles (1881–1910, 1911–1940, etc.).
- **Classification** : typologie des organisations ("racing team", "company or gov. agency", etc.).
- **Analyse** : tableau de contingence croisée, test du chi², puis visualisation des résidus standardisés via une heatmap.

## 3. Illustration

# Question 4 : Types d'organisations associées aux pilotes de F1 selon les périodes

## 1. Contexte et objectif

Analyser l'évolution des types d’organisations (employeurs, équipes, sponsors) associées aux pilotes de Formule 1 selon les périodes historiques.

**Enjeu** : comprendre la professionnalisation du sport automobile et l'évolution de ses acteurs institutionnels.

## 2. Méthodologie de production

- **Données** : issue de Wikidata via SPARQL, extraction des entités liées aux pilotes.
- **Regroupement temporel** : les périodes ont été regroupées en grands intervalles (1881–1910, 1911–1940, etc.).
- **Classification** : typologie des organisations ("racing team", "company or gov. agency", etc.).
- **Analyse** : tableau de contingence croisée, test du chi², puis visualisation des résidus standardisés via une heatmap.

## 3. Illustration

# Question 4 : Types d'organisations associées aux pilotes de F1 selon les périodes

## 1. Contexte et objectif

Analyser l'évolution des types d’organisations (employeurs, équipes, sponsors) associées aux pilotes de Formule 1 selon les périodes historiques.

**Enjeu** : comprendre la professionnalisation du sport automobile et l'évolution de ses acteurs institutionnels.

## 2. Méthodologie de production

- **Données** : issue de Wikidata via SPARQL, extraction des entités liées aux pilotes.
- **Regroupement temporel** : les périodes ont été regroupées en grands intervalles (1881–1910, 1911–1940, etc.).
- **Classification** : typologie des organisations ("racing team", "company or gov. agency", etc.).
- **Analyse** : tableau de contingence croisée, test du chi², puis visualisation des résidus standardisés via une heatmap.

## 3. Illustration

![Heatmap](../../Notebooks_jupyther/wikidata_exploration/images/Chi2_plot.png)

## 4. Interprétation

Cette carte de chaleur montre l'écart à l'indépendance statistique entre types d'organisations et périodes historiques (résidus du test du chi²).

### Période 1881–1910 :
- Forte **surreprésentation** de "company or gov. agency" et de "not classified organisation".
- 🧐 Hypothèse : à cette époque, les courses automobiles étaient principalement organisées par des industriels, clubs ou entités d'État. Les écuries n'étaient pas encore structurées.

### 1911–1970 :
- Légère **sous-représentation** des entreprises/gouvernements.
- Montée progressive des "racing teams".
- 💡 Apparition d'équipes semi-professionnelles, mais hétérogénéité importante.

### 1971–2000 :
- Réduction des écarts : les catégories se rapprochent de l’indépendance.
- Légère reprise des "not classified organisations".
- 🤔 Peut révéler la présence d'entités non nommées ou de sponsors peu documentés.

### Bilan
- Le graphique illustre la **professionnalisation progressive** de la F1.
- Le rôle dominant des "racing teams" s’affirme après 1940, avec un déclin des entités non classifiées.
- Les premières décennies sont marquées par une organisation plus institutionnelle ou artisanale.

## 5. Limites

- Certains résultats peuvent être biaisés par la complétude variable des données Wikidata.
- La catégorisation "not classified" peut masquer une grande variété de cas réels.


