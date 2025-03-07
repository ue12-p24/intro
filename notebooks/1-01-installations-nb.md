---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3 (ipykernel)
  language: python
  name: python3
---

Licence CC BY-NC-ND, Thierry Parmentelat & Valérie Roy

```{code-cell}
:tags: [raises-exception]

%%python
from IPython.display import HTML
HTML(filename="_static/style.html")
```

# installations

ce notebook vise à vous permettre de faire toutes les installations nécessaires

+++

## la liste des outils

cliquez dans la bande verte pour voir le détail des outils que nous utilisons

````{admonition} la liste des outils
:class: seealso dropdown

il nous faut a minima

* le **terminal** - nous utilisons **`bash`**, qui est
  * natif sur les OS linux et MacOS,
  * et qui vient avec le produit `git for windows`
* l'éditeur de code **Visual Studio Code**, mieux connu comme VS-code
* **miniconda** pour Python (et les environnements virtuels)
* **Jupyter** pour les notebooks
  * on parlera un peu de *markdown* pour la mise en forme du texte,
  * et de $\LaTeX$ pour les formules mathématiques
* **Git** pour la gestion de versions  
  * c'est un outil super-utile pour le développement, c'est indispensable que vous sachiez l'utiliser  
* enfin on configurera également un compte sur **github.com**
  * pour le stockage de vos travaux - typiquement les rendus
  * et le travail en groupe - typiquement les hackatons et projets
````

+++

## quelques conseils

mais avant de commencer, voici quelques recommandations générales:

````{admonition} à lire attentivement !!
:class: attention

ceux qui zappent cette section ont 95% de chances de tomber dans le piège
````

+++

### comment tester une installation

après avoir installé, disons par exemple vs-code, on va vérifier que ça a bien marché   
et pour ça, on vous dit de taper dans le terminal `code .`

mais en fait l'installation de vs-code modifie **la façon dont s'initialise** le terminal  
et du coup ça n'**affecte pas** les terminaux **créés avant** l'installation   

```{admonition} pensez-y !
:class: important
il faut donc prendre l'habitude de **lancer un nouveau terminal après une installation**  
```

ceci est notamment pertinent lorsque vous recevez une erreur comme  
`code: command not found`  
si ce symptôme persiste même après avoir essayé dans un nouveau terminal, c'est que l'installation s'est mal passée

````{admonition} le PATH (pour les curieux)
:class: dropdown note

le `PATH` c'est le mécanisme qui permet au terminal de trouver les commandes

et quand on installe un nouveau logiciel - comme on va le faire tout de suite avec
*git for windows* - il est souvent nécessaire de **modifier le `PATH`** pour que les nouvelles
commandes deviennent accessibles depuis le terminal

ce n'est pas crucial de le savoir, mais si vous êtes curieux, sachez que

* `PATH` c'est ce qu'on appelle une variable d'environnement (ça veut dire qu'elle se
  propage d'un processus à l'autre),

* que c'est une liste de répertoires où sont cherchées les commandes

  ```bash
  # un exemple sur linux/macos
  # le ':' est un séparateur
  $ echo $PATH
  /opt/conda/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
  ```

* et qu'elle est le plus souvent définie/modifiée dans un fichier caché qui s'appelle `.bashrc` dans votre homedir
* lorsque vous créez un nouveau terminal, celui-ci va **lire le contenu** de votre `.bashrc`  
  c'est pourquoi il **faut créer un nouveau terminal** pour tester une installation qu'on vient juste de faire

````

+++

### comment bien installer sur MacOS

sur Mac, quand vous installez une application - comme notamment vs-code:  
il est trés important **de copier l'application dans le dossier `Applications`** - on aura l'occasion d'en reparler

+++

## installation de git (et bash sur Windows)

suivez les instructions pour votre OS

+++

`````{admonition} Windows
:class: dropdown seealso

en installant ***git for windows*** on va faire d'une
pierre deux coups, et installer à la fois `bash` et `git`

* allez sur le site là  <https://gitforwindows.org/>
* téléchargez et lancez l'installation...
* vous pouvez prendre **toutes les options par défaut**

```{admonition} on peut prendre toutes les options par défaut
:class: dropdown tip

