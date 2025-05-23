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
:tags: [raises-exception]

%%python
from IPython.display import HTML
HTML(filename="_static/style.html")
```

# vs-code & markdown

+++

## éditeur de code : micro-démo

> micro démo de Visual Code sur le fichier `foo.txt`

* depuis le terminal, aller dans le bon répertoire et lancer
  ```bash
  code .
  ```

(label-vscode-parameter)=

````{admonition} un exemple de passage de paramètre
:class: tip

*vs-code* est un éditeur qui travaille **sur un dossier**; comme ça:

* quand on fait une recherche, on recherche dans (tous les fichiers de) tout le dossier
* et aussi, d'une fois sur l'autre, on retrouve les fichiers qu'on avait consultés la fois précédente, 

c'est pourquoi on lance *vs-code* en tapant `code .` - et ici le `.` signifie "le dossier courant", [comme on l'a vu ici, rappelez-vous](#label-bash-dot)
````

````{admonition} *keyboard modifiers* (Control et Command)
:class: admonition-small
un éditeur de code comme VS-code utilise beaucoup les *modifiers*, les touches du clavier comme `Control` et `Command`  

comment ça marche ?  
dans la suite, quand on écrit par exemple **`⌃-N`** ça se lit comme "Control-N" et ça signifie que vous appuyez sur la touche *Control (⌃)*, et vous la maintenez enfoncée pendant que vous tapez la touche `n` (pas be soin de la touche Majuscule/Shift dans ce cas là); pareil pour la touche *Command (⌘)* sur Mac

enfin, notez que les raccourcis ne sont pas les mêmes sur Windows et sur Mac (ce serait trop simple);   
bien souvent (mais pas toujours) si le raccourci sur Windows est **`⌃-X`** alors sur Mac ce sera **`⌘-X`**
````

+++

### manipulations simples

pour plus de détails, voir aussi <https://code.visualstudio.com/docs/getstarted/userinterface>


on va montrer comment

* afficher/cacher l'explorateur de fichiers
* créer un nouveau fichier **`⌃-N`** (sur MacOS: **`⌘-N`**)
* lui donner un nom `foo.txt` avec le raccourci **`⌃-S`** (ça pourrait être quoi sur mac ?)
* modifier `foo.txt`, sauver la version modifiée
* créer un nouveau fichier `bar.txt`, le sauver
* montrer l'effet de l'**autosave** (menu *File*), il est **recommandé** de l'activer !
  montrer l'effet d'un fichier non sauvé (une boule noire au lieu de la croix, dans l'onglet à coté du nom de fichier)

* observer le contenu des fichiers depuis le terminal avec `cat`
* montrer comment se manifeste la fin de ligne

````{admonition} ouvrit avec simple-clic ou double-clic
:class: dropdown

essayez d'ouvrir un fichier (pas encore ouvert) depuis l'explorateur avec un simple ou un double clic  
il y a une différence subtile, pour la voir ouvrez-en plusieurs...
````

+++

### gestion des fenêtres

montrer des manipulations élémentaires de fenêtres

* afficher les deux fichiers côte à côte
* puis l'un au dessus de l'autre

+++

### extensions

* chercher une extension
* installer/désinstaller
* activer/désactiver une nouvelle extension
* **à faire**: installer les extensions
  * `Python` (de Microsoft)
  * `Jupyter` (de Microsoft aussi)

+++

(label-vscode-palette)=

### la palette

* de retour dans vs-code, montrer **la palette** :
  * `⇧ ⌘ P` Shift-Command-P (mac)
  * `⇧ ⌃ P` Shift-Control-P (windows)
* chercher une commande, par exemple `Format Document`

+++

### basculer entre les applications

* passer d'une application à une autre avec `⌥ ⇥` (Alt-Tab)
* typiquement pour basculer entre vscode et terminal

+++

### conseils

````{admonition} exécuter dans vs-code: pas recommandé !
:class: warning 

vs-code contient plein de fonctionnalités et notamment pour exécuter le code *directement dans vs-code* - 
c'est-à-dire sans retourner dans le terminal  
il faut **vous prévenir** que ces *features* sont notoirement **dures à configurer proprement**, aussi si vous rencontrez le moindre souci n'hésitez pas à **toujours utiliser le terminal natif** - en utilisant justement l'astuce juste ci-dessus pour gagner du temps dans ces aller-retours permanents
````

````{admonition} ouvrir un dossier plutôt qu'un fichier
:class: note

il est recommandé, avec vs-code, de prendre l'habitude d'ouvrir un **dossier**
(on dit aussi parfois un **répertoire**) plutôt qu'un fichier

si vous ouvrez un fichier (par exemple par un clic droit sur le fichier dans l'explorateur
de fichiers), vs-code va vous ouvrir le fichier dans une fenêtre déjà ouverte - souvent ça
va arriver comme un cheveu sur la soupe, dans un autre répertoire; si votre objectif c'est
d'ouvrir une nouvelle fenêtre, préfèrez ouvrir tout un dossier

pour cela, vous pouvez soit

* taper `code .` dans le terminal comme on l'a vu (et ici le `.` correspond au dossier courant)
* ou utiliser le clic droit depuis l'explorateur Windows, mais sur le dossier lui-même et non le fichier
````

````{admonition} vs-code et git
:class: tip
enfin pour bien utiliser vs-code avec git, [voyez cette section dans le notebook d'installation](label-vscode-for-commit)
````

+++

## markdown

+++

c'est un format simple, léger et bien pensé pour mettre en forme facilement vos textes, il
est devenu le couteau suisse pour écrire des documents

* avec un minimum de présentation
  * sections
  * listes
  * gras, italique, code
  * liens
  * maths
* toujours dans un **fichier texte** (c'est à dire par exemple, pas comme dans Word)

+++

format **très populaire** en ce moment, supporté e.g. :

* dans les notebooks, justement,
* dans discourse
* dans github
* sur whatsapp (en partie), …

et plus généralement dans tous les sites web de forums/blogs, où on peut entrer du texte
directement depuis le navigateur

+++

### micro-démo sous vs-code

> sous vs-code

* créer un fichier `foo.md`
* remarquer la petite icône ![](media/fig-vscode-markdown.png)
  * afficher côte à côte le markdown brut et rendu
* rapide survol
  * sections
  * listes avec et sans numérotation
  * gras, italique
* insister sur les plusieurs façons de mettre du code,
  * soit `inline` sans saut de ligne, ou alors
  * avec des "triple ticks" <code>```</code>
  * avec 4 espaces de marge
