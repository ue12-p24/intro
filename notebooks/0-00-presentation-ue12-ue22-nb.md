---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3 (ipykernel)
  language: python
  name: python3
language_info:
  name: python
  nbconvert_exporter: python
  pygments_lexer: ipython3
---

Licence CC BY-NC-ND, Thierry Parmentelat & Valérie Roy

```{code-cell} ipython3
:tags: [raises-exception]

%%python
from IPython.display import HTML
HTML(filename="_static/style.html")
```

````{admonition} pour démarrer
:class: tip

pour accéder rapidement à cette page, tapez dans votre navigateur

```bash
https://ue12-p24-intro.rtfd.io/
```

````

+++

*la petite introduction sur les enseignements commencée lors de la pré-rentrée*

+++

# L'enseignement de l'informatique en première année

- **4 modules** d'enseignement (un module = 9 séances de 3 heures)  
   chacun sur une **thématique**: *numérique/data*, *programmation*, *web-réseau*, *projets*  
   (moins de 4 semaines de cours d'informatique dans l'année)


- on ne couvre qu'une toute **petite partie** d'un **très vaste domaine**  
  c'est le **minimum du minimum** pour tout élève *quelle que soit sa future orientation professionnelle*

- vous ne progresserez que grâce à une **implication personnelle** en dehors des séances de cours  
  d'une séance à l'autre vous devez: **relire** les notebooks, **revoir** et **terminer** les exercices  
  et **lire** en autonomie les notebook non étudiés en cours

- votre **présence est obligatoire** à toutes les séances d'informatique

+++

### au premier semestre `UE12`

les deux modules:

----------

1. un module **python-numérique** comprenant
   * 5 séances sur `numpy` (librairie numérique), `pandas` (traitement de données) et `matplotlib` (visualisation)  
   * 2 séances sur la gestion de version de fichiers avec `git` et `github`  
   * 1 séance de hackathon (coder en équipe)

----------   

2. un module d'**apprentissage de la programmation** (**1 langage** au choix parmi 3)
   * `Python` approfondissements du langage
   * `C++` découverte d'un langage de haut niveau compilé (et proche de la mémoire)
   * `Julia` découverte d'un langage de haute performance, spécialisé en calcul scientifique  
    *nouveau cette année*
  * 9 séances (1 langage)  
  * une journée de hackathon (coder en équipe)

+++

### au second semestre `UE22`

les deux modules:

----------

1. un module **réseau** et **Web frontend et backend**

----------

2. un module de **projets informatique**
   * réalisés, en équipe de 4, sur une semaine *bloquée* (du 30 juin au 4 juillet)
   * avec des sujets proposés par des **alumni**, des **enseignants-chercheurs** des mines   
     et par les **élèves** motivés par leurs projets personnels 

----------

***maintenant nous allons procéder aux installations de vos portables***

+++

*la description plus complète des enseignements*

+++

# UE12 et UE22 d'Informatique

Présentation générale des UE12 et UE22  
Unités d'Enseignement du premier et du second semestre d'Informatique

````{admonition} pour démarrer
:class: tip

pour accéder rapidement à cette page, tapez dans votre navigateur

```bash
https://ue12-p24-intro.rtfd.io/
```

````

+++

## Nos objectifs

+++

````{admonition} **prise d'autonomie** dans l'**utilisation des ressources digitales**

pas de salle informatique  
le premier objectif est que vous sachiez **rapidement utiliser votre propre ordinateur** pour travailler  
*BYOD: Bring Your Own Device*

> vous devez apporter votre portable (et son chargeur) **à toutes les séances d'informatique**
````

----

````{admonition} **prise d'autonomie** dans le **numérique et la programmation**
avec pour cela un focus sur quelques outils (du moment)  
que vous devez installer sur vos ordinateurs
> ces outils serviront aux autres enseignements (mathématiques, machine-learning...)
````

----

