# Vscan Documentation 

## Introduction

Vscan est une suite de logiciels de sécurité, open source développée principalement en Python 3 compatible 3.8 et supérieur.
Il est diffusé sous licence GPLv3
Celui-ci s'appuie sur une base de données SQL et possède de nombreuses configurations et usages possibles.

## Présentation 

Vscan a pour mission de répondre a plusieurs besoins plus ou moins spécifiques. Il est conçu pour donner une certaine souplesse à son utilisation et être multi-plateforme.
Il peut être utilisé de façon préventive, passive, ou être un élément de sécurité actif.

## Composition 

Vscan se compose de quatre grands logiciels distincts : 
1. Le serveur de backend,
2. Le serveur API,
3. L'agent,
4. L'interface web.

### Le serveur de backend
Le serveur de backend contient le moteur de vscan.
Ce moteur a diverses fonctionnalités possibles détaillées dans la page "Fonctions" de cette documentation.

Il a les rôles suivants : 

* Interaction avec la base de données.
* Gestion des dictionnaires de références CPE ([voir ce lien](https://www.cert-ist.com/public/fr/SO_detail?code=CPE))
* Gestion des remontées de failles logicielles, au niveau des systèmes d'exploitation ou encore matérielless ([voir ce lien](https://fr.wikipedia.org/wiki/Common_Vulnerabilities_and_Exposures))
* Faire correspondance entre CVE et CPE pour avoir une base de données lisible.
* Remontée des alertes de sécurité à la publication d'une faille.


### Le serveur API

Le serveur API est un composant optionnel, il n'est pas installé par défaut lors d'une installation de vscan via un paquet rpm.

En effet, vous n'êtes pas obligé de mettre en place le serveur API lors d'une utilisation de vscan en mode passif/passif (voir ce mode plus bas).

Le serveur API est obligatoire dans le cas ou vous utiliseriez les modes actif/actif et actif/passif ainsi que pour l'interface web.

Il permet également une interaction via un logiciel tiers ou même via scripts. Il est donc très facile de personnaliser l'interface web de vscan ou de créer la vôtre (voir la documentation de l'api pour connaître les méthodes d'authentification et utilisation de celle-ci).

# L'agent
L'agent de vscan est également un composant optionnel, il est utilisé pour effectuer des interactions avec les machines gérées par vscan. 

Le serveur API doit être installé pour le fonctionnement de l'agent.

L'agent est obligatoire pour les fonctionnements en actif/actif et actif/passif.


## Les modes de vscan
Il peut être activé de trois manières différentes : 

1. Mode actif/actif
2. Mode actif/passif
3. Mode passif/passif 

### Le mode actif/actif
Le mode actif/actif a plusieurs usages possibles. Lorsque ce mode est mis en place, il permet une remontée des logiciels installés sur la machine en question mais également d'effectuer un certain nombre d’interactions à distance sur les machines.

Ce mode permet, entre autres, de créer des procédures en fonction des machines pour mettre en place une mitigation en cas d'attaque ou de suspicion (isolement de la machine, désactivation de certains composants, fonctionnement en mode dégradés, etc.).

Il peut également permettre le patching de machines (désactivé par défaut, dans ce mode il vous faudra l'activer et en aucun cas les patchs ne seront déployés de façon automatique). 

### Le mode actif/passif
Le mode actif/passif est un mode où seul le serveur est actif, l'agent remonte l'OS, les logiciels et le matériel installés mais ne peut intervenir sur la machine en question. 
Il permet au serveur de maintenir une liste de logiciels et leurs versions sur des environnement donnés. Vous pouvez ajouter les procédures pour obtenir les versions via l'interface web ou via API.
 

### Le mode passif/passif
Ce mode rend le serveur ainsi que l'agent passif. Le serveur sert de base de données de CVE/CPE, fait des correspondances et des remontées d'alerte sur les logiciels, systèmes d'exploitation ou matériels que vous lui demandez de suivre.
Dans ce mode vous n'avez pas d'agent actif sur les machines clientes et aucune possibilité de remonter les versions des composants installés.