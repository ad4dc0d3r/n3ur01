---
title: sublime text
date: 2017-03-02T12:00:00-05:00
draft: false
---

## TERMINUS

pour terminus j'ai ajoute les lignes suivantes dans default linux sublime-kemap

```json
[
	// Open a terminal tab at current file directory
	{
		"keys": ["ctrl+alt+b"],
		"command": "terminus_open",
		"args": {
			"cwd": "${file_path:${folder}}"
		}
	},
	{ "keys": ["ctrl+shift+`"], "command": "toggle_terminus_panel" }
]
```

puis interchanger avec la "console sublime"

```json
[
	// Open a terminal tab at current file directory
	{
		"keys": ["ctrl+alt+b"],
		"command": "terminus_open",
		"args": {
			"cwd": "${file_path:${folder}}"
		}
	},
	{ "keys": ["ctrl+`"], "command": "toggle_terminus_panel" },

	{
		"keys": ["ctrl+shift+`"],
		"command": "show_panel",
		"args": { "panel": "console", "toggle": true }
	}
]
```

# Plugins

pour prettier --> install le package via package manager puis
install l'api en globale:

```bash
npm install --global prettier

```

puis renseigner node path et prettie cli path dans jsprettier.sublime-settings-User (utilier which node et which prettier et coller resultat)

```json
{
	"node_path": "/home/ilan/.nvm/versions/node/v21.5.0/bin/node",
	"prettier_cli_path": "/home/ilan/.nvm/versions/node/v21.5.0/bin/prettier"
}
```

# 1 text editing

1. multi cursor: ctrl+click or click on word + ctrl+d
2. multi cursor on end line of a block ctrl+shift+L
3. wrapper (ex:html tags) on block: alt+shift+w

# 2 identations

1. ctrl +shift+d pour duplicate n'importe ou sur la ligne
2. ctrl+shift+key pour supprimer une ligne (pareil n'importe ou sur la ligne)
3. ctrl + [ ou ] pour deplacer une ligne
4. select + edit + line + reindent
5. ctrl + shift + v pour intelligent paste

# 3 Projects management

1. opening folder(drag and drop)
2. double click pour recuperer tabs presentation
3. ctrl+p pour rechercher un fichier par nom
    1. pareil avec @ pour trouver fonction
    2. pareil @. pour autocompletion sur selecteur css
    3. pour acceder un resultat de recherche i#sa --> donne el curseur directement sur le mot
    4. i:35 pour ligne
    5. ctrl + P permet sur le prefixe @ de lister toutes les fonctions de la page
4. show unsaved changes - via mouse menu
5. save project as: chercher project open recent ou open project

# 4 Command Palette

# 5 plugins

distraction free pour annuler full screen sur zen mode
keybinding super+F11

# 6 !!!! Test center !!!!

j'ai eu un probleme pour run build par defaut il m'a fallu utiliser gcc dans le terminal puis placer le buid sur defaut

# console super sublime n'accepte pas d'input sur sa console:

solution :

```c
 #ifndef Mishra

   freopen("input.txt", "r", stdin);

  freopen("output.txt", "w", stdout);

 #endif
```

fonctionne pas chez moi en c

-   sol 1 voir plus haut utiliser des texte pour input output
-   sol2 lier terminus a l'output de sublime:

--> tools --> build system --> recupere le nom du build systeme que tu veux modifier, ici: c
![](Pasted%20image%2020240129234349.png)
command palette: vpf
![](Screenshot%20from%202024-01-29%2023-44-32.png)

![](Screenshot%20from%202024-01-29%2023-45-30.png)

copier contenu:
![](Pasted%20image%2020240129234626.png)

et creer nouveau build an l'associant a terminus:
tools --> new build et copier apres avoir ajouter:
target et cancel

```json
{
	"target": "terminus_exec",
	"cancel": "terminus_cancel_build",
	"shell_cmd": "gcc \"${file}\" -o \"${file_path}/${file_base_name}\"",
	"file_regex": "^(..[^:]*):([0-9]+):?([0-9]+)?:? (.*)$",
	"working_dir": "${file_path}",
	"selector": "source.c",

	"variants": [
		{
			"name": "Run",
			"shell_cmd": "gcc \"${file}\" -o \"${file_path}/${file_base_name}\" && \"${file_path}/${file_base_name}\""
		}
	]
}
```

ensuite choisir simplement cterminus dans la liste de builder
