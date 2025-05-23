---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Calysto Bash
  language: bash
  name: calysto_bash
language_info:
  help_links:
  - text: MetaKernel Magics
    url: https://metakernel.readthedocs.io/en/latest/source/README.html
  name: bash
---

Licence CC BY-NC-ND, Thierry Parmentelat & Valérie Roy

```{code-cell}
:tags: [raises-exception]

%%python
from IPython.display import HTML
HTML(filename="_static/style.html")
```

# le terminal

le premier outil que nous allons voir c'est ce qu'on appelle le terminal;  
un terminal qu'est-ce que c'est ?

> le terminal c'est tout simplement un *process* (programme) qui permet de lancer d'autres *process*

+++

## mais pourquoi ne pas juste cliquer ?

ça peut paraitre moins pratique que de cliquer sur les icones du bureau... **mais** en fait c'est **beaucoup plus puissant** !

* d'abord c'est un peu comme un langage de programmation, on peut faire **en une ligne** ce qui prendrait **des heures avec un cliquodrome** !
* et aussi on va pouvoir **passer des paramètres** aux programmes - [voir par exemple avec vs-code](#label-vscode-parameter)
* enfin c'est de cette manière qu'on accède à des ressources distantes (cloud, cluster de calcul, ...)

+++

## `bash`

il y a plein de types de terminal selon les systèmes d'exploitation  
mais pour que nous travaillions tous ensemble sur le même objet, nous avons **choisi un terminal** qui
s'appelle ``bash``

* `bash` vient avec l'installation de base sur MacOS et linux
* sur Windows, il faut l'installer séparément, on l'a vu avec ***git for
  windows***

+++

## dossiers et fichiers

comme vous le savez, le contenu du disque dur est organisé en **dossiers** et **fichiers**  
le **dossier** est juste un cas particulier de fichier, qui **contient d'autres fichiers** (ou dossiers, donc) - au lieu de contenir des données

````{admonition} termes synonymes :

* dossier = répertoire = *folder* = *directory*: c'est tout pareil
* fichier = *file*: idem, ce sont des synonymes
````

+++

### dossier utilisateur (*home directory*)

chaque utilisateur possède un **dossier privilégié** (on dit aussi parfois répertoire),  
qui est **la racine** de l'arbre dans lequel il peut ranger ses affaires  
**indépendamment** des fichiers propres au système d'exploitation

pour y aller le plus simple est de faire simplement `cd` sans paramètre

```bash
# pour aller dans mon homedir, je fais juste ceci

cd
```

````{admonition} rappels à propos du prompt
:class: admonition-small dropdown attention

la plupart du temps on ne montrera plus le `$` qui est affiché par le terminal (le *prompt*),  
ça permet notamment de simplifier le copier-coller depuis le support de cours vers le terminal
````

```{admonition} nouveau terminal

en principe, un terminal qui vient d'être créé **commence dans le home directory**  
c'est toujours le cas sur MacOS et Linux  
toutefois sur Windows, en pratique ce n'est pas toujours le cas en fonction de votre setup  
aussi **si vous êtes dans ce cas-là**, prenez l'habitude de faire `cd` avant toute chose dans le terminal
```

```{code-cell}
# sans paramètre je vais tout en haut de mon espace
# c'est mon home-directory

cd
```

### dossier courant

tous les programmes (processus) ont ce qu'on appelle un **dossier courant**  
dans le terminal on peut le voir avec **la commande `pwd`** comme ceci

```{code-cell}
# pour voir où il est
# pwd = print working directory

pwd
```

### une petite session

commençons par une petite promenade dans le contenu de ce cours  
je suppose que vous l'avez déjà cloné, [sinon retournez à cette section pour le faire](#label-clone-course)

je vous invite à expérimenter tout ceci dans votre propre terminal (et sans taper les `$ ` évidemment) :

`````{admonition} screenshot
:class: note

````{div}
```{image} media/fig-bash-relative-paths.png
:width: 750px
```
````
`````

`````{admonition} à noter sur cet exemple
````{div}

* la commande `ls` permet d'afficher le **contenu d'un dossier** - ou de vérifier si un fichier existe
* une fois que je change de dossier en allant dans `demo/python`, je ne **trouve plus** le fichier `README.md`  
  if faut que je dise bien qu'il est en fait **deux étages plus haut**  
  en indiquant `../../README.md` (car `..` signifie : le dossier parent)

* je peux faire tourner le programme `fact.py` **sans précider le dossier** de `fact.py`  
  car il est dans le **même dossier que moi**

* je *peux aussi* bien sûr lancer le même programme en donnant son **chemin absolu**  
  remarquez que cette forme marcherait alors quel que soit mon dossier courant !

* remarquez enfin que le programme `python` a été trouvé comme étant en fait `/c/miniconda/python`
  c'est grâce à cette fameuse variable `PATH` que le programme d'installation de conda a modifiée pour nous
````
`````

+++

### chemins relatifs et absolus

+++

````{admonition} à quoi ça sert d'avoir un dossier courant ?

en fait c'est uniquement une **commodité** pour ne pas avoir à retaper le chemin complet depuis la
racine des dossiers  

par exemple dans la session juste au dessus, on a vu qu'on pouvait faire, de manière équivalente:

- `python fact.py`
- `python /c/Users/Jean\ Mineur/cours-info/intro/demo/python/fact.py`

et cela bien sûr parce qu'on est dans le dossier `/c/ bla bla /python`
````

````{admonition} chemin relatif / chemin absolu
- quand un chemin commence par un `/` on dit que c'est un **chemin absolu**  
  parce qu'il se comprend à partir de la racine du disque - `/` 
- sinon c'est un **chemin relatif** - comme `fact.py`  
  parce qu'il se comprend **par rapport** au dossier courant
````

+++

(label-bash-dot)=
### `.` et `..`

on nous donne deux outils pour naviguer dans l'arbre des fichiers; par convention:

* `.` désigne le répertoire courant
* `..` désigne le répertoire "au dessus" du répertoire courant  
  on l'utilise pour fabriquer des chemins du genre de
  ```bash
  ls ../frere/neveu
  ```
  
````{admonition} exemples
- dans la session de tout à l'heure on a fait à un moment
  ```bash
  ls ../../README.md
  ```
  pour voir le fichier qui se trouve à la racine du cours, alors qu'on était descendu dans `demo/python`
- pour lancer *vs-code*, on le fait presque toujours en tapant
  ```bash
  code .
  ```
  ce qui signifie: lancez le programme `code` **dans le dossier courant**  
  (techniquement, en lui passant en paramètre le dossier courant)
````

+++

### `cd -`

````{admonition} pour revenir en arrière (avancé)
:class: dropdown

enfin, une astuce utile c'est pour **revenir en arrière** avec `cd -`  
avec cette commande, vous retournez au dossier où vous étiez avant le dernier `cd`

```bash
$ pwd
/c/Users/Jean Mineur
$ cd cours-info/intro
$ pwd
/c/Users/Jean Mineur/cours-info/intro
$ cd -
$ pwd 
/c/Users/Jean Mineur
$ cd - 
$ pwd
/c/Users/Jean Mineur/cours-info/intro
```
````

+++

## astuces & conseils

un peu en vrac, quelques conseils généraux pour bien utiliser votre ordi

+++

### la complétion

ce qu'on appelle **complétion**, c'est la capacité d'un outil à vous aider à taper votre code, en complétant **la phrase que vous avez commencée**

exemple :

* vous lancez un terminal, et si nécessaire vous allez dans votre home-directory
* à cet endroit il y a en principe un dossier qui s'appelle `cours-info`  

  ```bash
  # vous tapez
  $ cd cours-
  # à ce stade-là, vous tapez sur la touche 'Tabulation` - parfois représentée avec le signe ⇥
  # et s'il n'y a qu'un nom de fichier qui commence comme cela, vous obtenez magiquement
  $ cd cours-info/
  ```

````{admonition} partout et tout le temps

la complétion est un outil **indispensable** pour ne pas perdre un temps précieux !  
ça marche avec **presque tous les outils** (pas seulement dans le terminal)  

apprenez à la maitriser, entrainez-vous à vous déplacer dans le dossier du cours, sans taper l'intégralité des noms de dossier
````

+++

### un raccourci vers `cours-info`

le *homedir*, c'est une racine tentante pour mettre ses affaires, mais souvent il y a pas
mal de fourbis dès le départ  
sur Windows par exemple si vous regardez son contenu
(faites-le !), vous verrez que c'est pas mal encombré

c'est pourquoi on vous a demandé de créer un dossier `cours-info` dans lequel on va ranger vos différents dossiers:  
chaque cours dans un repo, puis au besoin un dossier par exercice ou TP ou hackaton, etc...

(label-raccourci-cours-info)=
je vous recommande de passer 5 minutes pour ajouter ce dossier dans les **raccourcis de votre explorateur de fichiers**  
de cette façon vous y aurez un accès direct en un clic, comme ceci  
(ici sur Windows, mais c'est une *feature* disponible sur tous les OS)

```{image} media/fig-quick-access-cours-info.png
:width: 750px
```

+++

### ne pas abuser sur la profondeur des arbres  

vous pouvez bien sûr décider de mettre le `cours-info` où vous voulez dans votre ordi, mais 
dans tous les cas, évitez de couper les cheveux en 4 en créant plein de sous-répertoires, genre :

~~`/c/Users/Jean\ Mineur/Desktop/mines/première-année/info/ue12/cours-info`~~

au contraire il est préférable de se limiter à une profondeur "raisonnable", c'est bien plus pratique à l'usage...

+++

### noms de fichiers simples

c'est assez facile (avec l'explorateur de fichiers notamment) de créer des fichiers dont
le nom contient des caractères biscornus, comme des espaces ou des accents

mais après ça devient rapidement compliqué de les utiliser, dans le terminal notamment

c'est pourquoi on recommande d'**éviter les espaces et les accents** dans les noms de
fichiers

````{admonition} Jean\ Mineur
:class: seealso admonition-small
si vous êtes observateur vous avez peut-être remarqué ceci dans la session de tout à l'heure:
```bash
python /c/Users/Jean\ Mineur/cours-info/intro/demo/python/fact.py
```
et vous vous êtes peut-être demandé pourquoi il y a un `\` dans `Jean\ Mineur`  

la réponse est que le nom du dossier contient un espace; vu dans l'explorateur de fichier on verrait bien `Jean Mineur`

**mais** pour `bash` un espace ça désigne un séparateur entre deux mots !!  
du coup on met ce caractère bizarre - on l'appelle le *baskslash* `\` - pour dire que l'espace ne doit **pas** être pris comme **un séparateur**, mais fait partie du nom de fichier...  
voyez que c'est quand même plus simple de mettre par exemple un `-` dans le nom de fichier, tant qu'on peut (là c'est le programme d'installation de Windows qui crée le homedir, on n'a pas eu le choix...)
````

+++

### affichez les extensions dans les noms de fichier

dans l'explorateur Windows, si vous créez un fichier **`foo.txt`**, par défaut on va vous montrer  
dans l'explorateur de fichiers une entrée qui s'affiche avec comme nom **simplement `foo`**

pourquoi ? dans son infinie sagesse Windows a jugé que c'était "plus simple" de ne pas montrer l'extension, ici `.txt`  
personnellement je ne trouve pas ça très pratique…

voici comment on peut changer ce comportement, pour voir **les noms de fichier en entier**

`````{grid} 1 1 2 2

````{card}
:header: par défaut, pas d'extension
```{image} media/fig-explorer-showext-1.png
:width: 600px
```
````
````{card}
:header: mais on peut le changer
```{image} media/fig-explorer-showext-2.png
:width: 600px
```
````
`````

si bien qu'après vous voyez bien ce qu'il faut: ![](media/fig-explorer-showext-3.png)

+++

## creusons un peu `bash`

+++

### quelques commandes utiles

+++

voici un résumé sur quelques commandes `bash`, parmi les plus simples et les plus utiles

| commande | fonction |
|-:|:-|
| `cd` | aller dans le *homedir* |
| `cd elsewhere` | changer de dossier courant |
| `pwd` | afficher le dossier courant |
| `ls` | lister les fichiers et dossiers dans le dossier courant |
| `ls elsewhere` | lister les fichiers et dossiers dans un autre dossier |
| `ls fi les` | lister les fichiers `fi` et `les` |
| `mkdir newfolder` | créer un dossier |
| `rm oldfile` | supprimer un (ou des) fichier(s) - **attention** ils sont supprimés pour de bon et non pas placés dans la corbeille |
| `mv oldname newname` | pour renommer un fichier (ou un dossier) |
| `echo a message` | pour afficher du texte |
| `cat somefile` | pour afficher le contenu d'un (ou plusieurs) fichier(s) |

+++

### *globbing*

si j'ai plusieurs fichiers qui se terminent en `.txt`, je peux les lister avec la notation en `*` comme ceci

```bash
# je crée (ou j'écrase) un second fichier bar.txt
$ echo "un autre fichier bidon" > bar.txt
```

de là je peux lister tous les fichiers qui se terminent en .txt

```bash
$ ls *.txt
bar.txt foo.txt
```
ou tous ceux qui commencent par un f

```bash
$ ls f*
foo.txt
```

ou toute combinaison du même genre

```bash
$ ls f*txt
foo.txt
```

+++

#### à n'importe quelle profondeur

```bash
# si je veux chercher tous les fichiers en *.txt
# à n'importe quelle profondeur sous mon dossier courant

ls **/*.txt
````

+++

````{admonition} le reste est optionnel

à partir d'ici le contenu est optionnel

````

+++

## bash - partie avancée

pour les curieux qui voudraient comprendre un peu mieux:

+++ {"tags": ["level_intermediate"]}

### les crochets `[]` (avancé)

```bash
# on peut aussi utiliser les [] 
# ici tous les fichiers qui commencent par un f ou un b et qui finissent en .txt

ls [fb]*.txt
```

```bash
# et si on veut par exemple tous les fichiers qui commencent par une lettre minuscule

ls [a-z]*.txt
```

```bash
# ou par une lettre, qu'elle soit en minuscule ou en majuscule

ls [a-zA-Z]*.txt
```

+++

### redirections

plutôt que d'afficher la résultat d'une commande dans le terminal, il est parfois pratique de rediriger cela dans un fichier

par exemple si j'écris dans le terminal

  ```bash
  # je crée ou j'écrase le fichier foo.txt
  echo "un petit fichier bidon" > foo.txt
  ```

ce qui va se passer c'est que je vais créer (ou écraser) le fichier `foo.txt` pour y ranger dedans la chaine  
`un petit fichier bidon\n`

le dernier cararactère (`\n`) correspond à un **saut de ligne**

+++

### la syntaxe de bash

pour décrire un peu mieux le langage bash, voici les caractères qui ont un rôle particulier dans une ligne de commandes bash:

- ` ` (Espace): on l'a déjà évoqué, l'espace sert à découper la phrase en mots; et de là
  - le premier mot correspond à une commande (qu'on cherche selon le PATH); c'est le programme qu'on va lancer
  - les autres mots sont passés au programme
  - donc si vous tapez
    ```bash
    dans cette phrase
    ```
    on va chercher un programme qui s'appelle `dans` et lui passer deux paramètres `cette` et `phrase`
- `"`: avec les quotes, on peut éviter le découpage; ainsi
  ```bash
  dans "cette phrase"
  ```
  va aussi exécuter la commande `dans` mais lui passer **un seul paramètre** qui contient un espace, `cette phrase`
- `>` et `<`: servent à rediriger l'entrée et la sortie du programme  
  comparez le résultat de
  ```bash
  # sans redirection: le texte s'affiche dans le terminal
  echo un message 
  # essayez de rediriger la sortie, cela va créer le fichier (s'il n'existait pas encore)
  echo un message > foo.txt
  ```
- `|` avec le *pipe* on peut facilement brancher la sortie d'un programme sur l'entrée d'un autre:
  ```bash
  prog1 arg1 | prog2 arg2
  ```
  signifie que la sortie de `prog1 arg1` est branchée (comme avec un tuyau) dans l'entrée de `prog2 arg2`
- `;` pour faire deux commandes l'une après l'autre
  ```bash
  prog1 arg1 ; prog2 arg2
  ```
  va lancer `prog1`, attendre qu'il ait terminé, puis lancer `prog2`; lorsque `prog2` sera terminé le terminal nous redonne la main

et plein d'autres choses utiles, très rapidement:

- le `~` pour faire référence à votre *homedir* (ex: `cat ~/.ssh/id_rsa.pub`)
- le `$` pour utiliser la valeur d'une variable (ex: `echo $PATH`)
- le `'` (simple quote) qui fontionne un peu, mais subtilement différemment de, la double quote
- le `&` pour lancer un programme en *background* (en arrière-plan), permet de rendre la main immédiatement; sert en plus de séparateur comme le `;`
- on peut faire des boucles, des tests, des calculs, ...
- etc etc..., plein d'autres encore, mais ne nous égarons pas...

+++

### les paramètres 

chaque commande est libre d'interpréter les paramètres comme elle veut; par exemple  
* avec la commande `cat` les paramètres sont tous interprétés comme des noms de fichiers
* par contre avec `git`, le premier paramètre doit être le nom d'une (sous-)commande `git` - comme par exemple `clone` ou `pull` - et les autres paramètres sont à leur tour interprétés en fonction, justement, de la sous-commande...

+++

### les options

quasiment toujours, la commande va accepter des paramètres qui sont optionnels, et qui permettent de modifier légèrement le comportement  
on en a vu déjà plusieurs, e.g.

* `ls [-l|-F]` pour choisir un mode de présentation
* `python --version`

le plus souvent également:

* les options commencent par `-` ou `--`
* elles apparaissent généralement **avant** les "vrais" paramètres
* la tradition veut qu'une même option est souvent disponible sous les deux formes
  * `-` pour l'option courte
  * `--` pour l'option longue
* ainsi par exemple c'est équivalent de faire
  * `python --version`
  * `python -V`

+++

## c'est quoi l'OS ?

partie optionnelle

votre OS (Operating System), vous le savez bien sûr, c'est Windows, MacOS, ou linux  
derrière quelques différences (très) visibles, ils possèdent en réalité de très nombreux concepts communs

+++

````{admonition} à quoi ça sert ?
:class: note

si on regarde le cas d'une calculette rustique, c'est un objet facile à utiliser parce que

* on ne fait tourner qu'un programme à la fois
* du coup un programme a librement accès à toutes les ressources
* par exemple : je peux décider sans souci de ranger la variable X dans la case mémoire 1

mais dans le cas d'un ordinateur c'est **beaucoup plus compliqué** !

* il y a plein de programmes qui tournent **en même temps**
* accessoirement plusieurs d'utilisateurs différents - possiblement **en même temps** aussi
* donc on ne peut plus du tout écrire un programme de manière aussi simpliste !  
  imaginez si deux programmes décident d'utiliser tous les deux la case mémoire 1 ...
````

+++

````{admonition} le rôle de l'OS: isolation entre les programmes
:class: note

ainsi le rôle de l'OS c'est principalement de fournir de l'**isolation** entre les programmes, en termes de

* travail concurrent: le *scheduler* de l'OS "*donne*" le ou les processeurs (CPU) aux programmes  
  dans un mode ***chacun son tour*** - et à relativement haute fréquence  
  ce qui donne l'illusion qu'ils tournent tous en même temps  
  ```{admonition} pour voir tous les programmes
  :class: dropdown seealso

  * sur mac, lancez *Activity Monitor*
  * sur Windows: *Task Manager*
  * sur linux, lancez `top` ou `htop`

  et vous allez voir les dizaines de programmes qui sont actifs dans votre ordinateur
  ```
* accès à la mémoire: chaque programme a accès à un espace qui lui est propre
* accès (concurrents) aux autres périphériques, notamment
  * mémoire de masse (*aka* "disque dur" même si on a presque tous un SSD maintenant...)
  * réseau
  * carte graphique...

````

+++

````{admonition} notion de **process**
:class: note

l'unité de base pour matérialiser cette isolation s'appelle un ***process***  
chaque programme qui tourne constitue un ***process***, qui possède

* le code du programme, évidemment
  ```{admonition} pas forcément unique
  :class: admonition-x-small
  il est possible et même fréquent d'avoir plusieurs processus qui sont créés à partir du même code; c'est le cas par exemple lorsque vous avez deux terminaux en même temps à l'écran
  ```

* son espace mémoire
* un dossier courant (pour pouvoir utiliser des chemins d'accès *relatifs*, on va en reparler tout de suite)
* éventuellement une liste de processus fils
* et tout un tas d'autres détails...
````

+++

````{admonition} arborescence de processus
:class: admonition-x-small note

on ne peut créer un **process** .. que depuis un **process**  
(comme on l'a vu plus haut par exemple, le terminal passe son temps à créer des *process*)
et donc entre autres un *process* contient l'identité de son *process* parent - qu'on appelle le `ppid` pour *parent process id* (ce qui du coup, donne à l'ensemble des processus une structure d'arbre)

pourquoi c'est important pour nous ?  
parce que ça explique cette histoire scabreuse de la variable `PATH`  
car en effet les variable d'environnement - comme `PATH` - sont **héritées du processus parent**  
````

+++

````{admonition} soyons précis (pour les curieux)
:class: seealso

le terme *OS* - *Operating System* a plein de significations différentes dans le langage
courant

* Windows et MacOS : incluent une interface graphique
* linux : l'interface graphique est plus clairement séparée, car on a le choix d'installer telle ou telle

**mais** nous ici lorsqu'on parle d'OS, on désigne **seulement** ce qu'on appelle aussi le
**noyau**  
c'est-à-dire techniquement :

* le **seul** programme dans l'ordinateur qui a **accès direct** aux périphériques
* qui "fait tourner" les programmes en leur donnant tour à tour accès au processeur
* et qui fait en sortes qu'ils soient **isolés les uns des autres**
* tous les autres programmes (*user land*) accèdent à ces ressources au travers
  d'**abstractions**:

  * mémoire : **mémoire virtuelle**  
    la case mémoire '1' est redirigée vers un bout de mémoire allouée au programme  

  * **système de fichiers**  
    le disque dur est accessible au travers de dossiers et fichiers

  * **interface réseau**  
    les applications utilisent "gratuitement" les protocoles réseau - comme TCP/IP  
    qui sont en fait implémentés dans le noyau

  * **périphériques exotiques**  
    les constructeurs de composants - comme par ex. une carte vidéo ou une carte son - fournissent ce qu'on appelle un *driver*
    (qui est intègré au noyau) pour exposer aux applications une interface indépendante du matériel
````
