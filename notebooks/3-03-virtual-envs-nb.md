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

# environnements virtuels

on voit ici comment créer de multiples environnements Python; ce n'est sans doute pas utile dans l'immédiat, mais cela vous sera peut-être utile bientôt...

+++

## à quoi ça sert ?

on l'a mentionné un peu plus haut, cela peut être utile de créer plusieurs environnements Python différents; c'est utile notamment :

* si vous travaillez sur plusieurs projets différents, qui ont chacun leur ensemble de
  dépendances, pas forcément compatibles entre elles;
  par exemple, l'un utilise Django-5.x et l'autre Django-3.x
  ou même, l'un utilise python-3.12 et l'autre python-3.11

* ou encore, lors de la sortie d'une nouvelle release de Python, que vous voulez essayer sans tout casser

il existe plusieurs solutions pour gérer cela, notamment la solution `virtualenv`, mais
nous allons pour notre part nous concentrer sur `miniconda`, puisque c'est ce qu'on a
installé

+++

## miniconda

c'est un des points forts de miniconda, que de permettre de facilement
créer/activer/détruire des environnements multiples; on entend par environnement :

* un socle `Python` accessible par les commandes `python` et `pip`
* installé au départ sans aucune librairie tierce (enfin si, disons plutôt le strict
  minimum, comme `pip`), pour que vous puissiez construire votre environnement de scratch

+++

les commandes utiles sont

* `conda env list`
* `conda create -n mon_environnement python=3.12`
* `conda env remove -n mon_environnement`

+++

et pour gérer tout cela, on dispose de commandes pour changer d'environnement; le modèle
mental est simple :

* lorsque vous créez un terminal, vous êtes dans l'environnement qui s'appelle `base`,
  c'est celui que vous avez utilisé jusqu'ici

* vous pouvez passer dans un autre environnement avec  
  `conda activate mon_environnement`  
  qui a pour effet, entre autres, de modifier votre `PATH` pour que la commande `python`
  soit cherchée ailleurs

* pour en sortir, et revenir dans `base`, vous faites  
  `conda deactivate`

+++

## exemple de session

voici à titre indicatif une session sous MacOS pour illustrer tout ceci

````{admonition} le prompt
:class: note

vous remarquerez comme le *prompt* bash reflète **l'environnement dans lequel on se
trouve**  
ça semble **relativement impératif** si on ne veut pas s'emmêler les pinceaux  
surtout n'utilisez pas cette technologie si votre prompt ne montre pas l'environnement
courant,  
c'est beaucoup trop facile de se tirer une balle dans le pied si on n'a pas cet
aide-mémoire en permanence sous les yeux !
````

+++

### la liste de mes environnements

```bash
[base] ~ $ conda env list
conda environments:
#
base                  *  /Users/tparment/miniconda3
<snip ...>
```

+++

### j'en crée un nouveau avec Python-3.12

```bash
[base] ~ $ conda create -n demo-py312 python=3.12
Collecting package metadata (current_repodata.json): done
Solving environment: done
<snip ...>
```

+++

### on le voit

```bash
[base] ~ $ conda env list
conda environments:
#
base                  *  /Users/tparment/miniconda3
demo-py312                /Users/tparment/miniconda3/envs/demo-py312
<snip...>
```

+++

### pour entrer dans le nouvel environnement

```bash
[base] ~ $ conda activate demo-py312
[demo-py312] ~ $
```

+++

### les packages installés

très peu de choses

```bash
[demo-py312] ~ $ pip list
Package    Version
---------- -------------------
certifi    2020.4.5.1
pip        20.0.2
setuptools 46.2.0.post20200511
wheel      0.34.2
```

+++

### on y installe ce qu'on veut

```bash
[demo-py312] ~ $ pip install numpy==1.15.3
```

+++

### la version de python

```bash
[demo-py312] ~ $ python --version
Python 3.8.2
```

+++

### sortir 

```bash
[demo-py312] ~ $ conda deactivate
[base] ~ $
```

+++

### la version de python

```bash
[base] ~ $ python --version
Python 3.7.6
```

+++

### on n'a pas perturbé l'environnement de départ

```bash
[base] ~ $ pip show numpy
Name: numpy
Version: 1.18.1
```

+++

### pour détruire l'environnement en question

```bash
[base] ~ $ conda env remove -n demo-py312

Remove all packages in environment /Users/tparment/miniconda3/envs/demo-py312:
```

+++

## exercice: de retour dans vs-code

* créez un nouvel environnement miniconda avec Python-3.12
* de retour dans vs-code, sélectionnez cet environnement

notez que ce réglage est associé au *workspace* vs-code

c'est quoi un *workspace* ? ça correspond en gros à la sauvegarde de l'état de l'éditeur
lui-même : la liste des fichiers en cours d'édition, les onglets ouverts, etc…  

pour expérimenter, créez une session vs-code dans un directory, choisissez votre
environnement Python, sortez de la session; ré-ouvrez vs-code sur le même répertoire, vous
devez retrouver ce réglage
