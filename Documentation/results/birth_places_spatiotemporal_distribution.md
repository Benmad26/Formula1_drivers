
---

```markdown
<!-- page2_distribution_continents.md -->

# Question 2 : Répartition des naissances par continent

## 1. Contexte et objectif  
Comment se distribuent géographiquement les naissances selon les grands continents ?  
**Enjeu** : visualiser les régions sous-/sur-représentées.

## 2. Méthodologie de production  

1. **Source et jointure géographique**  
   - Triplestore Wikidata pour pays + contiennent la propriété „continent”  
   - Fichier GeoJSON des contours continents (ou données internes)

2. **Requête SPARQL et chargement**  
   ```python
   # Même principe que précédemment, avec continent en plus
   sparql.setQuery("""
   SELECT ?continentLabel (COUNT(?birth) AS ?count) WHERE {
     ?birth wdt:P31 wd:Q5;
            wdt:P19/wdt:P17 ?country.
     ?country wdt:P30 ?continent.
     SERVICE wikibase:label { bd:serviceParam wikibase:language "fr". }
   }
   GROUP BY ?continentLabel
   """)
   results = sparql.query().convert()["results"]["bindings"]
   df2 = pd.DataFrame([{"continent": r["continentLabel"]["value"], "count": int(r["count"]["value"])} for r in results])

