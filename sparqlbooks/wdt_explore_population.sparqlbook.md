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

