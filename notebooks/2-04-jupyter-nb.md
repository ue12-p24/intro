---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Calysto Bash
  language: bash
  name: calysto_bash
---

+++ {"slideshow": {"slide_type": ""}}

Licence CC BY-NC-ND, Thierry Parmentelat & Valérie Roy

```{code-cell}
%%python
from IPython.display import HTML
HTML(filename="_static/style.html")
```

(label-jupyter)=
# jupyter et notebooks

Les notebooks sont de petits *cahiers* d'exercices exécutables. Ils sont très pratiques
pour expliquer pas à pas ce qu'on fait, comme dans ces cours, mais ils sont aussi très pratiques dans la vraie vie !

Nous allons vous montrer dans cette section comment utiliser `jupyter`,
localement sur votre ordi, pour créer des notebooks avec des cellules de texte
et des cellules de code...

````{admonition} dépendances supplémentaires

si vous êtes en train de lire un cours que vous avez cloné depuis github, et que celui-ci contient un fichier `requirements.txt`, alors tapez également cette commande

```bash
pip install -r requirements.txt
```

et de cette façon, vous aurez déjà toutes les librairies utilisées à l'intérieur des notebooks (typiquement numpy, pandas, et autres éventuellement plus exotiques)
````

+++

## utilisation de base

pour lancer un serveur jupyter vous tapez dans le terminal la commande

```bash
jupyter lab
```

quelle que soit l'option choisie, le terminal va afficher plein de messages, 
mais ça aura aussi pour effet, bien plus intéressant, d'ouvrir une fenêtre ou un onglet dans votre navigateur Web:

`````{grid} 1 1 2 2
````{card} le serveur se lance dans le terminal 
```{image} media/jlab-001-blob.png
:align: center
```
````
````{card} mais ça ouvre aussi une page dans votre browser web
```{image} media/jlab-002-welcome.png
:align: center
```
````
`````

````{admonition} notebook classic
:class: dropdown seealso admonition-small

si on préfère on peut aussi lancer ceci - c'est une interface un peu plus simple, mais le principe est grosso-modo le même

```bash
jupyter notebook
```
````

+++

### le processus serveur

en fait là on fait deux choses complémentaires

* on lance un programme (le serveur Jupyter) qui tourne dans le terminal
* on demande au browser de créer une page qui interagit avec ce serveur

du coup ça signifie que **le serveur Jupyter doit tourner en permanence**

* si vous le tuez depuis le terminal, le notebook dans le browser va cesser de fonctionner
* ça signifie aussi que cette session du terminal n'est plus utilisable pour autre chose…

+++

## micro-démo Jupyter lab

depuis le navigateur, vous pouvez vous déplacer dans le cours  
pour commencer allez dans le dossier `demo/notebooks` où vous verrez ceci

```{image} media/jlab-003-in-demo.png
:align: center
:width: 600px
```

+++

### créer un notebook

créez un nouveau notebook, et appelez-le `foo` (*File* -> *Rename Notebook...*), vous devez voir maintenant ceci

```{image} media/jlab-004-new-notebook-foo.png
:align: center
:width: 600px
```

+++

### créer des cellules mixtes

à présent arrangez-vous pour créer une nouvelle cellule, de sorte à avoir une cellule de texte suivie d'une cellule de code, comme ceci

```{image} media/jlab-005-mixed-cells.png
:align: center
:width: 600px
```

+++

### gérer l'affichage

vous pouvez libérer de la place et supprimer le browser de fichiers sur la gauche  
essayez de cliquer sur les boutons de la barre de gauche pour comprendre la logique  
remarquez la troisième icône ![](media/jlab-006-toc-icon.png), qui permet d'afficher la table des matières

```{image} media/jlab-006-more-space.png
:align: center
:width: 600px
```

+++

### mode édition ou commande

chaque cellule est dans un des deux modes :