et entre autres, à la question ***Adjusting your PATH environment*** :  
choisissez au moins l'option recommandée (#2) - on peut prendre l'option (#3) si on veut importer plus d'outils dans le terminal, mais ce n'est pas strictement nécessaire pour le cours

![](media/fig-set-path-git-for-windows.png)
```

````{admonition} machine DSI / pas de droit administrateur ?
:class: smaller dropdown warning

le programme d'installation de *git for windows* est conçu pour installer le programme dans `C:\Program Files`,
qui peut nécessiter des **droits administrateur**; et malheureusement il ne propose pas de choisir un autre endroit...

aussi, si vous n'arrivez pas à installer *git for windows*, il va vous falloir lancer le programme d'installation "à la main" c'est-à-dire depuis un terminal;
voici la procédure à suivre dans ce cas:

* lancer un terminal *PowerShell* (on ne peut pas encore utiliser le terminal *bash* naturellement, puisqu'on ne l'a pas encore installé)
* trouver le nom de votre *homedir*; pour cela tapez
  ```bash
  cd
  pwd
  ```
  qui devrait vous répondre quelque chose qui contient votre nom, comme genre
  ```bash
  C:\Users\Jean Mineur
  ```
* se déplacer dans le dossier où vous avez téléchargé le programme d'installation (généralement `Downloads`)
  ```bash
  cd Downloads
  ```
* lancer le programme d'installation en ligne de commande en précisant un dossier d'installation **sous votre homedir**  
  à affiner selon le nom du fichier que vous avez téléchargé, mais ça ressemble à
  ```bash
  .\Git-2.34.1-64-bit.exe /DIR="C:\Users\Jean Mineur\GitForWindows"
  ```
````

`````

+++

`````{admonition} Mac et Linux
:class: dropdown seealso

sur ces deux OS, `bash` est **préinstallé**  
pour installer `git`, utilisez ce lien:  
<https://git-scm.com/book/fr/v2/D%C3%A9marrage-rapide-Installation-de-Git>

* rien de particulier à signaler sur linux, c'est sans doute déjà installé, et sinon c'est trivial
* par contre pour les Mac: **attention ça peut être long !!** la méthode recommandée passe par l'activation de Xcode, un peu de patience sera nécessaire..
  ````{admonition} Mac & Xcode
  :class: dropdown tip
  si vous optez pour la méthode "XCode", on vous dit de taper `git --version` pour déclencher l'installation de XCode; si cela vous affiche seulement un message d'erreur, vous pouvez aussi lancer l'installation de XCode directement depuis le terminal avec la commande suivante:

  ```bash
  xcode-select --install
  ```
  ````
`````

+++

`````{admonition} on vérifie bash (tous OS)
:class: important dropdown

vous devez pouvoir

* lancer un terminal `bash`
  ```{admonition} Windows
  :class: dropdown note
  
  cherchez *bash* dans le menu Démarrer  
  lancez l'application qui s'appelle *Git Bash*  
  n'hésitez pas à faire en sorte (*Pin to Taskbar*) que ce programme reste dans la barre des tâches même lorsqu'il est inactif; ça vous facilitera la vie...
  ```

* pour vérifier que c'est bien du `bash` - et pas du *PowerShell* par exemple, tapez
  ```bash
  echo $BASH_VERSION
  ```
  qui doit répondre
  ```bash
  5.2.15(1)-release        # c'est juste un exemple hein
  ```
  ````{admonition} zsh sur Mac
  :class: dropdown

  si vous avez un Mac, il se peut que votre terminal soit un `zsh` et pas un `bash`  
  ce n'est pas un souci, les deux outils sont très largement compatibles !  
  pour savoir quel est exactement votre shell, vous pouvez faire  
  ```console
  echo $SHELL
  ```
  ````
`````

+++

````{admonition} on vérifie git (tous OS)
:class: important dropdown

* pour vérifer que vous avez bien installé `git`:
  ```bash
  $ git --version
  git version 2.41.0       # pareil, la réponse peut être différente chez vous
  ```
  **remarque**  
  dans cette forme, le `$` signifie que j'ai tapé `git --version`  
  et que ça m'a répondu `git version 2.41.0`  
  c'est pour abréger un peu  
  pensez bien à **ne pas taper le `$` vous même**  
  car bien sûr ça va marcher beaucoup moins bien si vous le faites ;)

* si vous n'avez pas **au moins la version 2.23**, faites-vous connaitre; le mieux serait de mettre à jour pour obtenir une version plus récente, car certains éléments du cours sur git ne vont pas fonctionner chez vous...
````

+++

### exercice: le dossier `cours-info`

