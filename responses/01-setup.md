  Bienvenue dans ce laboratoire qui te guidera à écrire un programme dans le language [Python](https://www.python.org). Le programme se concentrera sur l'écriture d'un programme Python accédant une base de donnée [MySQL](https://www.mysql.com/) et cela par son protocole X DevAPI permettant l'accès au [Document Store](https://www.mysql.com/products/enterprise/document_store.html) de la base de données. Avant de commencer, nous allons nous assurer que l'environnement de développement est prêt. 
  
Courage, ce n'est qu'en `dix` étapes

## :a: Installer Python 

:zero: Présence de Python

Ouvrir un terminal et vérifier la version de Python avec la commande suivante

```
% python --version
```

Si Python est installé, le résultat de la commande donnera une version. Cette version doit être superieure à `3.x.x`

:one: installer Python avec un `Package manager`

Si Python n'est pas installé, utiliser un gestionnaire de librairies.

:computer: Windows avec [choco](https://chocolatey.org/install)

```
PS > choco install anaconda3
```

:apple: MacOS avec [HomeBrew](https://docs.brew.sh/Installation)

```
% brew cask install anaconda 
% echo 'export PATH="/usr/local/anaconda3/bin:$PATH"' >> ~/.zshrc 
```

:warning: Ce laboratoire n'utilise pas Python **2**

## :b: Installer [Git](https://git-scm.com/downloads)

:two: Présence de Git

Ouvrir un terminal et vérifier la version de Git avec la commande suivante

```
% git --version
```

Si le résultat donne un numéro de version. C'est parfait sinon

:three: installer Git avec un `Package manager`

Si Git n'est pas installé, utiliser un gestionnaire de librairies.

:computer: Windows avec [choco](https://chocolatey.org/install)

```
PS > choco install git.install
```

:apple: MacOS avec [HomeBrew](https://docs.brew.sh/Installation)

```
% brew install git
```

## :ab: Installer [Docker Desktop](https://www.docker.com/products/docker-desktop)

`Docker Desktop` permet l'installation de la base de données MySQL 8.0 avec beaucoup de facilité.

:four: Présence de Docker

Ouvrir un terminal et vérifier la version de Git avec la commande suivante

```
% docker --version
```

Si le résultat donne un numéro de version. C'est parfait sinon

:five: installer `Docker Desktop` avec un `Package manager`

:computer: Windows avec [choco](https://chocolatey.org/install)

```
PS > choco install docker-desktop -y
```

:apple: MacOS avec [HomeBrew](https://docs.brew.sh/Installation)

```
% brew cask install docker
```

## :o: Installer [MySQL Server](https://hub.docker.com/r/mysql/mysql-server/)

On est plus très loin, il nouis reste à installer la base de donnée.

:six: Créer le conteneur `some-mysqlds`

:pushpin: sous Powershell

```
PS> docker container run `
         --name some-mysqlds `
         --env MYSQL_ROOT_PASSWORD=password `
         --publish 3306:3306 `
         --publish 33060:33060 `
         --detach `
         mysql/mysql-server:latest
```

:pushpin: sous Bash

```
$ docker container run \
         --name some-mysqlds \
         --env MYSQL_ROOT_PASSWORD=password \
         --publish 3306:3306 \
         --publish 33060:33060 \
         --detach \
         mysql/mysql-server:latest
```

:seven: Créer la base de données `world_x`

:pushpin: sous PowerShell

```
PS > docker container exec --interactive some-mysqlds mysql `
                        --user root --password=password `
                        --execute "CREATE DATABASE world_x;"
```

:pushpin: sous Bash

```
$ docker container exec --interactive some-mysqlds mysql \
                        --user root --password=password \
                        --execute "CREATE DATABASE world_x;"
```

:bulb: Jusqu'ici tu auras pu constater que PowerShell et bash utilise deux séparateurs différents pour continuer une instruction sur la ligne suivant pour plus de clareté. PowerShell utilise le `backtick` ``` et bash utilise le `backslash` \  . Pour simplifier l'écriture on utilisera PowerShell en convention dans ce laboratoire avec le prompt `PS >`

:eight: Créer l'utilisateur `root` sous le sous-réseau déterminé par le pont [Bridge](https://docs.docker.com/network/network-tutorial-standalone/) du conteneur Docker

Nous allons tricher un peu pour faciliter la connection en se donnant l'adresse IP de la passerelle du Pont.

Créons notre utilisateur spécial `'root'@'172.17.0.1'`

```
PS > docker container exec --interactive some-mysqlds `
                mysql --user root --password=password `
                --execute "CREATE USER 'root'@'172.17.0.1' IDENTIFIED BY 'password';"
```

Et donnons lui tous les droits d'accès à n'importe quelle base de données

```
PS > docker container exec --interactive some-mysqlds `
                mysql --user root --password=password `
                --execute "GRANT ALL ON *.* TO 'root'@'172.17.0.1';"
```

## :eight_pointed_black_star: [X DevAPI](https://dev.mysql.com/doc/x-devapi-userguide/en/) en Python

Finalement installons la librairie nous permettant d'accéder à la base de données sous Python. Utilisons l'utilitaire Python permettant l'installation de librairie `Package Manager` [pip](https://pypi.org/project/pip/)

:nine: [Installer MySQL Connector Python avec pip](https://dev.mysql.com/doc/dev/connector-python/8.0/installation.html#installing-connector-python-with-pip)

```
PS > pip install mysql-connector-python
```
:round_pushpin: Vérifier l'installaiton du connecteur MySQL en imprimant sa version qui doit être de 8.x.x 

```
PS > pip show mysql-connector-python 
```

## :100: Cloner le référentiel

Maintenant que nous avons tout, nous pouvons cloner le référentiel contenant le bloc d'assemblage du code que tu vas écrire. Dans un terminal tapes `git clone {{ repoUrl }}`, la version `SSH` est également recommandée

Dans le référentiel, il y a deux fichiers:

- `README.md`: un fichier `markdown` donnant des informations sur le laboratoire
- `b000000000.py`: un fichier Python contenant le code à construire
- `b000000000.json`: un fichier `json` contenant des données à charger

Maintenant que tout est en place, nous pouvons commencer.

Laisses un commentaire avec ton *:id:* github pour continuer.
