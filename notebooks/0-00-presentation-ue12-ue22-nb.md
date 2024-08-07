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
nbhosting:
  title: "pr\xE9sentation des UEs"
---

Licence CC BY-NC-ND, Thierry Parmentelat & Valérie Roy

```{code-cell} ipython3
:tags: [raises-exception]

%%python
from IPython.display import HTML
HTML(filename="_static/style.html")
```

# UE12 et UE22 d'Informatique

Présentation générale des UE12 et UE22  
Unités d'Enseignement du premier et du second semestre d'Informatique

````{admonition} pour démarrer
:class: tip

pour accéder rapidement à cette page, tapez dans votre navigateur

```bash
https://tinyurl.com/ue12-p24
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

en cas de **dificulté**: compréhension, charge de travail, rapidité des cours (trop/pas assez), motivation, problème de portable...

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
  - découverte d'un langage compilé de haut niveau

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

* - rudiments de Web
  - 5
  - HTML, CSS, JavaScript

* - réseau
  - 2
  - TCP/IP, http

* - site Web
  - 1
  - réaliser un site web en flask

* - hackaton-WEB
  - 1
  - réaliser un code en groupe de 4
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
  - 6
  - libérées

* - propriété intellectuelle/industrielle
  - 1
  - conférence

* - soutenances
  - 2
  - présentation des projets en groupe
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

## Les 2 langages <span style="color:blue">Python</span> et <span style="color:blue">C++</span>

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

+++

## Les supports de cours
(label-liste-cours)=

```{list-table} les cours en ligne
:header-rows: 1
:stub-columns: 1

* - cours
  - URL
* - intro (ce cours)
  - <https://ue12-p24-intro.readthedocs.io/>
* - Python numérique
  - <https://ue12-p24-numerique.readthedocs.io/>
* - GIT
  - <https://ue12-p24-git.readthedocs.io/>
* - Python avancé
  - <https://flotpython-slides.readthedocs.io>
* - C++
  - <https://cpp.bmarchand.fr/>
```

% S2 - à paraitre
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

> à-la-maison: vous terminez les notebooks commencés et vous relisez les notebooks déjà vus

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

mais pour ça il faut avoir bien tout installé...  
on en reparle donc à la fin des installations

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

vous êtes naturellement autorisés à utiliser toutes les ressources disponibles sur Internet

### google, StackOverflow

S'agissant des ressources "classiques" telles que la recherche google, et les sites spécialisés comme StackOverflow, leur usage est même **fortement recommandé**; vous rencontrez un concept pour la première fois, ou vous avez de la difficulté à écrire un morceau de code, vous devez avoir le réflexe de chercher à en savoir plus sur google ou wikipedia, ou à trouver une solution sur SO (stackoverflow), ...


### chatGPT[^chatgpt], Copilot[^copilot]

Toute cette famille d'outils récents issue de l'IA sont clairement de très bons outils **d'aide** à la programmation, et nous ne pouvons pas les ignorer  

````{admonition} Quelle est leur place dans les cours ?

> il faut les voir comme une amélioration, voire un remplacement des recherches Internet/stack-overflow/...

> ***mais* ils ne se substituent pas** au programmeur ...  
> ils peuvent simplement lui faire gagner du temps dans l'écriture de certaines parties du code

> naturellement les résultats qu'ils vous donnent demandent à être **très soigneusement testés et validés**[^responsible]

> si vous n'avez pas de compétences en programmation: vous ne pourrez pas exploiter correctement leurs résultats
````

donc, ce que nous vous conseillons fortement (demandons):

1. d'abord vous apprenez à programmer
2. de manière ensuite à être capables de tirer partie de ces nouveaux super outils

---

[^chatgpt]: *ChatGPT is an AI-powered language model developed by OpenAI, capable of generating human-like text based on context and past conversations.*

[^copilot]: *GitHub Copilot is non-free, cloud-based and AI-powered tool developed by GitHub and OpenAI to assist users of (some) IDEs (like vscode) by autocompleting code.* 

[^responsible]: github says about github-copilot: *"you are responsible for ensuring the security and quality of your code. We recommend you take the same precautions when using code generated by GitHub Copilot that you would when using any code you didn't write yourself. These precautions include rigorous testing, IP scanning, and tracking for security vulnerabilities....*
