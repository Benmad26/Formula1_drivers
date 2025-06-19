
<!-- page1_distribution_temporelle.md -->

# Question 1 : Distribution des naissances dans le temps

## 1. Contexte et objectif  
Nous souhaitons analyser comment le nombre de naissances (issues de Wikidata) évolue au fil des années.  
**Enjeu** : repérer les périodes de pic et de creux, et comprendre d’éventuels phénomènes historiques.

## 2. Méthodologie de production  

1. **Source des données**  
   - Triplestore Wikidata  
   - Requête SPARQL pour récupérer count de naissances par année  

2. **Requête et chargement**  
   ```python
   from SPARQLWrapper import SPARQLWrapper, JSON
   import pandas as pd

   sparql = SPARQLWrapper("https://query.wikidata.org/sparql")
   sparql.setQuery("""
   SELECT ?year (COUNT(?birth) AS ?count) WHERE {
     ?birth wdt:P31 wd:Q5 .
     ?birth wdt:P569 ?date .
     BIND(YEAR(?date) AS ?year)
   }
   GROUP BY ?year
   ORDER BY ?year
   """)
   sparql.setReturnFormat(JSON)
   results = sparql.query().convert()["results"]["bindings"]
   df = pd.DataFrame([{"year": int(r["year"]["value"]), "count": int(r["count"]["value"])} for r in results])
