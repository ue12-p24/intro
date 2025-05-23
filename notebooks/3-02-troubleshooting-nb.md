---
jupytext:
  encoding: '# -*- coding: utf-8 -*-'
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
%%python
from IPython.display import HTML
HTML(filename="_static/style.html")
```

# troubleshooting

les erreurs les plus fréquentes lors des installations

si vous ne trouvez pas la réponse ici: **commencez par demander à google** en précisant bien votre contexte: le nom de l'OS, le logiciel qui ne fonctionne pas comme attendu, et le message d'erreur; il y a de très grandes chances que vous trouviez votre réponse sur `stackoverflow.com`

dans tous les cas, essayez d'abord de trouver par vous même avant de demander de l'aide à vos camarades ou aux professeurs

+++

## `code: command not found`

(label-troubleshoot-code-command-not-found)=

+++

````{admonition} symptôme
:class: error

vous lancez `code` dans le terminal et ça vous dit `code: command not found`
````

````{admonition} solution
:class: seealso

tout d'abord, si vous êtes sur Mac, assurez-vous **de bien avoir copié votre application `Visual Studio Code` dans le dossier `Applications`**

si c'est le cas, lancez vs-code par les menus   
puis dans la palette (ctrl-shift-P sur Windows, command-shift-p sur mac)  
trouvez la commande `shell command: install 'code' command in PATH`

comme toujours, relancez un nouveau terminal et réessayez
````

+++

## `python: command not found`

(label-troubleshoot-python-command-not-found)=

+++

````{admonition} symptôme
:class: error

vous lancez `python` ou `conda` dans le terminal et ça vous dit `python: command not found`
````

````{admonition} solution 1
:class: seealso

tapez dans votre terminal
 
  ```bash
  conda init bash
  ```
  avant de lancer un nouveau terminal et de réessayer

  ```{admonition} sur mac
  :class: warning
  
  si vous êtes sur mac, il se peut que votre shell soit `zsh` et pas `bash`  
  pas de souci pour suivre le cours avec `zsh`, mais par contre vous devez peut-être taper ici `conda init zsh`
  ```
````

````{admonition} solution 2 - Windows
:class: seealso

essayez de taper cette commande dans un terminal tout neuf  
  ```bash
  /c/miniconda/Scripts/conda.exe init bash
  ```
  avant de lancer un nouveau terminal et de réessayer
````


````{admonition} solution 3
:class: seealso

si ce n'est pas cela, le plus probable est que vous n'avez pas bien coché la case `mettre à jour $PATH` lors de l'installation de miniconda; réinstallez, relancez un terminal, et réessayez
````

+++

## `ModuleNotFoundError: No module named 'bidule'`

+++

````{admonition} symptôme
:class: error

vous avez installé un module Python avec `pip` (n'importe lequel, disons `numpy`) depuis le terminal  
**MAIS** depuis python, vous essayez de l'importer et il n'est pas trouvé...
````

````{admonition} solution
:class: seealso

dans 99% des cas, c'est parce que vous avez plusieurs environnements Python différents; vous installez dans un, et vous exécutez dans un autre...

vérifiez bien des deux cotés de quel python il s'agit, en tapant par exemple `type python`  
il faut bien sûr que ce soit le même python des deux cotés (à nouveau, là où vous installez et là où vous exécutez)
```{admonition} dans vs-code
:class: note

souvenez-vous aussi que sous VS-code vous avez un menu pour, justement, choisir l'environnement Python à utiliser
```
````

+++

## `jupyter lab` n'ouvre pas de nouvelle fenêtre dans le browser

+++

````{admonition} symptôme
:class: error

avec Windows: vous tapez `jupyter lab` dans le terminal, vous avez bien la litanie de messages qui s'affichent, mais ça ne crée pas une fenêtre dans le browser
````

````{admonition} solution 1
:class: seealso

il faut savoir d'abord que, parmi la dite litanie de messages il y a vers la fin quelque chose qui ressemble à
```bash
    To access the server, open this file in a browser:
        file:///Users/tparment/Library/Jupyter/runtime/jpserver-44282-open.html
    Or copy and paste one of these URLs:
        http://localhost:8889/lab?token=d805f1f129d6f2a531f4bb6104050a894c656c91059fe464
        http://127.0.0.1:8889/lab?token=d805f1f129d6f2a531f4bb6104050a894c656c91059fe464
```

la première solution consiste à copier-coller cette url, par exemple  
`file:///Users/tparment/Library/Jupyter/runtime/jpserver-44282-open.html`  
et d'ouvrir ça "à la main" dans le navigateur

bon c'est pédestre mais ça peut vous débloquer pour commencer
````

````{admonition} solution 2
:class: seealso

pour résoudre le problème plus en profondeur, je n'ai pas encore la solution universelle,  
mais je vous recommande pour commencer de bien vous assurer que vous avez choisi Chrome comme navigateur par défaut

à suivre donc - et si vous trouvez la solution dans votre cas spécifique, n'hésitez pas à la partager avec les enseignants..
````

+++

## ne peut pas lancer un programme Python depuis vs-code

+++

````{admonition} symptôme
:class: error

avec Windows: vous essayez de lancer votre programme Python depuis vs-code, mais vous avez un message selon lequel avec PowerShell on ne peut pas changer d'environnement
````

````{admonition} solution
:class: seealso

puis dans la palette (ctrl-shift-P sur Windows, command-shift-P sur mac)  
tapez `select default profile`  
et choisissez `bash` plutôt que `PowerShell`
````
