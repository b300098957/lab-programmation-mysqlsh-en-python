## Utilisation de Variables

Dans cette section, on va créer deux variables `session` et `db` que l'on utilisera à travers le cycle de vie de notre programme.

Sur ce, on va essayer de se connecter au  gestionnaire de base de données [SGBD](https://fr.wikipedia.org/wiki/Syst%C3%A8me_de_gestion_de_base_de_donn%C3%A9es). Plus précisément au `document store` **DS** du gestionnaire en important son Interface de Programmation [API](https://fr.wikipedia.org/wiki/Interface_de_programmation) par l'intermédiaire de la librairie `mysqlx` que l'on a déjà installé avec l'utilitaire Python `pip`.

Un `document store` permet le stockage de document de type `json`.

- [ ] Ajout de la librairie `mysqlx`. Juste aprés la fonction `charge`, rajoute le code suivant:

```python
import mysqlx
```

- [ ] Grace à la librairie, on peut maintenant se connecter à la base de données. On va créer notre variable `session` nous permettant d'obtenir une session d'entrée auprès de la base. On va se connecter à notre propre machine `localhost` avec l'identifiant de `root` créé précédemment. Juste après l'import rajoute:

```python
session = mysqlx.get_session({
    "host": "localhost",
    "port": 33060,
    "user": "root",
    "password": "password"
})
```



- [ ] Maintenant qu'on a l'accord du gestionnaire de base de données pour converser, on va se connecter à la base `world_x` grâce à la `session` et on va utiliser notre variable `db` pour guarder l'information de la base. Après la `session` rajoute:

```python
db = session.get_schema("world_x")
```

- [ ] Pour la fin de notre test de connexion, on va fermer le dialogue avec le gestionnaire de base de données en fermant la session. Toujours à la fin de la fonction `main`, juste après l'impression du chargement du fichier JSON `print(charge('b000000000.json'))` , rajoute le bloc:

:warning: Attention de bien respecter l'indentation requise par Python pour délimiter les blocks. Les espaces de l'indentation sont composés de trois espaces en général.

```python
  # Ne pas oublier de remercier le gestionnaire de BD
  session.close
```

La formation du bloc `main` est maintenant terminée

Maintenant fais tourner ton code et mets le *nombre* de la dernière valeur de `LifeExpectancy` de l'objet `JSON` que tu as trouvé dans le commentaire et faisons rouler ce tutoriel!
