<!-- ---
title: A4-Forge
description: Un outil pour transformer automatiquement les fichier Markdown de son répertoire en pages HTML au format A4, prêtes pour l'impression
header-includes: |
  <link rel="stylesheet" href="https://unpkg.com/sakura.css/css/sakura.css" media="screen" />
  <link rel="stylesheet" href="https://unpkg.com/sakura.css/css/sakura-dark.css" media="screen and (prefers-color-scheme: dark)" />
  <style>pre > code {white-space: pre-line;}a{color:darkorchid!important}</style>
--- -->

# Mise en forme automatique au format A4 de ses fichiers Markdown

**A4-Forge** (sur [Gitlab](https://forge.apps.education.fr/eyssette/a4-forge) ou sur [Github](https://github.com/eyssette/a4-forge)) est un outil pour transformer automatiquement les fichiers Markdown de son répertoire en pages HTML au format A4, prêtes pour l'impression.

Les fonctionnalités sont les suivantes :

1. Un calcul automatique de la taille de police optimale pour que le contenu du document tienne sur le nombre de pages choisi, sans dépassement.
2. La possibilité de choisir le nombre de pages, le nombre de colonnes, une impression en format paysage ou portrait
3. La possibilité de répéter plusieurs fois le même contenu sur les différentes pages ou colonnes
4. Un respect automatique des règles typographiques françaises sur les espaces insécables

## Quelques exemples

- Impression sur une page : [rendu](https://eyssette.forge.apps.education.fr/a4-forge/test-1page), [source](https://forge.apps.education.fr/eyssette/a4-forge/-/blob/main/test-1page.md?plain=1)
- Impression sur 3 colonnes, avec répétition du même contenu : [rendu](https://eyssette.forge.apps.education.fr/a4-forge/test-3colonnes-copies), [source](https://forge.apps.education.fr/eyssette/a4-forge/-/blob/main/test-3colonnes-copies.md?plain=1)
- Impression sur 2 pages et 3 colonnes : [rendu](https://eyssette.forge.apps.education.fr/a4-forge/test-2pages), [source](https://forge.apps.education.fr/eyssette/a4-forge/-/blob/main/test-2pages.md?plain=1)


## Configuration de l'impression

Pour configurer l’impression, il faut ajouter un en-tête au début de votre document markdown. Plusieurs paramètres sont disponibles.

Voici un exemple avec tous ces paramètres (on n'est pas obligé de tous les utiliser) :

```yaml
---
pages: 1
colonnes: 2
espacementColonnes: 20px
mx: 20px
my: 20px
paysage: true
copies: 2
maths: true
---
```

- `pages` et `colonnes` indiquent respectivement le nombre de pages et de colonnes
- on peut définir l'espacement en pixels entre les colonnes : `espacementColonnes: 30px`
- `mx` et `my` définissent les marges à gauche et à droite (pour `mx`), en haut et en bas (pour `my`)
- pour une impression en format paysage, on met `paysage: true`
- pour recopier plusieurs fois le contenu du document (par exemple pour mettre deux fois le même contenu sur une page A4 pour ensuite découper sa page et distribuer du A5), il faut indiquer le nombre de copies ainsi : `copies: 2` pour deux copies.
- `maths: true` permet d'écrire des formules mathématiques avec la syntaxe `$FORMULE$` ou `$$FORMULE$$`. Si la formule est trop longue, la mise en page risque cependant d'être perturbée et il faudra la retoucher manuellement.


## Trois usages possibles

### 1/ Conversion en ligne

Copiez-coller votre markdown dans cet outil de conversion en ligne et cliquez sur le bouton “Convertir”:

<https://a4.forge.apps.education.fr>


### 2/ Sur une forge

Clonez ce dossier (sur [Gitlab](https://forge.apps.education.fr/eyssette/a4-forge) ou sur [Github](https://github.com/eyssette/a4-forge)) et créez des fichiers markdown dans votre dossier cloné.
Ils seront automatiquement convertis et accessibles en ligne.

Sur Github, il faudra donner la permission : `Read and Write` dans : `Settings/Actions/General/Workflow permissions`

### 3/ En local

Récupérez ce dossier (sur [Gitlab](https://forge.apps.education.fr/eyssette/a4-forge) ou sur [Github](https://github.com/eyssette/a4-forge)) en local et ouvrez-le avec VSCode. Une tâche pour VSCode est définie dans le dossier .vscode afin d'automatiser la conversion du fichier markdown sur lequel vous travaillez.

Vous pouvez aussi utiliser le template pandoc, le filtre fr-nbsp.lua et le fichier CSS utilisé par défaut.

## Syntaxe markdown autorisée

Hormis la syntaxe ordinaire, on peut aussi utiliser des codes emojis (p.ex. `:smile:`), le surlignement (`==texte surligné==`) et les blocs admonitions :

```
::: warning
Attention, bloc spécial de texte
:::
```

On peut aussi utiliser des balises HTML et notamment la balise `<style></style>` à l'intérieur de son document afin de modifier la feuille de style CSS.

On peut insérer des images avec la syntaxe Markdown habituelle : `![](URL)` mais le redimensionnement des images ne se fera pas automatiquement. On peut cependant utiliser la balise `<style>` afin de faire des modifications en CSS pour imposer une taille maximum de l'image (par exemple : `<style>img {max-height:100px}</style>`).


## Crédits

Cet outil est distribué gratuitement et sous licence libre.

Il dépend des outils libres suivants : [pandoc](https://pandoc.org/) et [fr-nbsp](https://github.com/InseeFrLab/pandoc-filter-fr-nbsp) pour les versions sur forge ou en local, et [Markdown-it](https://github.com/markdown-it/markdown-it), [Markdown-it-Emoji](https://github.com/markdown-it/markdown-it-emoji), [Markdown-it-Admonition](https://github.com/docarys/markdown-it-admonition)  et [js-yaml](https://github.com/nodeca/js-yaml) pour la version en ligne.

## Autres logiciels à tester

N'hésitez pas également à tester [pdfautonup et pdfimpose](https://ababsurdo.fr/blog/20240325-imposition-pour-les-profs/), des logiciels libres créés par [Louis Paternault](https://ababsurdo.fr/apropos/)