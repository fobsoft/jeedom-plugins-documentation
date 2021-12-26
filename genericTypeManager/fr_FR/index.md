---
layout: default
title: Documentation twilio
lang: fr_FR
pluginId: twilio
---

<div id="title">
<a href="../../../{{site.baseurl}}/{{page.pluginId}}/{{page.lang}}">Plugin {{page.pluginId}}</a>
</div>

# Présentation
Plugins pour gérer vos commandes via leur type générique de manière dinamique. Il se présente de la même manière que les sommaires des objets à la différence que les commandes sont ajouté automatique à l'équipement si celle-ci fait partie de son objet parent ou de l'un de ces enfants. Une fois fait, il vous donnera ces possibilités:
* Créer une commande d'information qui regroupe toutes les commande d'un type générique.
* Créer une commande d'action qui regroupe toutes les commande d'un type générique, par exemple, déverrouiller toute les serrures extérieures.

À venir dans les prochaines versions
* Ajouter des commandes de manière manuelle à un sommaire
* Ajouter des modes à l'équipement avec des actions à exécuter
* Ajouter des actions et conditions aux changements d'une valeur d'une commande d'information.

Ainsi en utilisant ce plugins pour gérer une pièce par exemple, il sera possible lors d'une détection de présence de passer au mode présent de l'équipement et d'exécuter l'ouverture des lumières à la condition que la luminosité soit plus petite qu'une valeur prédéterminée.

> Le plugin est encore jeune et peut encore comporter quelques bugs mais il évolue régulièrement : n’hésitez pas à me contacter à mon courriel personnel, sois le fobsoft@gmail.com avec toutes vos remarques et suggestions.

# Installation et Configuration du plugins
Pour l'instant, le plugins ne dispose pas d'information générique pour son fonctionnement. Par contre vous pouvez le constater deux crons peuvent activé, elles servent à faire l'ajoute de nouvelle commande à l'équipement. Donc si vous ne prévoyez pas l'ajout de plusieurs équipements, vous pouvez désactiver celle qui roule aux cinq minutes. Une fois activé, on peut donc passer directement à la création d'un équipement.

![Installation et Configuration - 1](../images/Installation%20et%20Configuration%20-%201.png)

# Configuration des équipements

Les équipements sont accessibles à partir du menu Plugins → Organisation → Agenda.

Sur cette page vous retrouvez la liste de vos équipements. Cliquez sur un équipement pour accéder à sa configuration:


# FAQ
Pour toute question ou problème, écrivez-moi au fobsoft@gmail.com 

# Changelog
[Lien vers le changelog](./changelog.md)
