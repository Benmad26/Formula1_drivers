# Catalogue des Pilotes de F1

## Objets (avec leurs propriétés)

### 1. Personne (Pilote de F1)

Les propriétés d'une **personne** dans le contexte des **pilotes de F1** pourraient être les suivantes :

| Propriété            | Description                                         |
|----------------------|-----------------------------------------------------|
| **nom**              | Nom complet du pilote                               |
| **date de naissance**| Date de naissance du pilote (ex. : 07-01-1985)      |
| **lieu de naissance**| Lieu de naissance du pilote (ex. : Stevenage, Royaume-Uni) |
| **origine**          | Nationalité (ex. : britannique)                     |
| **formation**        | Formation scolaire et/ou sportive (ex. : karting)   |
| **occupation**       | Occupation (ex. : Pilote de F1, ancien pilote, etc.)|
| **publications**     | Publications ou articles où le pilote est mentionné (si applicable) |

Exemple de données :

| nom                  | date de naissance | lieu de naissance  | origine      | formation        | occupation     | publications |
|----------------------|-------------------|--------------------|--------------|------------------|----------------|--------------|
| Lewis Hamilton       | 1985-01-07        | Stevenage, Royaume-Uni | Britannique  | Karting, Formule Renault | Pilote de F1  | Article XYZ |

---

### 2. Organisation (Écurie de F1)

Les écuries de F1 sont des **organisations** et auront des propriétés comme :

| Propriété           | Description                                         |
|---------------------|-----------------------------------------------------|
| **nom**             | Nom de l’écurie                                     |
| **type**            | Type de l’organisation (ex. : Écurie de F1)         |
| **siège**           | Lieu de siège de l’écurie (ex. : Brackley, Royaume-Uni) |
| **fondation**       | Année de fondation de l’écurie                      |

Exemple de données :

| nom          | type            | siège             | fondation |
|--------------|-----------------|-------------------|-----------|
| Mercedes     | Écurie de F1    | Brackley, Royaume-Uni | 1954      |
| Ferrari      | Écurie de F1    | Maranello, Italie | 1929      |

---

### 3. Lieu (Lieu de naissance et lieux de courses)

Les **lieux** peuvent représenter les lieux de naissance des pilotes et/ou les lieux des **circuits de F1**. Les propriétés peuvent être :

| Propriété             | Description                           |
|-----------------------|---------------------------------------|
| **nom**               | Nom du lieu (ex. : Stevenage)         |
| **type**              | Type de lieu (ex. : Ville, Circuit de F1) |
| **coordonnées géographiques** | Latitude et longitude du lieu      |

Exemple de données :

| nom          | type              | coordonnées géographiques       |
|--------------|-------------------|---------------------------------|
| Stevenage    | Ville             | 51.9025° N, 0.2042° W          |
| Circuit de Monaco | Circuit de F1 | 43.7333° N, 7.4167° E          |

---

### 4. Œuvre (Publications, rapports, ou livres)

Les **œuvres** dans ce cas pourraient inclure des **publications** sur les pilotes, leurs biographies, des rapports sur les saisons de F1, etc. Les propriétés seraient :

| Propriété                 | Description                               |
|---------------------------|-------------------------------------------|
| **référence bibliographique** | Titre du livre ou article               |
| **année de publication**  | Année où la publication a été réalisée   |
| **lieu de publication**   | Lieu où l'œuvre a été publiée (ex. : Londres) |

Exemple de données :

| référence bibliographique        | année de publication | lieu de publication |
|----------------------------------|----------------------|---------------------|
| "My Life in Formula 1"          | 2012                 | Londres             |
| "F1: The Auto Biography"        | 2018                 | New York            |

---

## Relations entre objets

Les **relations** entre ces objets sont essentielles pour montrer les connexions entre les pilotes, les écuries, les lieux, et les publications. Voici quelques exemples de relations qui pourraient être utilisées dans ton projet :

### 1. **Personne est née dans Lieu**
Chaque pilote a un **lieu de naissance**, et cette relation peut être exprimée comme suit :
- **Lewis Hamilton** est né à **Stevenage**.

### 2. **Personne est élève de Personne**
Si tu souhaites montrer des relations de mentorat ou d'apprentissage entre les pilotes, tu peux utiliser cette relation :
- **Lewis Hamilton** a été mentoré par **Fernando Alonso** (ou autre pilote).

### 3. **Personne est membre de Organisation**
Cette relation montre quel pilote est associé à quelle **écurie** :
- **Lewis Hamilton** est membre de l'**écurie Mercedes**.

### 4. **Œuvre a pour auteur Personne**
Si tu souhaites associer un pilote à une publication, tu peux établir une relation où un **pilote est l'auteur** d'une **œuvre** (par exemple une autobiographie) :
- **Lewis Hamilton** est l'auteur de **"My Life in Formula 1"**.

### 5. **Œuvre a lieu de publication**
Cette relation montre où une œuvre a été publiée :
- **"My Life in Formula 1"** a été publié à **Londres**.

---

## Exemple de relations entre objets

Voici un exemple avec quelques relations entre les objets :

- **Lewis Hamilton** est né à **Stevenage**.
- **Lewis Hamilton** a été membre de **Mercedes**.
- **Lewis Hamilton** est l'auteur de **"My Life in Formula 1"**, publié à **Londres**.
- **Mercedes** a été fondée en **1954** et a son siège à **Brackley, Royaume-Uni**.