````{admonition} nos cours sont introductifs
seul un **travail personnel entre les cours** vous permettra **d'assimiler** les rudiments  
et d'**acquérir** quelques automatismes (nécessaires à la programmation)

> ne pas travailler l'informatique pour vous consacrer aux autres matières plus fondamentales/exigeantes n'est pas un bon choix

> vous avez déjà un bon niveau en informatique ? venez-nous voir, vous éviterez de perdre votre temps
````

----

````{admonition} les cours sont coopératifs
et non pas compétitifs; vous êtes très à l'aise ? aidez vos camarades, vous apprendrez plein de choses aussi !
````

----

ces quelques compétences en informatiques sont **incontournables quel que soit votre futur métier**  

> il vous faudra aussi les tenir à jour

----

en cas de **difficulté**: compréhension, charge de travail, rapidité des cours (trop/pas assez), motivation, problème de portable...

> contacter valerie.roy@minesparis.psl.eu

+++

## Le programme sur l'année (8 ECTS)

2 ECTS = 9 séances de 3 heures

+++

### UE12: premier semestre (4 ECTS)

```{list-table} **PE** *Programmation Élémentaire* (2 ECTS)
:header-rows: 1
:stub-columns: 1
:align: center
:width: 80%
:name: table-pe

* -
  - séances
  - contenu

* - python-numérique
  - 5
  - pandas, numpy, matplotlib

* - git
  - 2
  - système de gestion de versions de projets

* - hackaton-PE
  - 1
  - réaliser du code en groupe (min 2 max 4)
```

```{list-table} **AP** *Apprentissage de la Programmation* (2 ECTS)
:header-rows: 1
:stub-columns: 1
:align: center
:width: 80%
:name: table-ap

* - langage (au choix)
  - séances
  - contenu

* - python-avancé
  - 9
  - approfondissements du langage Python

* - c++
  - 9
  - découverte d'un langage de haut niveau et compilé

  
* - Julia
  - 9
  - découverte d'un langage de haute performance, spécialisé en calcul scientifique

* - hackaton-AP (pour tous)
  - 2
  - réaliser du code en groupe de 4
```

+++

### UE22: second semestre (4 ECTS)

```{list-table} **PFC** *Programme fiables et concurrents* (2 ECTS)
:header-rows: 1
:stub-columns: 1
:align: center
:width: 80%
:name: table-pfc

* - 
  - séances
  - contenu

* - Web frontend
  - 5
  - HTML, CSS, JavaScript

* - Web backend
  - 4
  - TCP/IP, http, serveurs d'API 
```

```{list-table} **PI** *Projet Informatique* (2 ECTS) en groupe de 4 élèves
:header-rows: 1
:stub-columns: 1
:align: center
:width: 80%
:name: table-pi

* - 
  - séances
  - contenu

* - travail en groupe
  - semaine bloquée
  -

* - propriété intellectuelle/industrielle
  - 1
  - conférence

```

````{admonition} à propos du module PI

- implication des alumnis et d'enseignants-chercheurs-ingénieurs de l'école qui proposent et encadrent des sujets
- parfois sur un domaine que vous ne connaissez pas
- parfois avec des techniques que vous ne connaissez pas (encore)
````

+++

## Les cours

### Ce qu'on attend de vous

* que vous soyez présents à tous les cours (ils sont obligatoires)
* que vous préveniez votre enseignant en cas d'absence (avant si cela vous est possible)
  il vous indiquera quoi rattraper

* que vous soyez à l'heure (un contrôle continu sera fait en début de séance)

### Votre comportement

soyez constructifs, coopératifs

*  vis-à-vis des autres élèves en les aidant sans être compétitif
*  vis-à vis de vos enseignants en leur posant des questions, en leur disant si ils vont trop/pas assez vite...  
  aidez les à comprendre où vous en êtes

### Pour savoir où vous en êtes ? et pour vous évaluer

