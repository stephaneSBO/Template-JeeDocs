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

La rédaction de la documentation se fait en utilisant des fichiers **".md"** (Mardown). Ce format permet une rédaction rapide et simple, avec en plus une mise en forme rapide et facile à apprendre même pour les personnes qui n'ont pas de connaissances en programmation.

Pour réaliser la documentation, une fois installée et configurée, il n'y a aucun autre fichier à modifier que le(s) fichier(s) du dossier "./dossierMonPlugin/docs/docs/"

Pour éditer un fichier .md on peut utiliser n'importe quelle éditeur de texte, ou le faire directement depuis l'éditeur intégré à GitHub.

## Structure du fichier .md

Pour que le fichier .md soit valide, il doit être composé de 2 parties : 

1. La première partie doit commencer et se terminer par "---", entre les deux une série de clés qui vont permettre au système de gérer les éléments traduits dans l'interface de doc fournie par Jeedom.

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
   La partie de gauche de chacune de ces lignes ne doit surtout pas être modifiée, ce sont les clés (repère) pour le système. La partie de droite peut être modifiée, ce sont ces textes qui seront traduit dans les divers .md des autres langues.
 
 
2. La deuxième partie contient quand à elle le texte de la documentation.  
 
```
# Titre
## Sous-titre
paragraphe 
...
...
...
```

## Balisage de base

Sur internet il existe plein de sites qui décrivant les différentes balises qui serviront au convertiseur (.md en .html) pour la mise en forme des éléments. On se contentera donc ici de vous décrire les balises de base.

A savoir que le langage Mardown interprète certain caractères tel que "\\ \* \` \- \_ \[\] \(\) \{\} \# \+ \. \!", selon leur position ou répétition ils ne seront donc pas affichés mais interpretés pour la mise en forme. Pour pouvoir afficher un de ces caractères lorsqu'il est interprété, il faut donc les "échapper" avec le caractère "antislash" ( \\ ).


### Titre de premier niveau

Tout à gauche du fichier (sans espace avec le bord de page) placer un "\#" suivi d'un seul espace, puis le texte du titre.

Les titres de premier niveau sont repris automatiquement pour créer le menu "Sommaire".

###### Exemple :

```
# Titre 1
```    

### Titre de deuxième niveau

Tout à gauche du fichier (sans espace avec le bord de page) placer deux "\#" suivis d'un seul espace, puis le texte du titre.

Les titres de deuxième niveau sont repris automatiquement pour créer le menu "Sommaire".

###### Exemple :

```
## Titre 2
```   

### Titre du troisième au sixième niveau

Tout à gauche du fichier (sans espace avec le bord de page) placer entre 3 et 6 "\#" suivis d'un seul espace, puis le texte du titre.

Ces titres ***ne sont pas repris*** pour créer le menu "Sommaire".

###### Exemple :

```
### Titre 3
#### Titre 4
##### Titre 5
###### Titre 6
```

### Les paragraphes

Pour créer un nouveau paragraphe il suffit d'avoir un espace entre 2 lignes

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

Tout à gauche du fichier (sans espace avec le bord de page) placer un (*) suivi d'un espace pour créer une liste à puce, en allant à la ligne et ajoutant une tabulation ont peux créer un sous niveau de liste à puce.

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

Il y a plusieurs syntaxes pour cette mise en forme selon le résulat recherché. Entre [] se trouve le texte à afficher, puis sans espace entre () l'adresse internet, voici un exemple :

```
[Cliquer ici](https://www.google.com)
```



### Les images

Les images doivent  se trouver dans le dossier "./dossierMonPlugin/docs/images/", pour les ajouter dans votre documentation, il faut utiliser la syntaxe ![] qui contient le texte alternatif si l'image n'est pas trouvée suivi directement sans espace de () qui contient le lien vers l'image à partir de la racine de la documentation.

###### Exemple :

```
![image -> markdown_logo.png introuvable](../img/markdown_logo.png)
```

### Bloc code

#### sans coloration syntaxique

Pour afficher du code mis en évidance sans coloration syntaxique, il faut sur une nouvelle ligne mettre 3 backqute "***\```***" suivi du code que l'on souaite afficher, puis à nouveau 3 backqute "***```***"

###### Exemple :

```
Mon code ici
```

#### avec coloration syntaxique

Comme pour le bloc code sans coloration, il faut sur une nouvelle ligne mettre backqute "***```***", affin d'ajouter la coloration cette il faut directement après la 3ème ajouter le nom du langage.

Exemple : 
```
\```javascript
if(true){
 var text = "mon texte";
}
\```
```

###### Résultat :

```javascript
if(true){
 var text = "mon texte";
}
```


# Personnalisation avancée

***!!! ATTENTION !!!*** les developpeurs ont un devoir de fournir une doc de qualité et une présentation convenable, modifier les fichier qui sont présenter si dessous risque de rendre illisible la documentation, il vous faut donc prendre toutes les précotions pour pouvoir revenir a une version convenable, vous etes seul résponsable en cas de problème si vous avez modifier ses fichiers.

