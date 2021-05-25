# Environnements de développement

Vscan dispose de trois environnements de développement créer dans docker dans trois version différentes.

Les 3 versions actuellement supportées sont : 

* Ubuntu 20.04
* Centos 7
* Centos 8

Debian arrivera prochainement comme OpenSuse.

Pour créer l'environnement de développement il vous suffis de cloner le dépot gitlab de vscan et de lancer le script suivant : 

```bash 
./start-dev-env 
```
Les options vous serrons indiquées : 

```
centos:8             Create and start Centos 8 vscan dev environnement.
centos:8:release	Create and start release Centos 8 release.
centos:7             Create and start Centos 7 vscan dev environnement.
centos:7:release     Create and start release Centos 7 release.
ubuntu:18.04         Create and start Ubuntu 18.04 vscan dev environnement (DEPRECATED)
ubuntu:20.04         Create and start Ubuntu 20.04 vscan dev environnement
```

Vous arriverez donc dans un conteneur avec vscan installé, une interface web pour mysql ([sidu](https://sourceforge.net/projects/sidu/)) accessible via votre navigateur web a cette adresse : http://127.0.0.1:8080 .

 