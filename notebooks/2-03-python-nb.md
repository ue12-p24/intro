---
jupytext:
  encoding: '# -*- coding: utf-8 -*-'
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Calysto Bash
  language: bash
  name: calysto_bash
---

Licence CC BY-NC-ND, Thierry Parmentelat & Valérie Roy

```{code-cell}
---
slideshow:
  slide_type: ''
tags: [raises-exception]
---
%%python
from IPython.display import HTML
HTML(filename="_static/style.html")
```

# Python

+++

## rappels

en guise de rappel, pour utiliser python vous pouvez:

- soit lancer un programme depuis le terminal avec  
  `$ python moncode.py`
- soit écrire / utiliser un notebook interactivement avec  
  `$ jupyter lab`
- soit pour un usage interactif et volatil (sans sauver votre travail) depuis le terminal  
  `$ ipython`

+++

## la complétion

on a déjà parlé de la complétion avec le terminal, c'est disponible également avec python:

exemple :

* on lance `ipython`
* on tape le début d'une commande, par exemple `import frac`
* à ce point, on appuie sur la touche `Tabulation` ( ⇥ )
* ipython se rend compte que le seul mot qui fait du sens dans ce contexte et qui commence
  par `frac` est `fractions`, du coup il remplit la commande

la complétion est un outil **indispensable** pour ne pas perdre un temps précieux;
apprenez à la maitriser

+++

## *RTFEM*

il est normal de faire des erreurs quand on code, tout le monde en fait

on verra un peu plus loin comment les détecter le plus tôt possible (grâce à des
extensions dans un éditeur de code)  
mais les cas où ça se produit quand même, la première chose à faire est bien entendu de
**lire le message d'erreur**

le langage Python s'efforce de vous donner des indications plutôt claires dans ces cas-là

voici par exemple un fichier très proche de `fact.py` qu'on vient de faire tourner  
mais j'y ai intentionnellement glissé une petite erreur de syntaxe  
voici le code, et ce qui se produit si on essaie de le faire tourner

```{code-cell}
:cell_style: split

cat ../demo/python/fact-broken.py
```

```{code-cell}
:cell_style: split

python ../demo/python/fact-broken.py
```

je vous demande en exercice de trouver l'erreur en question

en pratique, il arrive qu'on se trouve face à des erreurs plus difficiles à diagnostiquer,
mais dans tous les cas **commencez par *RTFEM***  
ça va de soi mais ça va mieux en le disant, je suis certain qu'on aura l'occasion de le
rappeler pendant les cours de langage :)

+++

## Python et vs-code

maintenant qu'on a installé Python, on peut retourner dans vs-code pour voir à quoi
ressemble l'extension Python (vérifiez que vous l'avez bien installée)

+++

###  les zigouigouis

pour commencer, l'extension Python vous permet de voir les erreurs dans votre code  
l'extension Python de vs-code va afficher **en permanence**  (à chaque sauvegarde) les soucis détectés par `pylint`


````{admonition} c'est quoi pylint ?
:class: admonition-small

`pylint` est un outil pour trouver les erreurs dans le code Python  
il détecte beaucoup d'erreurs (erreurs de syntaxe, variables mal orthographiées, etc..)  
si `pylint` n'est pas installé, vs-code va automatiquement vous proposer de le faire (choisissez alors de préférence l'option *install with pip*)
````

+++

### voir les erreurs

grâce à cette *feature* vous pouvez voir les erreurs **avant de lancer** votre programme; 
apprenez à les voir et à les corriger **avant même** d'essayer de faire tourner votre code, cela vous
fera gagner beaucoup de temps !

voici par exemple comment se manifeste, dans *vs-code*, le fichier `fact-broken.py` de tout à l'heure:  
en regardant bien, vous voyez apparaître un *zigouigoui* comme ceci ![](media/fig-vscode-zigouigoui.png) (en général c'est plus visible qu'ici, mais avec l'habitude vous détecterez cela tout de suite !)

+++

`````{grid} 1 1 2 2

````{card} que faire avec les zigouigouis
```{image} media/fig-vscode-errors-1.png
:align: center
:width: 500px
```
````

````{card} ouvrir l'onglet *PROBLEMS*
```{image} media/fig-vscode-errors-2.png
:align: center
:width: 500px
```
````
`````

+++

````{admonition} valeur indicative seulement
:class: warning

**attention** il faut toutefois toujours garder à l'esprit que cette phase de détection préliminaire des
erreurs de programmation n'a **qu'une valeur indicative**

`pylint` fait tous ses efforts, **mais** :

* ce n'est pas parce qu'un programme n'a pas de zigouigoui qu'il va tourner à coup sûr
* et réciproquement, il y a des programmes qui tournent alors qu'ils ont exhibé des erreurs

donc il faut garder votre cerveau en marche, et **ne pas se fier aveuglément** à cette information
````

+++

### terminal intégré

depuis vs-code, on peut exécuter du Python sans avoir à recourir au terminal (ou disons plutôt, il y a un terminal intégré dans vs-code, ce qui évite de basculer entre les applications); vous utilisez cette *feature* lorsque vous cliquez sur la flêche ici
```{image} media/fig-vscode-run-python.png
:align: center
:width: 300px
```

````{admonition} mise en garde
:class: warning

toutefois, on vous **met en garde**, car c'est d'une utilisation parfois (souvent) confusante ! 
aussi **si vous rencontrez des soucis** avec ce mode d'utilisation, préférez revenir à un mode bien contrôlé, qui consiste à basculer dans le "vrai" terminal, de façon à bien comprendre ce qu'on fait...
````

cette précaution étant prise, voici quelques mots sur cette feature:

+++

`````{admonition} réglages importants

à ce stade, il y a deux réglages importants pour utiliser le terminal intégré:

* (Windows surtout): choisissez le terminal `bash`, et pour cela [utilisez la palette](#label-vscode-palette) et tapez  
  *`Terminal: Select Default Profile`*

* assurez-vous aussi de bien utiliser le Python installé avec miniconda, et pour cela:

```{image} media/fig-vscode-select-python.png
:align: center
:width: 500px
```

````{admonition} environnements virtuels
:class: seealso note admonition-small

lorsqu'on fait du développement professionnel, on a habituellement une installation Python
par projet; une partie optionnelle avancée sera consacrée à ce sujet un peu plus loin
````
`````

+++

pour essayer, une fois ceci mis en place:

- mettez-vous dans le dossier `demo` du cours
- lancez `code .`
- ouvrez le fichier `fact.py`
- si vous n'avez pas encore installé l'extension 'Python' de *vs-code*, il va vous proposer de le faire
  n'hésitez pas à accepter (cela peut prendre un peu de temps...)
- cliquez sur la flêche (palette: `Python: Run Python File in Terminal`)  
  -> vs-code ouvre un terminal et exécute le fichier `fact.py`
- vous pouvez utiliser ```Control ` ``` (palette: `View: Toggle Terminal`) pour afficher/fermer le terminal intégré

mais à nouveau: **en cas de soucis avec cette *feature*, repassez au terminal "normal"** :)