* édition : pour changer le contenu d'une cellule (le texte que vous tapez va directement dans la cellule)
* commande : cette fois quand vous tapez un caractère il est interprété comme une commande
* pour sortir du mode édition : tapez `Escape` ou encore `Control-M`

`````{grid} 1 1 2 2
````{card} en mode **'commande'**
voici à quoi ressemblent **nos deux cellules en mode 'commande'**

```{image} media/jlab-007-command-mode.png
:align: center
:width: 600px
```
````
````{card} et en mode **'édition'** - la différence est un peu subtile
```{image} media/jlab-007-edit-mode.png
:align: center
:width: 600px
```
````
`````

+++

### raccourcis utiles

autant prendre rapidement l'habitude d'utiliser les raccourcis clavier - ça va tellement plus vite !

parmi les plus fréquemment utilisés, il y a :

* `Shift-Entrée`: pour évaluer la cellule courante et passer à la suivante
* `⌥-Entrée`: pour évaluer la cellule et en insérer une dessous
* `Control-M M` pour passer la cellule courante en `Markdown`
* `Control-M Y` pour passer la cellule courante en `Code` (y comme pYthon)

il y a aussi des raccourcis pratiques pour créer directement des sections

* `Control-M 1` met la cellule en markdown, et insère si nécessaire un `#` au début de la
  cellule; on crée ainsi une cellule de titre de rang 1

* `Control-M 2` : de rang 2, etc…

pour une liste exhaustive, à partir du menu, faites *Help* → *Keyboard Shortcuts*

````{admonition} Control-M
:class: note

en fait, le préfixe `Control-M` est un raccourci pour **revenir en mode commande**  
et donc quand on dit que, par exemple, `Control-M M` fait passer en `Markdown`, il faut comprendre qu'en mode commande, la lettre `M` fait passer en `Markdown`; on ajoute juste le `Control-M` pour être sûr que la séquence marche dans les deux modes, mais si on est déjà en mode commande on n'a pas besoin de taper le `Control-M`
````

+++

### la palette

mimée sur celle de vs-code, il y a ici aussi une palette, que l'on invoque avec `Shift-Ctrl-C` (`Shift-Command-C` sur Mac)

c'est extrêmement utile pour trouver des commandes un peu évoluées, qui ne sont pas forcément toutes accessibles au travers d'un bouton dans l'interface

```{image} media/jlab-008-palette.png
:align: center
:width: 600px
```

+++

### sélection multiple

* en général on a exactement **une** cellule courante
* mais avec `Shift-⬆` ou `Shift-⬇` on peut sélectionner plusieurs cellules contigües

```{image} media/jlab-009-multiple-selection.png
:align: center
:width: 600px
```

c'est utile pour par exemple les déplacer toutes ensemble

+++

### déplacer les cellules

parlant de déplacer les cellules, on peut le faire à la souris comme ceci

```{image} media/jlab-010-move-cells.gif
:align: center
:width: 600px
```

+++

## lire le cours localement

maintenant que vous avez cloné le cours, et que vous savez utiliser Jupyter, vous pouvez lire le cours directement sur votre ordi  
on rappelle  toutes fins utiles qu'il est [nécessaire d'avoir bien configuré jupytext](#label-config-jupytext)

le rendu va être parfois un tout petit peu différent de la version web (HTML statique), mais c'est le même contenu
(enfin, si vous êtes bien  jour sur votre ordi, [voyez comment bien suivre les éventuelles modifications ultérieures](#label-git-pull))

+++

donc vous pouvez par exemple

* ouvrir un des notebooks de démonstration (dans le dossier `demo/notebooks`)  
  (on ne recommande pas forcément de commencer avec le présent notebook, car il utilise un kernel `bash` qui n'est pas standard…)

* l'exécuter localement
* et vous amuser à le modifier

+++

je vous demande surtout de

* ouvrir le notebook de checklist, qui résume les compétences attendues
* et vérifier que vous avez bien tout installé
* et si vous êtes en avance, attaquez-vous à l'exercice qui figure à la fin de la
  checklist