*pour le fun* (non noté)
> des hackatons pour vous apprendre à travailler ensemble

un contrôle continu noté (quiz ou exercices au début de chaque cours)

des mini-projets de programmation (notés et **personnels**)

### À savoir

> les enseignants ne pourront pas attribuer de note de contrôle continu aux élèves trop souvent absents (qui iront donc en rattrapage)

> si vous êtes absent parce que vous connaissez déjà parfaitement toutes ces notions: contacter `valerie.roy@minesparis.psl.eu`

+++

## Les 3 langages <span style="color:blue">Python</span>, <span style="color:blue">C++</span> et <span style="color:blue">Julia</span>

vous prendrez un de ces langages au choix
> un formulaire vous sera envoyé pour le choix du langage

### <span style="color:blue">Python</span>

- simple, lisible et *élégant*, interprété
- très grand nombre de librairies
- prototypage rapide
- applications web, data-science, machine-learning

#### <span style="color:blue">C++</span>

- haut-niveau, mais aussi proche de la machine, typé, compilé, très performant
- plus difficile d'accès que <span style="color:blue">Python</span> et plus exigeant, mais vous apporte une compréhension fine de ce qui se passe en machine
- de belles constructions (templates)
- logiciels scientifiques, OS, BdD, moteurs de rendus, logiciels de
  micro-contrôleurs (tout ce qui doit aller vite)

#### <span style="color:blue">Julia</span>

- langage moderne, de haute performance
- généraliste mais spécialisé dans le calcul scientifique
- prototypage rapide
- cours plus exigeant que celui de <span style="color:blue">Python</span>

+++

## Les supports de cours
(label-liste-cours)=

```{list-table} les cours en ligne
:header-rows: 1
:stub-columns: 1

* - cours
  - URL
  - github
* - intro (ce cours)
  - <https://ue12-p24-intro.readthedocs.io/>
  - <https://github.com/ue12-p24/intro>
* - Python numérique
  - <https://ue12-p24-numerique.readthedocs.io/>
  - <https://github.com/ue12-p24/numerique>
* - GIT
  - <https://ue12-p24-git.readthedocs.io/>
  - <https://github.com/ue12-p24/git>
* - Python avancé
  - <https://ue12-p24-python.readthedocs.io/>
  - <https://github.com/flotpython/slides>
* - C++
  - <https://cpp.bmarchand.fr/>
  - ??
* - Web frontend
  - <https://ue22-p24-web.readthedocs.io/>
  - <https://github.com/ue22-p24/web>
* - Web backend
  - <https://ue22-p24.github.io/backend/>
  - <https://github.com/ue22-p24/backend>
```

% S2 - à paraître
% * - Web
%  - <https://ue12-p24-web.readthedocs.io/>
% * Réseau
%  - <https://slides.bmarchand.fr/>

ils contiennent

* les notions de base à connaître
* quelques notions intermédiaires
* des notions avancées (pour ceux qui vont plus vite)

les notebooks sont plutôt rédigés pour être étudiés *en autonomie*

* ils sont donc trop détaillés pour être parcourus entièrement en cours
* les enseignants en choisiront certains et les parcourront rapidement pour vous présenter des notions et des exercices    
  **en cours**: écoutez vos enseignants et posez des questions  
  (plutôt que de lire les notebooks dans votre coin... vous les relirez bien sûr entre les cours)
> en cours: on commence les apprentissages ensemble en parcourant des *notebooks*

> à-la-maison: vous terminez les notebooks commencés, vous relisez les notebooks déjà vus et vous lisez les autres en autonomie

+++

### Sous quelle forme 

ce sont des **notebooks** Jupyter, formés de

* cellules de textes: les explications (en `markdown`)
* cellules de code: que vous exécutez et pouvez modifier

ils sont souvent disponibles sous deux formes:

### HTML statique

i.e. dans un site web "normal", lisible comme d'hab avec votre navigateur
c'est pratique parce que