`````{admonition} pas à pas
:class: note dropdown

depuis le terminal on peut tout faire ! et pour commencer on va apprendre à **créer un dossier**  
c'est dans ce dossier qu'on vous invite à travailler pendant les cours d'info

* créez un nouveau terminal
* **regardez dans quel dossier vous êtes**
  ```bash
  pwd
  ```
  qui devrait vous répondre quelque chose qui contient votre nom, comme genre
  ```bash
  # sur Windows
  /c/Users/Jean Mineur
  # sur Mac / Linux
  /Users/jeanmineur
  ```
  c'est votre *home directory*, en abrégé *homedir*

  ````{admonition} ce n'est pas le cas ?
  :class: attention dropdown
  si vous vous trouvez dans un dossier bizarre (qui n'a rien à voir avec votre nom), 
  prenez l'habitude de commencer par forcer le terminal à aller dans votre homedir en faisant simplement
  ```bash
  cd
  ```
  ```{admonition} à quoi ça sert ?
  :class: note dropdown

  sur mac et linux, c'est optionnel car le terminal démarre justement dans le homedir; c'est le comportement normal  
  par contre selon les configurations sur Windows, il peut être nécessaire de prendre l'habitude de faire un premier `cd` au début du terminal, car dans certains setups le terminal démarre dans un autre dossier...
  ```
  ````

* **créez un dossier `cours-info`**
  ```bash
  mkdir cours-info
  ```
  bien entendu il ne faut le faire qu'une seule fois :)

* **allez dans ce nouveau dossier**
  ```bash
  cd cours-info
  ```
  éventuellement refaites `pwd` pour constater que vous avez changé de dossier

* maintenant ouvrez votre **explorateur de fichiers**, et déplacez-vous dans ce même dossier
  à ce stade vous devez constater que le dossier est bien créé, et qu'il est bien vide
  ```{admonition} on peut créer un raccourci
  c'est important car c'est une opération qu'on **va faire très souvent**;  
  on verra plus tard comment créer, dans l'explorateur de fichiers, [un raccourci pour pouvoir faire ça rapidement](#label-raccourci-cours-info)...
  ```
`````

+++

## installation de vs-code

nous demandons à **tous** les élèves d'installer et de savoir utiliser vs-code  
il s'agit d'un **éditeur de code**, c'est ce qu'on va utiliser pour écrire nos programmes  

````{admonition} pas de pyzo
:class: error

il y a eu **beaucoup de problèmes** les années passées avec les éditeurs de type *pyzo*  
ne les utilisez surtout pas dans nos cours, vous allez perdre un temps précieux et en faire perdre à vos enseignants pour des raisons inintéressantes, et extérieures à Python
````

+++ {"jp-MarkdownHeadingCollapsed": true}

````{admonition} installation (toutes plateformes)
:class: seealso dropdown

On y va. Le site est là <https://code.visualstudio.com/>.  
Vous voulez installer donc il va falloir que vous alliez dans une section *download* ... vous la voyez ?  
à vous de jouer maintenant

```{admonition} Windows: toutes les option par défaut
:class: seealso dropdown

pour les Windows, à nouveau vous prenez **toutes les options par défaut**
```

```{admonition} pour les Mac: déplacez dans le dossier Applications !
:class: warning dropdown

**Attention**  

on l'a signalé déjà rapidement, mais la bonne façon d'installer une appli sur MacOS en général est de la glisser-déplacer dans le dossier `Applications`  

aussi une fois que vous aurez téléchargé, et double cliqué sur le zip, vous allez voir un fichier de type `.app`, **qui se trouve dans votre dossier `Downloads`**  
**il est impératif** de glisser-déplacer ce fichier dans le dossier `Applications`  
si on ne le fait pas, ça semble fonctionner, mais on a des tas de problèmes assez retors par la suite

```
````

+++ {"jp-MarkdownHeadingCollapsed": true}

`````{admonition} on vérifie l'installation de vs-code
:class: important dropdown

* si le programme d'installation a lancé un exemplaire de vs-code, fermez-le

* dans **un nouveau terminal** (voir + haut)  
  ```bash
  code --version
  ```
  qui doit afficher un numéro de version (et d'autres détails, par exemple
  ```bash
  1.84.2
  1a5daa3a0231a0fbba4f14db7ec463cf99d7768e
  x64
  ```

  ````{admonition} command not found ?
  :class: dropdown note

  si à la place vous voyez  
  ```bash
  code: command not found
  ```
  d'abord vérifiez que vous avez bien essayé **dans un nouveau terminal** (oui je sais...)  
  et sinon [allez voir cette page](#label-troubleshoot-code-command-not-found)
  ````

* lorsque ça fonctionne, prenez l'habitude de lancer vs-code comme ceci
  ```bash
  # first I want to choose in which folder I am going to work
  cd 
  cd cours-info
  code .
  ```

* et tant que vous y êtes, **activez le mode *Auto Save***:  
  ⮑ dans le menu *File*, cliquez sur *Auto Save* (ça ajoute une check mark)  
  l'effet de ce réglage est que vos modifications sont sauvées toutes seules, pas besoin de *Control-S* sans arrêt !

* pour ceux qui sont en avance, amusez-vous à créer un fichier:
  * Control-n (ou Command-n sur mac) pour créer un nouveau fichier
  * Control-s (sur mac c'est toujours Command-truc) pour indiquer dans quel fichier le sauver, disons `foo.txt`
  * écrivez une ligne ou deux
  * quittez vs-code
  * vérifiez la présence du nouveau fichier
    * depuis l'explorateur de fichiers
    * et aussi depuis le terminal, où vous pouvez utiliser `cat foo.txt` pour afficher le contenu que vous venez de taper
`````

