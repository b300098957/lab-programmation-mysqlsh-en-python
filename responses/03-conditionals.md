Continuons maintenant dans la manipulation des documents stockés dans la collection retournée par la fonction `lecture`.

Pour naviguer dans la collection, on manipule des enregistrements `data items` et l'instruction les manipulant est `fetch`. `fetch` se décline en deux configurations:

* par la récupération entière (d'un coup) des documents [fetch_all](https://dev.mysql.com/doc/x-devapi-userguide/en/fetching-all-data-items-at-once.html)

* par la récupération individuelle [fetch_one](https://dev.mysql.com/doc/x-devapi-userguide/en/working-with-data-sets.html)

```python
  for doc in docs.fetch_all():
    for country in doc.countries:
```

Le code ci-dessus décrit une boucle `for` consommant tous `fetch_all` les documents `docs`, récupérés de la lecture. Du document `doc` extrait, on va lire le document `countries`. Un document `json` est délimité par des `{` et `}` et composé de `key: value`. Par exemple, le contenu du fichier `b000000000.json` : 

```json
{
  "countries": [
    {
      "GNP": 116729,
      "_id": "ZAF",
      "Name": "South Africa",
      "IndepYear": 1910,
      "geography": {
        "Region": "Southern Africa",
        "Continent": "Africa",
        "SurfaceArea": 1221037
      },
      "government": {
        "HeadOfState": "Thabo Mbeki",
        "GovernmentForm": "Republic"
      },
      "demographics": {
        "Population": 40377000,
        "LifeExpectancy": 51.099998474121094
      }
    },
    {
      "GNP": 3459,
      "_id": "HTI",
      "Name": "Haiti",
      "IndepYear": 1804,
      "geography": {
        "Region": "Caribbean",
        "Continent": "North America",
        "SurfaceArea": 27750
      },
      "government": {
        "HeadOfState": "Jean-Bertrand Aristide",
        "GovernmentForm": "Republic"
      },
      "demographics": {
        "Population": 8222000,
        "LifeExpectancy": 49.20000076293945
      }
    }
  ]
}
```

Pour récupérer les documents de la base de données, on utilise la fonction `find` de la collection. `find` ramène des ensembles de données `data set` dont on manipulera les `data items` avec `fetch`. Ce sont deux notions différentes marchant de pair.

On va tenter de créer une fonction `former_des_chefs()` qui prendra des documents d'une collection et extraira uniquement les chefs de gouvernements. On créera au passage une collection `chefs_de_gouvernement` que nous pourrons sauveguarder dans la base de données ultérieurement et au passage récupérer le résultat finale `data set` et le stocker dans une variable `docs` en mémoire et la retourner de la fonction. 

- [ ] Le code de notre fonction `former_des_chefs()` devrait ressembler à ceci, place le tout de suite après la fonction `lecture`:

```python
def former_des_chefs(docs):

  # Crée une nouvelle collection 'chefs_de_gouvernement'
  nomColl = 'chefs_de_gouvernement'
  maColl = db.create_collection(nomColl)

  # Manipuler la collection et la rajouter à la nouvelle
  for doc in docs.fetch_all():
    for country in doc.countries:
      # Insert des documents JSON de type government
      maColl.add(country['government']).execute()

  # Trouver tous les documents JSON et les mettre en mémoire
  docs = maColl.find().execute()

  # Détruit la collection
  db.drop_collection(nomColl)

  return docs
```

- [ ] Placer la fonction `former_des_chefs()`:

remplace la fonction `main` par le code suivant:

```python
def main():
  docs = lecture('b000000000.json')
  chefs = former_des_chefs(docs)
  print(len(chefs.fetch_all()))
  # Ne pas oublier de remercier le gestionnaire de BD
  session.close
```

- [ ] Exécute ton code et ajoute en commentaire l'impression que tu as obtenu. On passera ensuite au code suivant.
