---
layout: default
title: Documentation Generic Type Manager
lang: fr_FR
pluginId: genericTypeManager
---

<div id="title">
<a href="../../../{{site.baseurl}}/{{page.pluginId}}/{{page.lang}}">{{page.title}}</a>
</div>

> Le plugin est encore jeune et peut encore comporter quelques bugs, mais il évolue régulièrement : n’hésitez pas à me contacter à mon courriel personnel, sois le fobsoft@gmail.com avec toutes vos remarques et suggestions.

# Présentation
Plugins pour gérer vos commandes via leur type générique de manière dynamique. Il se présente de la même manière que les résumés des objets à la différence que les commandes ayant le type générique prédéfini sont ajouté automatiquement au résumé créé dans l'équipement si celle-ci fait partie de l'objet parent de l'équipement ou de l'un de ces enfants. Une fois fait, il vous donnera ces informations et possibilités :
* Une commande d'information pour chaque résumé qui regroupe toutes les commandes ayant le type générique prédéfini dans le résumé.
* Des commandes d'actions pour chaque résumé qui regroupe toutes les commandes ayant le type générique prédéfini dans le résumé, par exemple, si l'équipement se trouve au plus bas niveau des objets, une seule commande nous permettrait d'allumer toutes les lumières de la maison.
* Une variable d'état par défault pour l'exécution d'un résumé.
* Ajouter des modes à l'équipement et de prédéfinir des actions à exécuter
* Ajouter des actions aux changements d'une commande d'information.
* Ajouter des conditions à l'exécution d'une commande d'action.
* Ajouter des variables pour prédéterminer certaines valeurs.
* Ajouter des tâches à effectuer si une valeur est modifié.

Ainsi en utilisant ce plugin pour gérer une pièce par exemple, il sera possible lors d'une détection de présence via le résumé lié au type générique "PRESENCE" d'exécuter l'action de passer au mode "Présent" de l'équipement, celui-ci exécutera l'ouverture des lumières via le résumé lié au type générique "LIGHT_SLIDE_OPEN" (l'une des actions du type générique "LIGHT_STATE") à un pourcentage prédéterminé par une variable de l'équipement à la condition que la luminosité du résumé lié au type générique "BRIGHTNESS" soit plus petite qu'une valeur prédéterminée de l'équipement (variable).

Voici une partie de l'arborescence de mes objets auxquels je ferai référence lors de mes exemples.

![Présentation1](../images/Présentation1.png)

# Installation et Configuration du plugins
Dans la section, "Configuration" se trouve quelques options pour configurer l'affichage des logs du plugin.

Dans la section "Fonctionnalités", vous pouvez constater deux crons, elles servent à faire l'ajout de nouvelles commande à l'équipement de manière dynamique. Donc si vous ne prévoyez pas l'ajout de plusieurs équipements, vous pouvez désactiver celle qui roule aux cinq minutes. 

Une fois le plugin activé, on peut donc passer directement à la création d'un équipement.

![InstallationConfiguration1](../images/InstallationConfiguration1.png)

# Configuration des équipements
Les équipements sont accessibles à partir du menu Plugins → Programmation → Generic Type Manager.

Sur cette page vous retrouvez la liste de vos équipements. Cliquez sur un équipement pour accéder à sa configuration ou sur "Ajouter" pour en créer un nouveau:

## Équipement
* Nom de l'équipement : nom de votre équipement.
* Objet parent : indique l’objet parent auquel appartient l’équipement.
* Activer : permet de rendre l’équipement actif.
* Visible : permet de rendre l’équipement visible sur le dashboard.

## Résumé

Les résumés, permettent de regrouper des informations ou actions d'un type générique. Toutes les commandes possédant ce type générique sous l'objet parent de l'équipement ainsi que les objets enfant de celui-ci seront automatiquement prit en considération.