* on n'a **besoin de rien installer**
* et on peut **facilement rechercher** dans tout un cours
* ça sert donc de support principal pour réviser

### notebooks exécutables

ce qui permet d'aller beaucoup plus loin, car

* on peut alors **modifier et exécuter** le code, ce qui est très pratique pour l'apprentissage
* et en plus c'est un outil qu'on **utilise beaucoup dans la vraie vie**, ça fait partie de vos futurs acquis

````{admonition} nbhosting
:class: dropdown admonition-small

enfin les années précédentes, nous avions utilisé une plateforme hébergée sur <https://nbhosting.inria.fr>, où les notebooks étaient accessibles en *live* (code modifiable et exécutable) sans installation préalable;
il s'agissait essentiellement d'une facilité pour les premiers cours, de sorte que l'on puisse avancer avant que toute la promo soit entièrement bien installée sur les ordis perso.

il devrait être entendu que le mode d'utilisation "normal" des notebooks est **en local sur votre ordi**,
aussi cette année 2024, nous allons nous passer totalement de cette plateforme;  
on pourra envisager de donner un accès à ce service aux élèves qui auraient des difficultés insurmontables avec leurs installations
````

+++

## Ressources Internet & IA

### google, StackOverflow

L'usage des **ressources "classiques"** (recherche *google*, sites spécialisés comme StackOverflow...) est **fortement recommandé**  
Vous rencontrez un concept pour la première fois ?  
Vous avez des difficultés avec certaines instructions dans un morceau de code ?  
Vous ne comprenez pas un message d'erreur ?  

**$\Rightarrow$** Ayez le réflexe de chercher à en savoir plus sur *google* ou *wikipedia*, ou à trouver une solution sur *stackoverflow*...


### chatGPT[^chatgpt], Copilot[^copilot]

```{admonition} Vous êtes un programmeur **expérimenté** ?  

> votre niveau vous permet:
> - de **juger** de la **qualité** du code proposé, de le **tester**, de le **critiquer**    
> - éventuellement de le **corriger**, l'**améliorer**, vous en servir de **base** ou le **jeter** 

> ces outils sont alors de très bons **assistants** qui peuvent vous faire **gagner du temps**  
  et vous donner des **idées** dans l'écriture de certaines parties du code

```

```{admonition} Vous êtes un programmeur **débutant** ?

> Ces outils, dans leur version classique, ne s'utilisent pas comme de simples **améliorations** des recherches sur Internet:  
  ils se **substituent** à vous et codent votre problème **à votre place**.  

> Difficile, pour un débutant:  
> - de **comprendre** un code généré avec des constructions très avancées (qu'on n'utilise pas quand on débute)
> - de **corriger** un code qui sera toujours *un peu faux par ci par là*

> si vous utilisez une IA:
> - vous allez **passer à côté** de l'apprentissage de base de la programmation par **recherche, essai, erreur**
> - une fois le code généré, vous ne serez pas capable d'imaginer une autre manière de faire  

>  mal utilisés, ces outils seront **contre productifs** voire nuisibles à vos apprentissages
> donc, ce que nous vous conseillons fortement:
> 1. d'abord vous apprenez à programmer
> 2. de manière ensuite à être capables de tirer partie de ces nouveaux outils

```

---

[^chatgpt]: *ChatGPT is an AI-powered language model developed by OpenAI, capable of generating human-like text based on context and past conversations.*

[^copilot]: *GitHub Copilot is non-free, cloud-based and AI-powered tool developed by GitHub and OpenAI to assist users of (some) IDEs (like vscode) by autocompleting code.* 

[^responsible]: github says about github-copilot: *"you are responsible for ensuring the security and quality of your code. We recommend you take the same precautions when using code generated by GitHub Copilot that you would when using any code you didn't write yourself. These precautions include rigorous testing, IP scanning, and tracking for security vulnerabilities....*

