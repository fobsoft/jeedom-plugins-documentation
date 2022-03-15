---
layout: default
title: Documentation Advanced Scenario
lang: fr_FR
pluginId: advancedScenario
---

<div id="title">
<a href="../../../{{site.baseurl}}/{{page.pluginId}}/{{page.lang}}">{{page.title}}</a>
</div>

> Le plugin est encore jeune et peut encore comporter quelques bugs, mais il évolue régulièrement : n’hésitez pas à me contacter à mon courriel personnel, sois le fobsoft@gmail.com avec toutes vos remarques et suggestions.

# Présentation
Plugins pour gérer, créer ou modifier vos scénarios. Utilise les fonctionnalitées du système issus de Jeedom en ajoutant quelque fonctionnalité.
* Une maintenance par nœud
* Ajout de tag
  * parentLog: Objet parent du déclencheur du scénario, si le nom des objets son remplacer dans la spécification des équipements ex: [#parentLog#][Lumiere][On], le scénario peut etre utilise pour n'importe quel objet. (A venir)
* Ajout de block
  * foreach: Permet de réaliser une action pour chaque élément d'un tableau. (A venir)
  * while: Permet de réaliser une action tant que la condition est valide. (A venir)
* Ajout d'opérateur
  * arrayIn: Permet de déterminer si une valeur est contenue dans l'array (A venir)
  * arrayNotin: Permet de déterminer si une valeur n'est pas contenue dans l'array (A venir)
* Ajout de commande
  * arrayAdd: Création/ajout d’une valeur à un tableau (n'existe que pendant l'exécution du scénario.) (A venir)
  * arrayRemove: Suppression d’une valeur d’un tableau (A venir)
  * logVariable: Permet d'afficher dans le log toutes les valeurs associées à l'exécution du scénario (variable, tag, tableau) (A venir)
  * execGenericType: Permet d'exécuter les commandes des équipements d'un type générique (A venir)

# Installation et Configuration du plugins
Dans la section, "Configuration" se trouve quelques options pour configurer l'affichage des logs du plugin.
Une fois le plugin activé, on peut donc passer directement à la création et modification de ceux-ci.

# Configuration
> Attention, il sera possible de convertir vos scénarios issus de Jeedom vers ce plugin, mais l'inverse ne sera pas possible.

Vous pouvez accéder à la fenêtre de maintenance à partir du menu Plugins → Programmation → Advance Scenario.

Sur cette page, vous retrouvez la liste de vos scénarios comme à l'habituelle. Ceux avec un icône vert son des scénarios qui ne sont pas convertis, et ceux de couleur gris sont des scénarios converti.
Une fois converti l'édition d'un scénario via la maintenance de Jeedom n'aura pas d'effet sur celui-ci.
Cliquez sur un scénario pour accéder à sa configuration ou sur "Ajouter" pour en créer un nouveau:

![Config1](../images/Config1.png)

# Scénario

## Général
Dans cette oonglet vous disposer des meme information que dans un scenario normal mise à par le fait qu'il n'y a pas de section pour les declancheur puisue ceux-ci sont gere directement dans le flow.

![Config2](../images/Config2.png)

## Flow

Vous disposez à droite de l'écran des actions habituel d'un scénaario, il suffit d'un "drag and drop" vers la droite pour en ajouter. Je ne documenterais pas le fonctionnement des actions d'un scénario, puisqu'il y a déjà une documentation dédiée à ceci. 

![Flow1](../images/Flow1.png)

# A faire
* Empécher la suppression du node "Départ" puisque celui-ci est le point d'entré général
* Ajouter un bouton test, pour tester le flow du scénario et ainsi voir son issue