+++

## installation de miniconda / Python

* il y a de très nombreuses distributions de Python disponibles
* notre choix : **miniconda**, parce que
  * il est relativement léger
  * il permet d'installer en mode "user", c'est-à-dire sans droits administrateur
  * il permet également de fabriquer des *environnements virtuels*
    (pas de panique, on n'utilisera pas ça tout de suite, mais c'est une possibilité qui devient vite intéressante)

* ça va sans dire, mais ne prenez **surtout pas Python 2.7** !

+++

```````{admonition} Windows
:class: seealso dropdown

``````{div}

`````{admonition} préparation
:class: seealso dropdown

````{div}
une première précaution, spécifique à Windows:  
il s'agit de contourner un bug dans l'installateur conda, qui se déclenche lorsqu'il y un caractère exotique (accent, cédille, ...) dans le nom du dossier d'installation; ce qui peut se produire si vous en avez dans votre nom !

du coup, nous allons pour commencer créer un dossier dont le nom est court et simple,
et **qui ne contient pas d'accent**, pour pouvoir y installer miniconda sans rencontrer ce bug

pour cela nous allons lancer la console Windows qui s'appelle `PowerShell`, et créer le
dossier `c:/miniconda`

en deux étapes, ça se présente comme ceci :

1. pour lancer la console `PowerShell`

```{image} media/fig-miniconda-powershell-locate.png
:width: 600px
```

2. on va créer maintenant le dossier dans lequel on installera ensuite miniconda,
et pour cela il y a une seule ligne à taper

```console
md c:/miniconda
```

```{image} media/fig-miniconda-powershell-md.png
:width: 600px
```

une fois la commande tapée vous pouvez sortir de PowerShell (utiliser la croix en haut à
droite par exemple)
````
`````



`````{admonition} download
:class: seealso dropdown