Il y as plusieurs niveau de personnalisation avancé, le premier "Création de sont propre design" comporte peux de risque car il suffi de changer le fichier SCSS pour reprendre un design valider, les autres modification touche au système de thème proposer par jeedom, cela aura pour consécance des modification profonde, de par ce fais une impossibilité d'utiliser les mises à jours proposer par Jeedom sans écraser les votres.

## Création de sont propre design

Il est possible de créer sont propore design, par design on entant positionnement des divers éléments de la page.

Pour créer sont propre design il faut créer un nouveau fichier ".scss" dans le dossier ./assets/css/".

Le nom du fichier doit être dans le format : styleJeedom-***X***.scss, ou ***X*** est un numéro de fichier a mettre en fonction du nombre d'autre fichier design disponible, par defaut il y en as 2, le nom du nouveau fichier serais donc "styleJeedom-3.scss".

Il vous faut commancer le fichier par 2 ligne avec 3 tirrets.

###### exemple : 

```
---
---
votre code CSS et SCSS
```

Dans le fichier de configuration ***_config.yml*** modifier la clé : ***design*** avec le nombre que vous avez attribuer au nouveau fichier ***styleJeedom-X.scss***

A partire de la il sera pris en compte comme fichier de style en plus des fichiers de base (style.scss et toc.scss) qui vont attribuer les valeurs de base aux éléments de la page.

Les couleurs reste appliquer depuis style.scss et toc.scss, il faut donc modifier dans le fichier de configuration _config.yml.

## Modification profonde

***!!! ATTENTION !!!*** la modification des fichiers nommer si dessous peux avoir un impacte importent sur le fonctionnement et le résultat d'affichage de la documentation, l'équipe jeedom ne peux donc assumer du support en cas de modification de ses fichiers.

### Fichier : default.html

Dans le dossier ./_layouts/, se fichier est le template de base pour générer la page de documentation, il est composer de plusieurs éléments telque du HTML, Liquid, JavaScript, YAML.

Le fichier est lus par GitHub Page pour créer la version HTML distribuer au clien.

### Fichier : style.scss

Dans le dossier ./assets/css/, ce fichier contiens les instruction css de base du thème, la personnalisation des couleurs reprise du fichier _config.yml

### Fichier : toc.scss

Dans le dossier ./assets/css/, se fichier contiens les instruction css de base pour le menu "Sommaire", ainsi que la personnalisation des couleurs reprise du fichier _config.yml pour cette partie.

### Fichier : jquery.inview.min.js<nolink>

Plugin Jquery qui permet de savoir si un élément entre ou sort de l'espace visible, il permet l'effet de mise en gras des titres dans le menu "sommaire" quant les éléments sont visible.

Source : https://github.com/protonet/jquery.inview


### Fichier : jquery.toc.js<nolink>

Plugin Jquery qui permet d'avoir un menu autogénérer 

Source : http://projects.jga.me/toc/


### Fichier : custom.jeedom.js<nolink>

Plugin Jquery qui permet d'ajouter des fonctionnalité et personnalisation via Javascript pour le thème jeedom.



# Lien - Ressources


* EN
	* ["GitHup Page"](https://pages.github.com/) : Site officiel pour le générateur de page hébérger par GitHub
	* ["Help on Github"](https://help.github.com/categories/writing-on-github/): Documentation Github
	* ["Doc Mita donnée Github Page"](https://help.github.com/articles/repository-metadata-on-github-pages/) : Documentation sur les variable globale disponnible dans Jekyll avec Github page
	* ["Mastering Markdown"](https://guides.github.com/features/mastering-markdown/)
	* ["MarkDown Cheatsheet"](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) : Explication condancée
	* ["Documentation GitLab"](https://docs.gitlab.com/ee/user/markdown.html) : Documentation Markdown du site GitLab
	* ["Dépot GitHub Jekll"](https://github.com/jekyll/jekyll/tree/master/docs) : Dépot officiel du générateur de page Jekll
	* ["Site de documentation Jekyll"](https://jekyllrb.com/) : Site officiel de documentation Jekyll hébérger sur GitHub Page
	* ["Site officiel du language Liquid"](https://shopify.github.io/liquid/) : Site officiel du language Liquide avec documentation, utiliser dans default.htmlet fichier .scss
* FR
	* ["Cour Markdown OpenClassRooms"](https://openclassrooms.com/courses/redigez-en-markdown) : Cour sur les base du Markdown du site OpenClassRooms
	* ["Guide d'un blog"](https://blog.wax-o.com/2014/04/tutoriel-un-guide-pour-bien-commencer-avec-markdown/) : Guide du blog de de Fabien Huet
	* ["Information Wikipedia"](https://fr.wikipedia.org/wiki/Markdown) : Page Wikipédia sur Markdown
	* ["Tuto vidéo FR de Grafikart"](https://www.grafikart.fr/tutoriels/html-css/jekyll-505) : Tuto vidéo d'explication Markdown
	* ["Pense Bête Markdown"](https://github.com/jamstatic/jamstatic-fr/wiki/Pense-b%C3%AAte-Markdown) Pense Bête ent Français pour la rédaction Markdown
