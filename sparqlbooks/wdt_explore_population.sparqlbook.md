## Explore Wikidata

In this notebook, we refine and document the main requests available on the page [Exploration of Wikidata](../documentation/wikidata/Wikidata-exploration.md) 


When you prepare the queries, you can execute them on the Wikidata SPARQL endpoint, and then document and execute them in this notebook.

Analyse des nationalités
```sparql
## Analyse quantitative par pays
SELECT ?paysLabel (COUNT(?pilote) AS ?nbPilotes) WHERE {
  ?pilote wdt:P106 wd:Q10841764. # Métier : pilote de F1
  ?pilote wdt:P27 ?pays.         # Nationalité
  SERVICE wikibase:label { bd:serviceParam wikibase:language "fr". }
}
GROUP BY ?paysLabel
ORDER BY DESC(?nbPilotes)


```
Analyse des dynasties 

```sparql
## Dynasties des pilotes
SELECT DISTINCT ?famille ?familleLabel ?membreLabel WHERE {
  ?membre wdt:P106 wd:Q10841764.
  ?membre (wdt:P3373|wdt:P40|^wdt:P40) ?famille.
  ?famille wdt:P106 wd:Q10841764.
  FILTER(?famille != ?membre)
  SERVICE wikibase:label { bd:serviceParam wikibase:language "fr". }
}
ORDER BY ?familleLabel
```
```sparql
SELECT ?ecurieLabel (COUNT(?gp) AS ?nbVictoires) WHERE {
  ?gp wdt:P1346 ?pilote.   # Gagnant d'un GP
  ?pilote wdt:P108 ?ecurie. # Employé par une écurie

  SERVICE wikibase:label { bd:serviceParam wikibase:language "fr". }
}
GROUP BY ?ecurieLabel
ORDER BY DESC(?nbVictoires)
```


Explore 

```sparql
   ## Count and inspect occupations and fields of work
   SELECT (COUNT(*) as ?eff)
    WHERE {
        ?item wdt:P31 wd:Q5;  # Any instance of a human.

            wdt:P106 wd:Q10841764. # Métier : pilote de F1
        
            # wdt:P101 wd:Q333  # astronomy 2161
            # wdt:P106 wd:Q169470 # physicist 32123
            #  wdt:P101 wd:Q413 # physics ~ 4000
            #  wdt:P106 wd:Q155647  # astrologer 1364
            #  wdt:P101 wd:Q34362 # astrology 241
            #  wdt:P106 wd:Q170790  # mathematician 39562
            #  wdt:P106 wd:Q901 # scientist 36117

    }  
    #LIMIT 10

```

```sparql
### Modern astronomers : born from 1971 onward
SELECT (count(*) as ?number)
WHERE {
    ?item wdt:P106 wd:Q10841764;  # Profession : pilote de F1
          wdt:P31 wd:Q5;        # Humain
          wdt:P569 ?birthDate.  # Date de naissance

    BIND(REPLACE(str(?birthDate), "(.*)([0-9]{4})(.*)", "$2") AS ?year)
    FILTER(xsd:integer(?year) > 1970)
}

```

```sparql
### Recents F+ drivers
SELECT (count(*) as ?number)
WHERE {
  ?item wdt:P106 wd:Q10841764;   # Profession : pilote automobile
        wdt:P31 wd:Q5;           # Instance de : humain
        wdt:P569 ?birthDate.     # Avec une date de naissance

  BIND(REPLACE(str(?birthDate), "(.*)([0-9]{4})(.*)", "$2") AS ?year)
  FILTER(xsd:integer(?year) > 1970 && xsd:integer(?year) < 2006)
}

```
### Count how many properties are available for the considered population

Execute this query **directly on the Wikidata sparql-endpoint** and save the result to a CSV document that you will store in your project: [population properties list](../Wikidata/properties_20250309.csv)


Open your CSV file with a spreadsheet editor:
* Inspect the content of the results and look for relevant properties with regard to your research questions
* Observe all the links to other semantic web repositories, probably the sources of this information.
* You can transform this file to your preferred spreadsheet editor format (Calc, Excel, etc.) and take notes row per row in the spreadsheet.


```sparql
PREFIX wdt: <http://www.wikidata.org/prop/direct/>
PREFIX wd: <http://www.wikidata.org/entity/>
PREFIX wikibase: <http://wikiba.se/ontology#>
PREFIX bd: <http://www.bigdata.com/rdf#>

SELECT ?p ?propLabel ?eff
WHERE {
  {
    SELECT ?p (COUNT(*) AS ?eff)
    WHERE {
      {?item wdt:P106 wd:Q169643}   # Profession = Pilote de F1
      UNION
      {?item wdt:P106 wd:Q10841764}  # Profession = Pilote automobile (si tu veux inclure les pilotes génériques)

      ?item wdt:P31 wd:Q5;           # Instance de : humain
            wdt:P569 ?birthDate.    # Date de naissance

      ?item ?p ?o.                   # Trouver toutes les propriétés associées

      BIND(REPLACE(str(?birthDate), "(.*)([0-9]{4})(.*)", "$2") AS ?year)
      FILTER(xsd:integer(?year) > 1949 && xsd:integer(?year) < 2006)  # Nés après 1950, avant 2006
    }
    GROUP BY ?p
  }

  # Obtenir le label de la propriété
  ?prop wikibase:directClaim ?p.

  SERVICE wikibase:label { bd:serviceParam wikibase:language "en". }
}

ORDER BY DESC(?eff)
# LIMIT 20

```