````{div}
commencez par [aller sur la page de downloads de miniconda](https://docs.conda.io/projects/miniconda/en/latest/#latest-miniconda-installer-links) qui ressemble à ceci

```{image} media/fig-miniconda-download.png
:width: 600px
```

puisqu'on est sur Windows, on n'a pas le choix, téléchargez le `*.exe`  
(avant de le lancer, voyez l'étape suivante pour les réponses aux questions...)
````
`````



`````{admonition} les réponses aux questions
:class: seealso dropdown

````{div}
vous lancez le `.exe`  
et vous prenez les options par défaut lorsqu'on vous pose une question  
**sauf pour les écrans qui suivent**:

* ***Install for:*** (si la question vous est posée)   
  répondez *Just me (recommended)*

  ```{image} media/fig-miniconda-just-me.png
  :width: 600px
  ```

  <div style="height: 0.5cm"></div>

* **le choix du dossier où installer**  
  sur cet écran vous remplacez le chemin qu'on vous propose par défaut, et vous
  choisissez à la place le dossier qu'on a créé dans l'étape précédente, c'est-à-dire
  `c:\miniconda`

  ```{image} media/fig-miniconda-set-install-dir.png
  :width: 600px
  ```

  <div style="height: 0.5cm"></div>

* **advanced options: *add to my PATH environment variable***  
  il est important de **bien cocher la case ci-dessous** (malgré l'avertissement en rouge)

  ```{image} media/fig-miniconda-add-path.png
  :width: 600px
  ```
````

````{admonition} pas coché la case ?
:class: dropdown 

si par mégarde vous êtes allé jusqu'au bout sans cocher cette case, [voyez cette page](#label-troubleshoot-python-command-not-found)
````
`````
``````
```````

+++

```````{admonition} MacOS
:class: seealso dropdown

``````{div}

`````{admonition} préparation: Intel ou M1 ?
:class: seealso dropdown

````{div}
c'est important que vous sachiez dire si votre Mac a une puce Intel ou M1 (en fait pour l'installation miniconda, M1 ou M2 c'est pareil..)  
et pour ça c'est simple, il suffit d'ouvrir le menu Pomme -> *About This Mac* où vous trouver l'information ici

```{image} media/fig-macos-about.png
:width: 600px
```
````
`````


`````{admonition} download
:class: seealso dropdown

````{div}
commencez par [aller sur la page de downloads de miniconda](https://docs.conda.io/projects/miniconda/en/latest/#latest-miniconda-installer-links) qui ressemble à ceci

```{image} media/fig-miniconda-download.png
:width: 600px
```

vous téléchargez **la seule entrée de type `.pkg`** qui correspond **à votre architecture**  
une fois le download terminé, vous double-cliquez sur le `.pkg`  
il n'y a pas de choix particulier où on pourrait se tromper..
````
`````
``````
```````

+++

```````{admonition} Linux
:class: seealso dropdown

``````{div}
`````{admonition} download
:class: seealso dropdown

````{div}
commencez par [aller sur la page de downloads de miniconda](https://docs.conda.io/projects/miniconda/en/latest/#latest-miniconda-installer-links) qui ressemble à ceci

```{image} media/fig-miniconda-download.png
:width: 600px
```

vous téléchargez **la première entrée pour Linux** (`Linux 64-bit`), les autres correspondent à des architectures différentes de celles qu'on trouve usuellement sur un ordi personnel
````
`````


`````{admonition} pour lancer l'installation
:class: seealso dropdown

````{div}
```bash
# just in case: go back to homedir
cd 
# go to the folder where download has ended up
cd Downloads
# making sure: list files that start with 'Miniconda3'
ls Miniconda3*
# very probably you will see only one file here, named 
# Miniconda3-latest-Linux-x86_64.sh
# (unless of course you download several times..)
#
# in any case, the way to actually run such a program is

bash Miniconda3-latest-Linux-x86_64.sh
```

les questions/réponses se passent dans le terminal, voici quelques trucs utiles:

- pendant le *License Agreement* on vous faire lire les conditions de la licence
  - pour avancer dans le document tapez *Espace*
  - pour abréger, tapez simplement *`q`*
- à la question  
  `Do you wish to update your shell profile to automatically initialize conda?`  
  on recommande de répondre `yes`
````
`````
``````
```````

+++

`````{admonition} on vérifie conda et python
:class: important dropdown

et on fait quoi pour vérifier ? on crée un **nouveau terminal** !

````{admonition} le prompt (rappel)
:class: dropdown

* le signe `$ ` **ne fait pas partie** de ce que vous devez taper
* c'est juste une indication pour dire que la commande s'adresse au terminal  
  c-à-d à nouveau : GitBash sur Windows, Terminal sur MacOS,  
  et n'importe quel terminal bash sur linux

ça signifie que vous **n'avez pas à taper le `$`**, ce
sera déjà affiché lorsque vous taperez vos commandes
````

````{admonition} la commande conda
:class: important dropdown

vous créez un nouveau terminal, et vous tapez
```bash
$ conda --version
conda 23.5.2
```
qui **ne doit pas** vous répondre `command not found`  
si c'est le cas, c'est que vous n'avez pas bien coché la case  
*Add Miniconda3 to my PATH environment variable*  
[dans ce cas voyez ici](#label-troubleshoot-python-command-not-found)

````

````{admonition} version de python
:class: important dropdown

pour savoir la version de python installée
```bash
$ python --version
Python 3.11.4
```
vous **devez** avoir une version 3.x, et **surtout pas** 2.7
````
  
````{admonition} quel python ? (optionnel)
:class: important dropdown

pour savoir quelle version de `python` est utilisée, vous pouvez taper
```console
$ type python
```
qui doit vous répondre quelque chose comme
```console
# sur Windows avec notre setup vous devez avoir
python is /c/miniconda/python
# sur Mac par exemple je vois 
python is /c/Users/JeanMineur/miniconda3/python
```
````

`````

+++

### exercice: vs-code + python

````{admonition} pas à pas
:class: dropdown note

* créer un nouveau terminal
* aller dans le dossier `cours-info` (on fait comment déjà ?)
* lancez vs-code
  ```bash
  code .
  ```

* copiez-collez le code ci-dessous dans un fichier qui s'appelle `fact.py`
  ```python
  # une fonction qui calcule factorielle
  def fact(n):
      return 1 if n <= 1 else n * fact(n-1)


  # on affiche quelques résultats
  for n in [4, 25]:
      print(f"fact({n}) = {fact(n)}")
  ```
  ```{admonition} quelques trucs
  :class: tip dropdown

  utilisez les raccourcis clavier (remplacer Control par Command sur Mac)

  * Control-N: créer un nouveau fichier
  * Control-S: sauver le nouveau fichier, et lui donner un nom si nécessaire
  * Control-A Control-C Control-V: comme d'habitude pour le copier-coller
  ```

* exécutez le programme
  ```bash
  $ python fact.py
  fact(4) = 24
  fact(25) = 15511210043330985984000000
  ```
````

+++

## installation des extras Python

c'est-à-dire:
- numpy + pandas + matplotlib
- ainsi que IPython + Jupyter

````{admonition} installation numpy et jupyter
:class: seealso

voici un bloc de commandes que vous pouvez copier-coller **dans le terminal**  
pour faire en un seul coup toutes les installations dont on aura besoin

par contre cela peut prendre un moment...

  (label-config-jupytext)=
  ```bash
  # c'est avec pip install qu'on installe quasiment tout pour Python
  pip install numpy pandas matplotlib
  pip install ipython jupyter
  pip install jupytext jupyterlab-myst
  jupytext-config set-default-viewer
  ```
````

```{admonition} à quoi servent Jupyter et Jupytext ?
:class: note dropdown

le cours est écrit sous forme de notebooks Jupyter, dans un format textuel (ici du markdown) grâce à Jupytext

de manière générale vous aurez le choix entre 

* lire le cours en HTML (comme ce premier cours), 
* ou de l'exécuter sous forme de notebook en lançant Jupyter sur votre ordi; on en reparlera
```

````{admonition} à quoi sert jupytext-config ?
:class: note dropdown

en l'absence de cette dernière commande, depuis Jupyter vous pouvez toujours ouvrir les notebooks jupytext ,
mais il faut passer par *Clic droit* → *Open with* → *Notebook*  
une fois que vous aurez exécuté la commande ci-dessus, vous pourrez ouvrir les notebooks
simplement en double-cliquant dessus
````

`````{admonition} on vérifie numpy et jupyter
:class: important dropdown

````{admonition} version de ipython et numpy
:class: seealso dropdown

lancez `ipython` et tentez de reproduire cette session  
vous ne devez pas avoir d'erreur du type `ModuleNotFound`

```bash
$ ipython
Python 3.11.4 | packaged by conda-forge | (main, Jun 10 2023, 18:10:28) [Clang 15.0.7 ]
Type 'copyright', 'credits' or 'license' for more information
IPython 8.14.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: import numpy

In [2]: print(numpy.__version__)
1.26.0

In [3]: exit()
$
```
````

````{admonition} version de jupyter
:class: seealso dropdown

de retour dans le terminal, affichez les versions des composants de Jupyter avec cette commande  
vous ne devez pas avoir de `command not found`
```bash
jupyter --version
```
````

````{admonition} les modules installés avec pip (optionnel)
:class: seealso dropdown

```bash
# pour obtenir la liste des librairies installées
# (possiblement beaucoup)
pip list
# pour voir la version installée de UNE librairie, par exemple
pip show numpy
```
````

`````

+++

### configuration de l'autoreload

````{admonition} autoreload
:class: seealso

copiez-collez ceci dans votre terminal

```bash
mkdir -p ~/.ipython/profile_default
cat >> ~/.ipython/profile_default/ipython_config.py << EOF
c.InteractiveShellApp.exec_lines = []
c.InteractiveShellApp.exec_lines.append('%load_ext autoreload')
c.InteractiveShellApp.exec_lines.append('%autoreload 2')
EOF
```
````

`````{admonition} à  quoi ça sert ?
:class: note dropdown

**le problème**: vous êtes dans `ipython` ou dans un notebook, et vous faites

```python
from my_module import my_function
my_function(...)
```

et puis ensuite un peu plus tard, vous modifiez `my_module.py` sous vs-code, et vous
voulez essayer la nouvelle version; votre première idée est de refaire l'import pour
recharger le module dans l'interpréteur

MAIS là attention, **un second `import` ne recharge pas le fichier** ! c'est le
comportement attendu, et souhaitable, car charger un module est coûteux; c'est
pourquoi l'interpréteur garde en mémoire les modules qu'il a déjà chargés, et du
coup vous pouvez ré-importer autant que vous voulez, vous allez toujours utiliser
le premier code, et non ce que vous venez de modifier !

**la solution**: avec cette astuce, vous n'aurez plus besoin de ré-importer,
vous pourrez juste ré-exécuter `my_function()` et vous utiliserez la dernière
version du module (pour autant que le nouveau module ne contienne pas d'erreur qui
empêche son chargement, bien entendu)

````{admonition} comment ça marche ?
:class: dropdown note

pour les curieux qui veulent comprendre, le script est en bash:

* il commence par s'assurer que le dossier `.ipython/profile_default` existe sous le home directory
* puis dans ce dossier, il ajoute dans le fichier `ipython_config.py` les 3 lignes de configuration qui précèdent le `EOF` (c'est du Python bien sûr); le fichier est créé s'il n'existait pas
````
`````

+++

### exercice: mon premier notebook (optionnel)

````{admonition} pas à pas
:class: dropdown

* créez un nouveau terminal
* allez dans `cours-info`
* tapez la commande `jupyter lab`
  cela doit ouvrir un nouvel onglet dans votre navigateur
  dans lequel tourne l'application Jupyter
  et le terminal devient inutilisable

* menu *Jupytext* -> *New Text Notebook* -> *Markdown MyST*
* renommez le nouveau fichier, qui a été créé sous le nom `Untitled.md`, en `mon-premier-notebook.md`
* dans la première cellule vous mettez le code de la fonction `fact()` (voir + haut)
* calculez différentes valeurs de `fact()` dans les cellules suivantes
* créez une cellule markdown et voyez ce que ça donne
  * les styles gras, italique, code, etc..
  * les listes à bullet
  * les titres
  * etc...
* (option)  dans une autre cellule markdown vous insérez une ou des équations $\LaTeX$, j'invente:
  $$
  \forall c \in \mathbb{C}^3-{1}, \exists c' \in \mathbb{C}^3, \phi(c') = \frac{c^2+1}{c-1}
  $$

* sortez de JupyterLab en faisant *File* -> *Shutdown*
* vous retournez dans le terminal qui maintenant fonctionne à nouveau

````

+++

## configuration git

avant de pouvoir utiliser git, il nous faire un minimum de configuration

c'est **très important** de bien **suivre toutes ces consignes**, 
ou alors vous risquez de sérieusement galérer plus tard…

+++

````{admonition} votre identité
:class: seealso

pour commencer vous devez configurer git pour qu'il connaisse votre identité, cela sera utilisé à chaque fois que vous faites un *commit*

  ```bash
  # remplacez ici vos nom et prénom et mail
  git config --global user.name "Jean Mineur"
  git config --global user.email jean.mineur@etu.minesparis.psl.eu
  ```
````

+++

(label-vscode-for-commit)=
``````{admonition} les autres réglages
:class: seealso`

à copier-coller tel quel dans le terminal
  ````bash
  # peut être copié tel quel
  git config --global core.editor "code --wait"
  git config --global init.defaultbranch main
  git config --global pull.rebase false
  git config --global alias.l "log --oneline --graph"
  git config --global alias.la "log --oneline --graph --all"
  git config --global alias.s "status"
  ````

````{admonition} à quoi ça sert ?
:class: note dropdown

* avec `core.editor` on choisit vs-code comme éditeur (voir ci-dessous)
* avec `init.defaultbranch` on indique que la branche initiale s'appelle `main`
* avec `pull.rebase` on indique qu'on veut *merge* et non pas *rebase* lorsqu'on *pull*
* avec les trois `alias` on définit des raccourcis; c'est comme ça par exemple qu'on pourra taper simplement  
  `git la`  
  au lieu de devoir taper  
  `git log --oneline --graph --all`
````

`````{admonition} pour utiliser vs-code avec git
:class: dropdown note

````{div}
à chaque commit est associé **un message**, et git a besoin de savoir **quel éditeur de code** vous voulez utiliser pour entrer ce message

dans notre cas nous allons utiliser **vs-code**, et c'est le propos du réglage qui s'appelle `core.editor`

```{admonition} terminer la rédaction du message
:class: attention

lorsque vous faites par exemple `git commit` et que l'éditeur se lance pour vous laisser entrer le message, le programme dans le terminal **attend que vous ayez fini** d'entrer le message  
et pour lui dire "ça y est, j'ai fini, on peut finaliser le commit", ce que vous devez faire, c'est:
- il ne suffit pas de simplement sauver le fichier (c'est nécessaire bien sûr, mais pas suffisant)  
- ce qui compte c'est que vous ***fermiez l'onglet qui édite le message***;
vous pouvez utiliser par exemple `Control-W` (ou Command-W sur mac); ou encore utiliser la petite croix en x à droite de l'onglet
- ce n'est **pas la peine** de terminer toute votre session vs-code (vous pouvez avoir plein d'autres fichiers ouverts à ce moment-là dans vs-code)
```
````
`````

````{admonition} command not found ?
:class: note dropdown
  
pour que ça fonctionne, il faut bien sûr que la commande `code` soit bien installée dans votre PATH; si vous avez `command not found` quand vous tapez `code .` dans votre terminal, [reportez-vous à la section sur ce problème](#label-troubleshoot-code-command-not-found)
````
``````

+++

`````{admonition} on vérifie: mon premier commit (optionnel)
:class: important dropdown

voici un petit scénario qui vous fait créer un dossier, un repo git, un fichier, et un commit; toutes les commandes sont à taper dans le terminal (bash bien sûr)

  ````bash
  # je repars de mon homedir
  cd
  # je vais dans le dossier cours-info
  cd cours-info
  # je crée un nouveau dossier 
  mkdir my-first-git-repo
  # je vais dedans
  cd my-first-git-repo
  # j'initialise ce dossier comme un repo git
  git init
  # je lance l'éditeur de code
  code .
  
  # à ce stade, dans vs-code, créez le fichier `readme.md`
  # avec une ou deux lignes de texte, sauvez-le
  # puis retournez dans le terminal:

  # on veut que readme.md soit dans le commit qu'on va créer
  git add readme.md
  git commit

  # à ce stade, vous devez voir une fenêtre s'ouvrir dans vs-code
  # allez-y, tapez un message sur la première ligne
  # (par exemple `mon premier commit`), 
  # puis faites `Control-S` suivi de `Control-W`
  # (ou Command-S suivi de Command-W sur mac)

  # et là si tout se passe bien: 
  # la fenêtre dans vs-code se ferme, 
  # et si vous retournez dans le terminal
  # vous voyez que le `git commit` est terminé

  # on peut alors continuer, et faire
  git log

  # qui doit vous montrer UN commit; vérifiez
  # que votre nom et mail est correct
  # et que la branche s'appelle bien `main`
  ````

`````

+++

## github et la clé SSH

depuis Août 2021, il est devenu très compliqué d'utiliser la méthode dite 'HTTPS' pour s'authentifier chez github;  
aussi nous allons ensemble voir comment créer une clé pour la méthode SSH

### compte github

pour commencer, créez-vous un compte sur github si ce n'est pas déjà fait

+++

### c'est quoi SSH ?

au départ, c'est un système de terminal distant pour pouvoir administrer les serveurs à distance; l'authentification est basée sur le principe d'une paire de clés publique/privée

sans entrer dans les détails, ces deux morceaux sont en gros **deux éléments symétriques** l'un de l'autre dans un très gros groupe fini, et on ne peut pas facilement calculer l'un à partir de l'autre  

par définition:

* la clé publique peut être divulguée sans aucun souci au monde entier
* par contre **la clé privée** doit être gardée secrète, donc **jamais exposée/copiée** en dehors de votre ordi

et donc, ce qu'on va faire tout simplement, c'est:

* générer une paire de clés
* et déposer une copie de la clé publique sur github, en l'associant à votre compte github

+++

``````{admonition} création de la paire de clés
:class: seealso dropdown

pour générer la clé publique vous faites simplement dans le terminal
```bash
ssh-keygen -t rsa
```

ce programme va vous poser des questions, à ce stade je vous recommande de toujours **répondre par simplement la touche *Entrée***, pour accepter les défauts et ne pas attacher de mot de passe votre clé privée (ce qui n'est pas une pratique hyper-sûre, mais à ce stade de votre cursus ça parait raisonnable; si vous êtes geek et/ou très soucieux de sécurité, mettez un mot de passe mais soyez prêt à taper votre mot de passe *ad nauseam*, ou à passer du temps à des configurations scabreuses pour ne pas avoir à le faire...)
`````{admonition} ça ressemble à ceci
:class: dropdown
````{div}
vous n'aurez pas *exactement* les mêmes messages, mais pour que vous ne soyez pas surpris voici *en gros* à quoi vous attendre comme session
```{image} media/ssh-keygen.png
:align: center
:width: 400px
```
````
`````
``````

+++

``````{admonition} affichage de la clé publique
:class: seealso dropdown

`ssh-keygen` va avoir pour effet de créer deux fichiers situés dans le dossier `~/.ssh`  
(le tilda signifie: directement sous votre homedir)  

du coup vous affichez le contenu de la clé publique en faisant maintenant

```bash
# pensez à copier-coller
# si vous ne trouvez pas le ~ sur votre clavier

cat ~/.ssh/id_rsa.pub
```

et vous copiez tout le contenu (en incluant bien tout, même le `ssh-rsa` et tout)
`````{admonition} ça ressemble à ceci
:class: dropdown
````{div}
de nouveau, pour que vous ne soyez pas surpris voici *en gros* à quoi vous attendre comme session
```{image} media/ssh-copy-key.png
:align: center
:width: 400px
```
````
`````
``````

+++

`````{admonition} attachez la clé à votre compte github
:class: seealso dropdown

````{div}

maintenant vous allez sur github:

1. dans le coin en haut à droite il y a votre icône  
2. qui ouvre un sous-menu dans lequel vous choisissez *Settings*  
3. dans la partie gauche de la page qui s'ouvre, cliquez 'SSH and GPG Keys'

```{image} media/github-profile-1.png
:width: 600px
:align: center
```

et là vous pouvez ajouter votre clé publique SSH:

1. mettez ce que vous voulez comme titre
2. mais vous collez la clé publique dans la zone qui va bien

```{image} media/github-profile-2.png
:width: 600px
:align: center
```
````
`````