Lors de l'ajout d'un résumé, il vous sera demandé deux choses, le nom que vous voulez donner au résumé qui doit être unique pour l'équipement et le type générique désiré. Si vous voulez créer un résumé dont les commande ne figure pas dans l'objet parent de l'équipement ou l'un de ces enfants, vous pouvez simplement inscrire "NONE" ainsi le plugin ne cherchera pas à associer de manier automatique des commandes à se résumer, se sera à vous de le faire manuellement.
* Général
  * Nom : nom du résumé
  * Icon : icône qui sera utilisé pour l'affichage du résumé sur le dashbord
  * Type générique : le type générique des commande qui doivent être inclus au résumé
  * Authorisé : permet de rendre le résumé actif, dans le cas contraire, les valeurs de celui-ci seront remonté, mais les actions associées à celui-ci ne seront pas exécuté.
  * Authorisé la gestion dynamique : Si activée, le système ajoute les commandes du type générique du résumé ce trouvant dans l'objet parent de l'équipement ainsi que les objets enfant de celui-ci. Si une commande déjà configuré ne si trouve pas ou plus, elle sera supprimé.
  * Affiché : permet de rendre visible le résumé sur le dashbord
  * Affiché même si nulle : permet de rendre visible le résumé sur le dashbord même si aucune valeur n'est remontée
  * Calcul : le type de calcul qui doit être effectué lors d'un changement de valeur d'une commande
  * Unité : Unité de la mesure
  * Méthode de comptage : Méthode de comptage, si binaire est sélectionné, le résumé agit comme un interrupteur (on , off)
* Action sur la valeur du résumé si
  * Activer : permet de rendre la commande active, dans le cas contraire, elle n'affectera pas le résumé.
  * Commande : liste des commandes qui affecte le résumé
* Condition pour déclenché
  * Activer : permet de rendre la condition active, dans le cas contraire, elle n'affectera pas l'action.
  * Commande : condition pour exécuter le déclenchement
* Action à effectuer si déclenché
  * Activer : permet de rendre la commande active, dans le cas contraire, elle ne sera pas exécuté.
  * Commande : liste des commandes à déclencher
* Action à effectuer si dé-enclenché
  * Activer : permet de rendre la commande active, dans le cas contraire, elle ne sera pas exécuté.
  * Commande : liste des commandes à déclencher


> Pour des exemples d'application de différents types générique, voir "Exemple de différents types générique".
> Comme mon installation domotique évolue et que ce plugin dispose d'une option pour le dupliquer ainsi qu'une option pour appliquer sa configuration sur un autre équipement, j'ajoute à l'équipement tous les résumés dont je pense avoir besoin dans l'une ou l'autre de mes pièces ce qui me donne ceci au final.
> Petite astuce, si un sommaire dispose de plusieurs déclencheurs et que vous voulez que les actions à effectuer lors de déclenchements ou de dé-enclenchements soient exécutées à chaque fois que l'un d'eux est enclenché, configurer le calcul pour que le système effectue une somme et qu'il y ait aucune méthode de comptage. Ainsi, chaque fois que le total changera, les actions vont se réeffectuer. Dans le cas contraire, configurer le calcul pour que le système effectue un maximum avec une méthode de comptage binaire.

![Resume1](../images/Resume1.png)
![Resume2](../images/Resume2.png)

## Mode
Les modes sont des consignes prédéterminées à exécuter à l'exécution de celui-ci. Par exemple, dans l’image ci-dessous, le mode "Présent" qui lors de son exécution exécute la consigne d'activer le type générique relié à l'ouverture des lumières et des prises et de changer le mode de mon thermostat, il détermine en fait le comportement que l'équipement doit avoir lorsque je suis présent dans la pièce. Ici, rien n’est figé, je peux définir autant de modes que je le souhaite pour les utiliser via des scénarios par exemple.

Pour chaque mode :
* Vous pouvez restreindre son exécution selon le mode précédant
* Vous pouvez, pour une meilleure visualisation, configurer une icône à celui-ci.

Pour chaque action :
* Vous pouvez rendre la commande active, dans le cas contraire, elle ne s'exécutera pas.
* Vous pouvez spécifier que la commande s'exécute en parallèle
* Vous pouvez restreindre son exécution selon le mode précédant
* Vous pouvez restreindre son exécution selon l'entité qui exécute le mode (le système, un utilisateur ou les deux) (à venir)

![Mode1](../images/Mode1.png)

## Variable
Les variables, permettent de sauvegarder des valeurs qui pourront être utilisées dans un mode par exemple ou modifiées par un scénario. Par exemple, dans l'exemple illustré, j'utilise "Max lux for light" pour configurer la luminausité maximal pour l'ouverture des lumières.

![Variable1](../images/Variable1.png)

Une fois configurées, elles peuvent être visualisées sur le dashbord en cliquant sur le "I" en haut à droite de la tuile.

![Variable2](../images/Variable2.png)

