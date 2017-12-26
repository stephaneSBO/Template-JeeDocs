---
key_do_not_edit_lang: fr_FR
key_do_not_edit_label:
    key_do_not_edit_titreMenu: Sommaire
    key_do_not_edit_btnAffiche: Déplier
    key_do_not_edit_btnMasquer: Cacher
    key_do_not_edit_messageHeadMobile: Version mobile du site
---

# Présentation

Cette documentation à pour but d'expliquer comment mettre en place une documentation **"Github Page"** pour vos plugins Jeedom.

L'équipe jeedom SAS met à diposition ce dépôt prêt à l'emploi pour l'installation d'une documentation aux standards jeedom.

Dans ce document, vous trouverez les différentes étapes pour l'installation de la documentation dans votre plugin, les bases pour la mise en forme automatique, les configurations possibles, des informations pour une personnalisation avancée, des liens vers diverses ressources.

Nb: Les documentations Github Pages sont compatibles avec les dépôts privés.

# Préambule 
Pour générer la documentation d'un plugin, le principal composant utilisé est la fonction ["Gitub Page"](https://pages.github.com/), elle permet d'utiliser diverses technologies afin de générer des fichier HTML pour créer un site statique.

Les pages de documentation sont écrites au format ["Mardown"](https://daringfireball.net/projects/markdown/), avec une extension ".md", ses fichiers sont repris par 2 intérpréteurs.

- Le premier [Jekyll](https://jekyllrb.com/) permet d'ajouter un système de variable, fichier de configuration, et converti les fichiers .md en HTML.

- Le deuxième, [Liquid](https://shopify.github.io/liquid/) est un language de template permettant de faire des calculs, tests, et traitements.

L'union de ses technologies permet une rédaction simple de page web sans connaissance en language de programmation.

Pour les developpeurs c'est un gain important de temps tout en garantissant une présentation de qualité pour la documentation de leurs plugins.


# Installation de la documentation

## Installation des fichiers et dossiers

Se rendre sur le dépôt Github du Template JeeDocs -> .......***URL à ajouter***.......

Télécharger sur votre ordinateur le .zip du dépôt.

Dans le dépôt de votre plugin ou dans son dossier local, créer un dossier ***docs*** à la racine.

Dézipper le fichier téléchargé dans le dossier local ***docs*** de votre plugin ou dans un dossier temporaire pour transférer les fichiers et dossiers dans le dossier ***docs*** de votre dépôt Github. Le tout doit se trouver dans la branche **"master"**.

## Arborescence 

Dans le schéma ci-dessous vous trouverez l'arborescence du système de documentation. Le "." représentant la racine du dossier ***docs*** de votre plugin, les différents dossiers et fichiers indiqués doivent donc se trouver à l'intérieur de ce dossier ***docs***. Vous pouvez voir qu'il y a un sous-dossier **"docs"**, dans lequel il faut bien mettre les fichiers **".md"**.

Exemple : 
> ./dossierMonPlugin/docs/docs/MesFichiers.md

Arborescence :

```		
	.
	|-- _config.yml
	|-- _layouts
		|--default.html
	|-- assets
		|-- logo_white.png
		|-- css
            		|-- style.scss
			|-- styleJeedom-1.scss
			|-- styleJeedom-2.scss
			|-- toc.scss
	|-- docs
		|-- index.md
		|-- (autres fichiers .md des traductions)
		|-- ...
	|-- images
		|-- (images utilisées par la documentation)
		|-- ...
	|-- js
		|-- custom.jeedom.js
		|-- jquery.inview.min.js
		|-- jquery.toc.js
```        


## Activation de Github Pages

Dans le dépôt de votre plugin, aller dans l'onglet **"Settings"**, rendez-vous dans la partie **"Github Pages"**, dans la liste déroulante du paragraphe **"Source"** choisir **"master branch"**, puis sauver. (Pas besoin de choisir de thème, tout est configuré dans les fichiers installés précédemment)

## Accéder à la page de documentation

A partir de là, vous avez une documentation fonctionnelle accessible à l'adresse 
> "https://VOTRE-NOM-UTILISATEUR-GITHUB.github.io/NOM-DU_DEPOT/docs/"


# Configuration de base

La totalité de la configuration et personnalisation de base à été regroupée dans un fichier de configuration nommé **"_config.yml"**. Ce fichier permet de configurer simplement des éléments comme les couleurs, le nom de l'image logo, le design (positionnement), les langues disponibles ainsi que diverses informations.

## Clé "theme"

Cette clé contient le nom du thème de base sur lequel est fondé le thème jeedom, cette valeur ne doit pas être modifiée.

## Clé "couleursPersoActif"

Cette clé prend comme valeur **false** ou **true**, cela permet de basculer entre le jeu de **"couleursDefaut"** (false) et **"couleursPerso"** (true), par défaut **couleursPersoActif** est paramétré à **"false"**.

## Clé "couleursDefaut"

Cette clé contient d'autres clés (sous-clés), chacune d'elles vous donnera la posibilité de modifier la couleur d'un élément du thème.

Les couleurs doivent être au format hexadecimal (Hex), exemple : **#D5FE98** !!! sans le ***#*** !!!

En principe il ne faut pas modifier ces valeurs, ce sont les couleurs par défaut du thème fourni par Jeedom, pour personnaliser les couleurs il convient d'utiliser la clé et les sous-clés **"couleursPerso"**. (Pour basculer il vous faut modifier la clé **"couleursPersoActif"**)

Exemple extrait du fichier de configuration :
 	
```
couleursDefaut:  
	body-background-color: 'f0f8df' 
	body-color: '2E5519'
	head-background-color: '96C927'
	head-color: 'f1ffe7'
	hx-color: '82BA1B'
	menu-background-color: 'D7F6C0'
	menu-title-color: '82BA1B'
	menu-color: '1F5615'
```

### Sous-Clé "body-background-color"

Cette clé permet de modifier la couleur de fond du corps de la documentation.


### Sous-Clé "body-color"

Cette clé permet de modifier la couleur du texte du corps de la documentation.


### Sous-Clé "head-background-color"

Cette clé permet de modifier la couleur de fond de l'entête de la documentation.


### Sous-Clé "head-color"

Cette clé permet de modifier la couleur du texte de l'entête de la documentation.


### Sous-Clé "hx-color"

Cette clé permet de modifier la couleur des titres et sous-titres de la documentation.


### Sous-Clé "menu-background-color"

Cette clé permet de modifier la couleur de fond du menu "Sommaire".


### Sous-Clé "menu-title-color"

Cette clé permet de modifier la couleur du texte du titre "Sommaire".


### Sous-Clé "menu-color"

Cette clé permet de modifier la couleur du texte des liens du menu "Sommaire".


## Clé "couleursPesro"

Cette clé contient d'autres clés (sous-clés), chacune d'elles vous donnera la posibilité de modifier la couleur d'un élément du thème.

Les couleurs doivent être au format hexadecimal (Hex), exemple : **#D5FE98** !!! sans le ***#*** !!!

En principe il convient de modifier cette clé et ses sous-clés pour modifier les couleurs, en cas de mauvais jeu de couleurs il vous sera donc possible de revenir facilement aux couleurs par défaut en modifiant la clé **"couleursPersoActif"**.

Les sous-clés sont les mêmes que pour la clé **"couleursDefaut"**, reportez-vous à cette section pour plus d'informations.


## Clé "nomLogo"

Cette clé permet d'indiquer le nom de l'image qui fait office de logo du plugin dans Jeedom, cette image doit se trouver dans le dossier **"plugin_info"** qui se trouve à la racine du dossier de votre plugin, il faut juste indiquer le nom et son extension, sans autres informations.

Exemple : ***monPlugin_icon.png***


## Clé "themeVersion"

Cette clé donne la version du thème fourni par Jeedom, il ne faut en aucun cas la modifier, elle est utilisée par le script de conversion "ASCIIDOC" en "Markdown" et dans le futur elle peut être utilisée par un système de mise à jour du thème.

La valeur de cette clé doit être un entier.


## Clé "design"

Cette clé permet de choisir un fichier CSS de positionnement. Par défaut le thème fourni par Jeedom dipose de 2 designs.

La clé prend en valeur un entier, par défaut elle vaut **"1"**, pour le deuxième design il suffit de lui donner la valeur **"2"**.

## Clé "langs"

Cette clé contient un tableau de valeurs, qui représentent les langues disponibles pour la documentation de votre plugin.

Chaque langue doit être au format "{{ page.key_do_not_edit_lang }}"

Exemple extrait du fichier de configuration :

```
[fr_FR,en_US,it_IT,ru_RU]
```

Actuellement la mise à jour de ces valeurs se fait manuellement, c'est à vous d'ajouter les valeurs qui correspondent, sauf dans le cas de l'utilisation du script de conversion (choix -> Conversion ancienne documentation) qui mettra les bonnes valeurs en fonction des fichiers déjà présents.

Dans le futur il est prévu d'avoir une mise à jour automatique de la valeur à la création d'une nouvelle traduction (nouvelle langue non présente).

## Clé "dateConversion"

Cette clé donne la date et heure de conversion des fichiers "ASCIIDOC" en "Markdown", il ne faut en aucun cas modifier cette valeur qui est utilisée par le script de conversion, et probablement aussi par le système de mise à jour du thème.

Le format de cette valeur est **"2017-12-25-22h00"**


# Conversion ancienne documentation



# Guide de rédaction

La rédaction de la documentation se fais en utilisent des fichiers **".md"** (Mardown), cela permet unrédaction aussi rappide qu'avec un simple fichier texte, avec en plus la mise en forme rapide et facile à apprendre même pour les personnes qui non pas de connaissence en programmation.

Pour réaliser la documentation, une fois installer et configurer, il ni as donc aucun autre fichier à modifier que le(s) fichier(s) du dossier "./dossierMonPlugin/docs/docs/"

On peux pour éditer un fichier .md utiliser n'importe quelle éditeur de texte, ou directement depuis l'éditeur intégrer au dépot GitHub.

## Structure du fichier .md

Pour que le fichier .md soie valide, il doit être composé de 2 parties : 
1. La première partie doit commancer et se terminer par "---", entre deux série de clé qui vont permetre au système d'ajouter des éléments linguistique traduit dans l'interface fournie par jeedom pour la doc

    ```
    ---
    key_do_not_edit_lang: fr_FR
    key_do_not_edit_label:
    key_do_not_edit_titreMenu: Sommaire
    key_do_not_edit_btnAffiche: Déplier
    key_do_not_edit_btnMasquer: Cacher
    key_do_not_edit_messageHeadMobile: Version mobile du site
    ---
    ```
   La partie de gauche de chaqu'une de ses lignes ne doit sur tout pas être modifier se sont les clés (repère) pour le système, la partie de droite peux être modifier pour changer le texte, c'est eux qui seront traduit dans les divers .md d'autre langue.
 
 
2. La deuxième partie contiens quant à elle le contenu propement dis.  
   
    	# Titre
      	## Sous-titre
      	paragraphe 
      	...
      	...
      	...
 


## Balisage de base

Sur internet nous trouvons pliens de site qui décrivent quelles sont les règle pour les différent balisages qui servirons au convertiseur .md en .html pour la mise en forme des élément, on se contentera donc ici de vous donnez juste les règles de base.

A savoir que le langage Mardown interprète certin caractère telque "\\ \* \` \- \_ \[\] \(\) \{\} \# \+ \. \!", selon leur position ou répétition il ne seront donc pas afficher mais interpreter pour la mise en forme. Pour pouvoir afficher un de ses caractères il faut donc les "échappers" avec le caractère "antislash" ( \\ ) si il n'es pas afficher


### Titre de premier niveau

Tout as gauche du fichier (sans espace avec le bord de page) placer un "\#" suivit d'un seul espace, puis le texte du titre.

Les titres de premier niveau sont repris automatiquement dans le menu "Sommaire" pour le créer.

###### Exemple :

```
# Titre 1
```    

### Titre de deuxième niveau

Tout à gauche du fichier (sans espace avec le bord de page) placer deux "\##" suivit d'un seul espace, puis le texte du titre.

Les titres de deuxième niveau sont repris automatiquement dans le menu "Sommaire" pour le créer.

###### Exemple :

```
## Titre 2
```   

### Titre de troixième niveau au sixième

Tout à gauche du fichier (sans espace avec le bord de page) placer entre 3 et 6 "\#" suivit d'un seul espace, puis le texte du titre.

Ces titres ***ne sont pas repris*** pour créer le menu "Sommaire".

###### Exemple :

```
### Titre 3
#### Titre 4
##### Titre 5
###### Titre 6
```

### Les paragraphes

Pour créer un nouveau paragraphe il suffi d'avoir un espace entre 2 lignes

###### Incorrect :

```
Paragraphe 1
Paragraphe 2
```        
   
###### Correct :
      
```
Paragraphe 1
        
Paragraphe 2
```

        
### Les listes à puce

Tout à gauche du fichier (sans espace avec le bord de page) placer un (*) suivi d'un espace pour créer une liste à puce, en allent à la ligne et ajoutant une tabulation ont peux créer un sous niveau de liste à puce.

###### Exemple : 

```
* texte
* texte
* texte
	* texte
   	* texte
* texte
```

### Les liens internet

Il y as plusieurs syntaxe pour cette mise en forme selon le résulat rechercher, entre [] se trouve le texte à afficher, puis sans espace entre () l'adresse internet, voici un exemple :

```
[Cliquer ici](https://www.google.com)
```



### Les images

Les images doivent  se trouver dans le dossiers "./dossierMonPlugin/docs/images/", pour les ajouter dans votre documentation, il faut uriliser la syintaxe ![] qui contien le texte alternatif si l'image n'es pas trouver suivi directement sans espace de () qui contien le lien vers l'image a partire de la racine de la documentation.

###### Exemple :

```
![image -> markdown_logo.png introuvable](../img/markdown_logo.png)
```

### Bloc code

#### sans coloration syntaxique

#### avec coloration syntaxique



# Personnalisation avancée

# Lien
