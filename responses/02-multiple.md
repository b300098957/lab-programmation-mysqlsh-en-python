Tu as entré {{ taille }} , j'ai trouvé `46.20000076293945` . Cela n'a pas trop d'importance pour l'instant, continuons!.

Dans cette section, on va `lire` le fichier `chargé` en mémoire dans le `Document Store`. Ce qui signifie que le fichier en format `JSON` sera lu et converti en format du `Document Store`. Ce fichier converti au format du gestionnaire de la base de données s'appelle un `Document`. Ce `Document` sera stoqué dans une `collection`. C'est l'équivalent d'une `table` dans le monde `SQL`. Dans notre cas, nous sommes dans le monde du `NoSQL`.

- [ ] Déclarer la fonction `lecture`

Cette fonction va créer une collection temporaire `temp` qui nous permettra de convertir le fichier `b000000000.json` en collection. Le résultat de cette collection aura pour effet d'utiliser pleinement les bénéfices d'un API comme X DevAPI. Celle de la manipulation des données en mémoire. La `collection` devient une `structure de données` permettant la manipulation de documents, comme la recherche `find`, l'ajout `add`. Finalement, nous ne guarderons pas la collection `temp` dans le `Document Store`. La fonction `lecture` servira donc a chargé le fichier `json` et présenter une `collection` en mémoire grace au retour de la fonction `lecture`.

Rajoute la fonction lecture juste après la déclaration de la variable `db`:

```python
def lecture(fichier):

  # Le nom de la collection temporaire
  nomColl = "temp"

  # Crée la collection temporaire maColl
  maColl = db.create_collection(nomColl)

  # charge le fichier dans la variable json
  json = charge(fichier)
    
  # Ajoute le contenu du fichier json dans la collection temporaire maColl
  maColl.add(json).execute()

  # Lis toute les documents convertis de la collection et les stocker dans la variable docs
  docs = maColl.find().execute()

  # Détruit la collection temporaire
  db.drop_collection(nomColl)

  # Retourne un dictionnaire Python du fichier json converti
  return docs
```

Nous avons donc la fonction `lecture` qui s'occupe de charger le fichier `json` dans une `collection` en mémoire que l'on peut manipuler

- [ ] Appelons la lecture

Maintenant il faut faire la lecture. Dans la fonction `main` remplace l'affichage du contenu du fichier `print(charge('b000000000.json'))` par le bloc ci-dessous en respectant l'indentation:

```python
  docs = lecture('b000000000.json')
  print(len(docs.fetch_all()))
```

- [ ] Fais tourner ton programme dans ton terminal

:warning: Mets le chiffre que le programme a imprimé dans le message de ta signature `commit` à la soumission de ton programme.

**Soumets ton code** vers GitHub pour continuer:
```
git add b000000000.py
git commit --message "La taille de la queue est <mon chiffre ICI>"
git push
```