* images et liens
  * montrer le code markdown de cette cellule notebook

cheatsheet <https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf>

+++

## mathjax

+++

on peut aussi écrire **des maths en markdown**, ça se fait en utilisant le langage $\LaTeX$  
c'est un peu abscons au début mais on s'y habitue vite, en tous cas ça produit de très jolies équations, comme par exemple

$$
\forall \epsilon \in \mathbb{R}^+, \exists\alpha\in\mathbb{R}^+,
\forall x, |x-x_0| < \alpha\implies |f(x)-f(x_0)| < \epsilon
$$

$$
\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6}
$$

+++

### *inline*

à la base markdown utilise pour ça le signe `$`

si vous voulez mettre des maths dans un paragraphe (on dit *inline*), vous utilisez un
seul `$` au début et à la fin de l'équation; c-a-d si vous écrivez

```latex
voici une petite équation $y = x^2 +2x +1$ au milieu de la ligne
```

vous obtenez

voici une petite équation $y = x^2 +2x +1$ au milieu de la ligne

+++

### paragraphe séparé

pour mettre une équation dans un paragraphe séparé on double le dollar de début et de fin

du coup

```latex
$$
\forall x \in \mathbb{R}, \forall \epsilon \in \mathbb{R}^+, \exists\alpha\in\mathbb{R}^+ \\
 |x'-x| < \alpha\implies |f(x')-f(x)| < \epsilon
$$
```

se présentera comme ceci :

$$
\forall x \in \mathbb{R}, \forall \epsilon \in \mathbb{R}^+, \exists\alpha\in\mathbb{R}^+ \\
 |x'-x| < \alpha\implies |f(x')-f(x)| < \epsilon
$$

+++

au passage, vous remarquez que les commandes $\LaTeX$  commencent par `\`

+++

### les mots du jargon $\LaTeX$

+++

ça dépasse complètement notre périmètre que d'essayer de faire le tour de $\LaTeX$; je
préfère commencer par quelques exemples qui devraient vous permettre de démarrer

+++ {"cell_style": "split"}

$$
\forall x\in \mathbb{R},
\; \exists y \leq \epsilon
$$

+++ {"cell_style": "split"}

```latex
\forall x \in \mathbb{R},
\; \exists y \leq \epsilon
```

+++ {"cell_style": "split"}

$$x_1=\frac{-b+\sqrt{b^2-4ac}}{2a}$$

+++ {"cell_style": "split"}

```latex
x_1=\frac{-b+\sqrt{b^2-4ac}}{2a}
```

+++ {"cell_style": "split"}

$$
A_{m,n} =
 \begin{pmatrix}
  a_{1,1} & a_{1,2} & \cdots & a_{1,n} \\
  a_{2,1} & a_{2,2} & \cdots & a_{2,n} \\
  \vdots  & \vdots  & \ddots & \vdots  \\
  a_{m,1} & a_{m,2} & \cdots & a_{m,n}
 \end{pmatrix}
$$

+++ {"cell_style": "split"}

```latex
$$
A_{m,n} =
 \begin{pmatrix}
  a_{1,1} & a_{1,2} & \cdots & a_{1,n} \\
  a_{2,1} & a_{2,2} & \cdots & a_{2,n} \\
  \vdots  & \vdots  & \ddots & \vdots  \\
  a_{m,1} & a_{m,2} & \cdots & a_{m,n}
 \end{pmatrix}
$$
```

+++ {"cell_style": "split"}

$$
\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6}
$$

+++ {"cell_style": "split", "slideshow": {"slide_type": ""}}

```latex
\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6}
```

+++

```{admonition} pour aller plus loin
:class: dropdown

ceux qui veulent creuser peuvent

* s'exercer avec un outil en ligne <https://www.codecogs.com/latex/eqneditor.php>
* commencer par cet article 
<https://www.physicsoverflow.org/15329/mathjax-basic-tutorial-and-quick-reference>

* approfondir avec celui-ci <https://en.wikibooks.org/wiki/LaTeX/Mathematics>
```