## Tâche
Les tâches, permettent d'ajouter à votre équipement des consignes prédéfinies au changement de valeur d'une variable prédéfini. Exemple : mettre le % par défault de l'ouverture des lumière la nuit à 1%.

* Déclencheur
  * Activer : permet de rendre la vérification active, dans le cas contraire, elle ne sera pas exécuté.
  * Commande : valeur de la commande qui déclanche la vérification
  * Condition : condition qui doit être valide pour exécuter les actions
* Action
  * Activer : permet de rendre l'action active, dans le cas contraire, elle ne sera pas exécuté.
  * Exécution: permet de spécifier que l'action s'exécute en parallèle
  
![Task1](../images/Task1.png)

# Exemple

## Exemple de différent type générique
Voici la configuration des équipements qui s'applique à toutes mes pièces internes qui me servent à les contrôler, dans ce cas, la pièce "RC - Pièce commune" qui est une pièce a aire ouverte incluant trois pièces distincte "RC - Sallon, RC - Salle à manger et RC - Cuisine". Ces trois pièces disposent de capteur de mouvements, luminosité et ouverture de porte et d'actionneur de lumières.

## NONE
Pour être en mesure de mettre mes pièces en mode "Veille" ou "Absence", je calcule le maximum de deux valeurs que possède chacun des profils de la maison soit (Present ou Proximité). Donc si une seule de ces valeurs binaire est à un, le résultat du résumé sera à 1. Mais comme ces commandes ne sont pas dans l'objet parent de l'équipement ou l'un de ces enfants, j'ai ajouté chacune des commandes manuellement. 

![RésuméNone](../images/RésuméNone.png)

Sur le dashbord l'équipement a donc cette apparence et vous pouvez voir l'icône configurée dans le résumé au niveau de la bande supérieure de la tuile de l'équipement puisqu'il s'agit d'une information sans possibilitée d'action. 

![DashbordNone](../images/DashbordNone.png)

## Type générique sans actionneur
Un type générique sans actionneur est un type générique associé à des commandes qui n'ont aucune commande d'action relié à celle-ci.

Pour être en mesure de mettre mes pièces en mode "Présent", j'ajoute un résumé qui regroupe mes capteurs de présence. Donc je choisis comme type générique "Présence", je spécifie les bonnes informations générales et je sauvegarde mes modifications. Normalement, une fois, ceci fait vous devriez voir apparaître dans "Action sur la valeur du résumé si" les commandes contenue sous l'objet parent ou l'un de ces enfants qui ont ce type générique. 

![RésuméInfo](../images/RésuméInfo.png)

Sur le dashbord l'équipement à donc maintenant cette apparence et vous pouvez voir l'icône configurée dans le résumé au niveau de la bande supérieure de la tuile de l'équipement puisqu'il s'agit d'une information. 

![DashbordInfo](../images/DashbordInfo.png)

## Type générique avec actionneur
Un type générique avec actionneur est un type générique associé à des commandes qui ont des commandes d'action relié à celle-ci.

Pour être en mesure d'ouvrir les lumières de ma pièce, j'ajoute donc un résumé qui regroupe les commande me donnant l'état de mes lumière. Donc je choisis comme type générique "Lumière état", je spécifie les bonnes informations générales et je sauvegarde mes modifications. Normalement, une fois, ceci fait vous devriez voir apparaître dans "Action sur la valeur du résumé si" les commandes contenue sous l'objet parent ou l'un de ces enfants qui ont ce type générique. 

![RésuméAction](../images/RésuméAction.png)

Sur le dashbord l'équipement a donc maintenant cette apparence et vous pouvez voir l'icône configurée dans le résumé au niveau de la bande inférieur de la tuile de l'équipement puisqu'il s'agit d'une action.
De plus vous disposer dans l'équipement d'une commande pour configurer la valeur par défaut lors de l'activation de l'équipement

![DashbordAction1](../images/DashbordAction1.png)

# À venir
  # Amélioration
    # Résumé
      # Ordonnancer les onglets des résumés (glissé/déplacé ou un index)
      # Ajouter un champ commentaire
    # Variable
      # Ordonnancer les variables (glissé/déplacé ou un index)
    # General
      # Ajouter un champ commentaire

  # Correction

# FAQ
Pour toute question, suggestion ou problème, écrivez-moi au fobsoft@gmail.com 

# Changelog
[Lien vers le changelog](./changelog.md)
