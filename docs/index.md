---
key_do_not_edit_lang: fr_FR
key_do_not_edit_label:
    key_do_not_edit_titreMenu: Sommaire
    key_do_not_edit_btnAffiche: Déplier
    key_do_not_edit_btnMasquer: Cacher
    key_do_not_edit_messageHeadMobile: Version mobile du site
---

# Présentation

Cette documentation à pour but d'expliquer comment mettre en place une documentations **"Github Page"** pour vos plugin Jeedom.

L'équipe jeedom SAS met à diposition se dépot prêt à l'emplois pour l'installation d'une documentation aux stadard jeedom.

Dans se document vous trouvez les différente étapes pour l'installation de la documentation dans votre plugin, les bases pour la mise en forme automatique, les configurations possible, des informations pour une personnalisation avancée, des liens vers des ressources.

# Préembule 
Pour générer la documentation d'un plugin, le principal composent utiliser c'est la fonction ["Gitub Page"](https://pages.github.com/), elle permet d'utiliser divers technologie affin de générer des fichier HTML pour créer un site statique.

Les pages de documentations sont écrit au format ["Mardown"](https://daringfireball.net/projects/markdown/), avec une extention ".md", ses fichier sont repris par 2 intérprétateurs.

- Le premier [Jekyll](https://jekyllrb.com/) permet d'ajouter un système de variable,fichier de configuration, et convertis les fichiers .md en HTML.

- Le deuxième, [Liquid](https://shopify.github.io/liquid/)  est un langage de template permetent de faire des calcule, teste, et traitement.

L'union de ses technologies permet une rédaction simple de page web sans connaissance en language de programation.

Pour les devloppeurs c'est un gains importent de temps tout en garantissent une présentation de qualité pour la documentation de leur plugin.


# Installation de la documentation

## Installation des fichiers et dossier

Se rendre sur le dépôt Github du Template docs Jeedom -> .......***URL à ajouter***.......

Télécharger sur votre ordinateur le .zip du dépot

Dans le dépot de votre plugin ou dans sont dossier local, créer un dossier ***docs*** à la racine

Dézipper le fichier télécharger dans le dossier local ***docs*** de votre plugin ou dans un dossier temporaire pour transférer les fichiers et dossiers dans le dosser ***docs*** de votre dépot Github. Le tout dois se trouver dans la branche **"master"**.

## Activation de Github Pages

Dans le dépôt de votre plugin, aller dans l'onglet **"Settings"**, randez-vous dans la partie **"Github Pages"**, dans la liste déroulante du paragraphe **"Source"** choisir **"master branch"**, puis sauver (Pas besoin de choisir de thème, tout configurer dans les fichiers installer précédement)

## Accèder à la page de documentations

A partir de là, vous avez une documentation fonctionnel accéssible à l'adresse 
> "https://VOTRE-NOM-UTILISATEUR.github.io/NOM-DU_DEPOT/docs/"


# Configuration de base

La totalité de la configuration, personnalisation de base à été regrouper dans une fichier de configuration nommer **"_config.yml"**, ce fichier permet de configurer simplement des élément comme les couleurs, le nom de l'image logo, le design (positionnement) à utiliser, les langues disponible ainssi que divers informations.

## Clé "theme"

Cette clé contien le nom du thème de base sur le quelle est fonder le thème jeedom, cette valeur ne dois pas être modifier.

## Clé "couleursPersoActif"

Cette clé prend comme valeurs **true** ou **false**, cela permet de switcher entre le jeu de **"couleursDefaut"** et **"couleursPerso"**, par défaut **couleursPersoActif** est paramétrer à **"false"** se qui active le jeu de couleur de la partie **"couleursDefaut"**.

## Clé "couleursDefaut"

Cette clé contiens d'autre clé (sous-clé), chaqu'une d'elle vous donnera la posibilité de modifier la couleur d'un élément du thème.

Le couleur doivent être au format hexadecimal (Hex), exemple : **#D5FE98** !!! sans le ***#*** !!!

En principe il ne faut pas modifier ses valeurs, se sont les couleurs par défaut du thème fournis par Jeedom, pour personnaliser les couleurs il convient d'utiliser la clé et les sous clé **"couleursPerso"**, pour switcher il vous faut modifier la clé **"couleursPersoActif"**

Exemple extret du fichier de configuration :
 	
    couleursDefaut:  
 		body-background-color: 'f0f8df' 
  		body-color: '2E5519'
  		head-background-color: '96C927'
  		head-color: 'f1ffe7'
  		hx-color: '82BA1B'
  		menu-background-color: 'D7F6C0'
  		menu-title-color: '82BA1B'
		menu-color: '1F5615'


### Clé : body-bakground-color

Cette clé permet de modifier la couleur de font de la partie texte de la documentation


### Clé : body-color

Cette clé permet de modifier la couleur du texte de la documentation


### Clé : head-background-color

Cette clé permet de modifier la couleur de font de l'entête de la page


### Clé : head-color

Cette clé permet de modifier la couleur du texte de l'entête de la page


### Clé : hx-color

Cette clé permet de modifier la couleur des titres et sous-titres de la documentation


### Clé : menu-background-color

Cette clé permet de modifier la couleur de font du menu "Sommaire"


### Clé : menu-title-color

Cette clé permet de modifier la couleur du texte du titre "Sommaire"


### Clé : menu-color

Cette clé permet de modifier la couleur du texte des liens du menu "Sommaire"


## Clé "couleursPesro"

Cette clé contiens d'autre clé (sous-clé), chaqu'une d'elle vous donnera la posibilité de modifier la couleur d'un élément du thème.

Le couleur doivent être au format hexadecimal (Hex), exemple : **#D5FE98** !!! sans le ***#*** !!!

En principe il convient de modifier cette clé et ses sous-clés pour modifier les couleurs, en cas de mauvais jeu de couleurs il vous sera donc possible de revenir facilement au couleurs par défaut en modifiant la clé **"couleursPersoActif"**

Les sous-clés sont les mêmes que pour la clé **"couleursDefaut"**, reporter vous à cette partie pour plus d'information.


## Clé "nomLogo"

Cette clé permet d'indiquer le nom de l'image qui fais office de logo du plugin dans Jeedom, cette image doit se trouver dans le dossier **"plugin_info"** qui se trouve à la racine du dossier de votre plugin, il faut juste indiquer le nom et sont extention, sans autre information.

Exemple : ***monPlugin_icon.png***


## Clé "themeVersion"

Cette clé donne la version du thème fourni par Jeedom, il ne faut en aucun cas la modifier, elle es utilisée par le script de convertion "ASCIIDOC" en "Markdown" et dans le future elle peut-être utilisée par un système de mise à jour du thème

La valeur de cette clé doit être un entier.


## Clé "design"

Cette clé permet de modifier la selection du fichier CSS de positionnement, par défaut le théme fourni par Jeedom dipose de 2 designs.

La clé prend en valeur un entier, par défaut elle veut **"1"**, pour le deuxième designe il suffi de lui donner la valeur **"2"**

## Clé "langs"

Cette clé contient un tableau de valeurs, qui représente les langues dispnible pour la documentation de votre plugin.

Chaque langues doit être au format "{{ page.key_do_not_edit_lang }}"

Exemple extret du fichier de configuration :
	
    [fr_FR,en_US,it_IT,ru_RU]

Actuelement la mise à jour de ses valeurs se fais manuellement, c'est a vous d'ajouter les valeurs qui correspondent, sauf dans le cas de l'utilisation du script de convertion (vois -> Convertion anciennent documentation) qui mettre les bonne valeur en fonction des fichier déjà présent.

Dans le futur il est prévu d'avoir une mise à jour automatique de la valeur à la création d'une nouvelle traduction (nouvelle langue non présente)

## Clé "dateConversion"

Cette clé donne la date et heure de conversion des fichier "ASCIIDOC" en "Markdown", il ne faut en aucun cas modifier cette valeur qui es utiliser par le scripe de conversion, et probablement aussi par le système de mise à jour du thème.

Le format de cette valeur **"2017-12-25-22h00"**


# Convertion anciennent documentation



# Guide de rédaction

# Personnalisation avancée

# Lien