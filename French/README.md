# Vscan Documentation 

## Introduction

Vscan est une suite de logiciels de sécurité, open source développé principalement en python 3 compatible 3.8 et supérieur.
Il est diffusé sous licence GPLv3
Celui-ci s'appuie sur une base de donnée SQL et possède de nombreuses configurations et usages possibles.

## Présentation 

Vscan a pour mission de répondre a plusieurs besoins plus ou moins spécifique. Il est conçu pour donner une certaine souplesse a son utilisation et être multi-plateforme.
Il peut être utilisé de façon préventive, passive, ou être un élément de sécurité actif.

## Composition 

Vscan se compose de quatre grand logiciel distincts : 
1. Le serveur de backend
2. Le serveur API 
3. L'agent 

### Le serveur de backend
Le serveur de backend contient le moteur de vscan.
Ce moteur a diverses fonctionnalités possibles détaillées dans la page "Fonctions" de cette documentation.

Il a les rôles suivants : 

* Interaction avec la base de donnée.
* Gestion des dictionnaires de références CPE ([voir ce lien](https://www.cert-ist.com/public/fr/SO_detail?code=CPE))
* Gestion des remontées de failles logiciel, système d'exploitation ou encore matériels ([voir ce lien](https://fr.wikipedia.org/wiki/Common_Vulnerabilities_and_Exposures))
* Faire la correspondance entre CVE et CPE pour avoir une base de donnée lisible.
* Remonté des alertes de sécurité a la publication d'une faille de sécurité.


### Le serveur API

Le serveur api est un composant optionnel, il n'est pas installé par défaut lors d'une installation de vscan via un paquet rpm.

En effet vous n'êtes pas obligé de mettre en place le serveur api lors d'une utilisation de vscan en mode passif/passif (voir ce mode plus bas).

Le serveur api est obligatoire dans le cas ou vous utiliseriez les modes actif/actif et actif/passif ainsi que pour l'interface web.

Il permet également une interaction via un logiciel tiers ou même via scripts, il est donc très facile de personnalisé l'interface web de vscan ou de créer la votre (voir la documentation de l'api pour connaître les méthodes d'authentification et utilisation de celle-ci)

# L'agent
L'agent de vscan est également un composant optionnel, il est utilisé pour effectué des interactions avec les machines gérée par vscan. Le serveur API doit être installé pour le fonctionnement de l'agent.

L'agent est obligatoire pour les fonctionnements en actif/actif et actif/passif.


## Les modes de vscan
Il peut être activé de trois manières différentes : 

1. Mode actif/actif
2. Mode actif/passif
3. Mode passif/passif 

### Le mode actif/actif
Le mode actif/actif a plusieurs usages possibles, lorsque ce mode est mis en place il permet une remontée des logiciels installés sur la machine en question mais également d'effectuer  un certain nombre d’interaction a distance sur les machines.

Ce mode permet entre autre de créer des procédures en fonction des machines pour mettre en place une mitigation en cas d'attaque ou de suspicion (isolement de la machine, désactivation de certains composants, fonctionnement en mode dégradés etc..).

Il peut également permettre le patching de machines( désactivé par défaut dans ce mode il vous faudra l'activer et en aucun cas les patch ne seront déployés de façon automatique). 

### Le mode actif/passif
Le mode actif/passif est un mode ou seul le serveur est actif, l'agent remonte l'os, les logiciels et le matériel installés mais ne peut intervenir sur la machine en question. 
Il permet au serveur de maintenir une liste de logiciels et leurs version sur des environnement donnés. Vous pouvez ajouté les procédure pour obtenir les versions via l'interface web ou via api.
 

### Le mode passif/passif
Ce mode rend le serveur ainsi que l'agent passif. Le serveur servira de base de donnée de CVE/CPE, fera des correspondances et remontées d'alerte sur les logiciels, systèmes d'exploitation ou matériels que vous lui demanderez de suivre.
Dans ce mode vous n'avez pas d'agent actif sur les machines clientes et aucune possibilité de remonté les versions des composants installés.