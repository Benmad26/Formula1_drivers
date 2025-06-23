# Catalogue des Pilotes de F1

## Objets (avec leurs propriétés)

### 1. Personne (Pilote de F1)

Les propriétés d'une **personne** dans le contexte des pilotes de Formule 1 exploitées dans ce projet sont :

| Propriété              | Description                                                  |
|------------------------|--------------------------------------------------------------|
| **nom**                | Nom complet du pilote (ex. : Lewis Hamilton)                 |
| **date de naissance**  | Date de naissance (extraite de Wikidata)                     |
| **lieu de naissance**  | Ville/pays de naissance (utilisé dans les analyses spatiales)|
| **continent d’origine**| Dérivé du lieu (Europe, Asie, etc.), utilisé pour les comparaisons |
| **occupation**         | Fonction dans Wikidata (Pilote de F1, parfois multiple)      |

---

### 2. Organisation (Écurie de F1)

Les écuries, modélisées comme **organisations**, ont été analysées via leurs relations avec les pilotes :

| Propriété           | Description                                                |
|---------------------|------------------------------------------------------------|
| **nom**             | Nom officiel de l’écurie (ex. : Ferrari, McLaren)          |
| **type**            | Type d’organisation (ex. : racing team)                    |
| *(autres propriétés comme le siège ou la date de fondation n’ont pas été exploitées ici)* |

---

### 3. Lieu (Lieu de naissance)

Les **lieux** ont été utilisés uniquement pour les naissances, avec :

| Propriété                  | Description                          |
|----------------------------|--------------------------------------|
| **nom**                    | Nom de la ville ou du pays           |
| **type**                   | Ville, région ou pays                |
| **continent**              | Continent dérivé du lieu (ex. : Europe) |

---

## Relations entre objets

Les relations effectivement exploitées dans l’analyse sont les suivantes :

### 1. **Personne est née dans Lieu**
Relation utilisée pour cartographier la répartition spatiale des naissances.

### 2. **Personne est membre de Organisation**
Relation clé pour le graphe biparti pilote ↔ écurie.

### 3. **Organisation est liée à plusieurs personnes**
Chaque écurie est connectée à un ou plusieurs pilotes au cours du temps.

### 4. **Personne appartient à un continent / période**
Utilisé pour analyser les profils géoculturels dans le temps.

---





