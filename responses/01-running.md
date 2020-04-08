Chèr.e {{ id }}, il est temps de faire de la programmation!

- [ ] Changer l'auteur du programme Python

```python
# -*- coding: utf-8 -*-
"""

@author: CollegeBoreal
"""
```

Modifier le programme Python avec l'éditeur de ton choix et changer l'auteur `CollegeBoreal` avec ton :id: Github

- [ ] Exécuter un programme Python

Voyons voir le programme Python, on peut y voir une fonction `main` qui contiendra toutes les instructions pour écrire le programme et une fonction `charge` servant à importer les données du fichier `b000000000.json`: Le format de fichier [json](https://www.json.org) (JavaScript Object Notation) permet le partage de données de façon légère (lightweight data-interchange format). C'est, pour les humains, un format plus facile à lire et écrire.

Tu remarqueras au passage que la fonction `charge` a besoin d'un code externe que l'on va récupérer grâce à l'import d'une librairie `import json`

```python
import json

def charge(fichier):
   with open(fichier) as f:
      return json.load(f)

def main():
  #print(charge('b000000000.json'))
```

En dessous de la fonction, on trouvera un `if` appellant cette fonction:

```python
if __name__== "__main__":
    main()
```

En faisant cela, la fonction `main` s'éxécutera dès que le programme Python est lancé.

Dans la fonction `main`, enlève le commentaire se trouvant sur la ligne:`#print(charge('b000000000.json'))`. Cela permettra d'imprimer le fichier à étudier. Il y a un `#` devant la ligne, qui veut dire que c'est un commentaire. Enlève le commentaire par le retrait du `#` permettant à Python de lire la ligne et sauveguarde le fichier.

- [ ] Fais tourner ton programme dans ton terminal

Pour éxécuter le programme Python taper `python b000000000.py` dans le terminal. Le programme Python doit se trouver dans le même répertoire ou l'on se trouve.

* Sous Powershell (Sous windows utilise le champ recherche de ta barre d'icône et tape `Anaconda Powershell` )

```
PS > python b000000000.py
```

* Sous ZSH (Sous :apple:)

```
% python b000000000.py
```


Après l'éxécution, sur ton terminal s'affichera les données du fichier `b000000000.json`. Nous ferons mieux dans quelques instants mais pour l'instant, il faut soumettre le code vers GitHub. 


- [ ] Soumettre les modifications

Pour chaque changement de fichiers dans ton référentiel, il faut  `ajouter` et `signer` le fichier qui te permet de formuler un message détailant ce que tu as changé. Ensuite tu peux `soumettre` une version mise à jour, en même temps que tes commentaires, vers GitHub. 

:round_pushpin: Faisons ces trois étapes:

1. Ajouter dans Git: `git add b000000000.py`
2. Signer dans Git: `git commit -m "Enlever le commentaire pour afficher le contenu du fichier"`
3. Soumettre à Git: `git push`
