{{ chefs }} :tada: :tada: :tada: 

C'est ce que l'on appelle un parcours sans faute.

## Tracer la visite d'une personne

Il nous reste maintenant à rajouter un bout de code servant à optimiser l'algorithme.

Pour éviter les cycles ou les etudiants seraient à proximité de plusieurs étudiants et que certains des étudiants auraient déjà répondu à la question posée. On remédiera à ce problème en tenant à jour une liste de personnes ayant répondus à la question ou ayant déjà été `visités`.

On tiendra une liste de personnes visitées en l'appellant `visitees`. On l'initialisera au préalable. Une liste vide peut s'écrire `list()` en Python mais aussi `[]` que l'on choisira car plus élégant . 

- [ ]   On placera ce code juste après l'appel de la fonction `search()`

```python
def search(name):
   visitees = []
```

- [ ]  Juste après la sortie de la queue `search_queue.popleft()`, on va tester si la `personne` n'a pas été visitée et on insère le block de code de la personne élue et si on ne sort pas de la condition on continue à chercher la proximité des autres étudiants

```python
      if not personne in visitees:
         if personne_elue(personne):
            ...
```

- [ ]  Enfin on termine le code en rajoutant la personne visitée dans la liste des visitées

```python
         ...
         search_queue += eleves[personne]
         visitees.append(personne)
```

:warning: Attention à respecter l'indentation quand on rajoute le code `if not personne in visitees:`. Tout le block qui suit doit être indenté de 3 espaces.

:bulb: Si tu as bien suivi le code, tu devrais trouver la fonction `search` comme ceci si tu tapes la commande `git diff` dans ton terminal

```python
 def search(name):
+   visitees = []
    search_queue = deque()
    search_queue += eleves[name]
-   print( len(eleves.values()) )
+   while search_queue:
+      personne = search_queue.popleft()
+      if not personne in visitees:
+         if personne_elue(personne):
+            print(personne + " a le fameux Mac")
+            return True
+         search_queue += eleves[personne]
+         visitees.append(personne)
    return False
```

:star:  `git diff` représente la différence entre le code en train d'ètre modifié et le code soumit sur GitHub

* Les lignes précédées d'un signe `+` sont les lignes ajoutées

* Les lignes précédées d'un signe `-` sont les lignes supprimées

- [ ]  Éxécute ton programme pour tester ton nouveau code


:tada: Sauveguarde de la base de données (dump)

```
$ docker container exec some-mysqlds \
                   mysqldump --user root --password=password world_x \
                   > ~/Developer/setrar/lab-programmation-mysqlsh-en-python/b000000000.sql
```

**Soumet ton code** vers GitHub pour continuer:
```
git add b000000000.py b000000000.sql
git commit -m "Tutoriel complété"
git push
```
