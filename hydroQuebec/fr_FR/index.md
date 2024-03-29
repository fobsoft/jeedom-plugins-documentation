---
layout: default
title: Documentation Hydro Québec
lang: fr_FR
pluginId: hydroQuebec
---

<div id="title">
<a href="../../../{{site.baseurl}}/{{page.pluginId}}/{{page.lang}}">{{page.title}}</a>
</div>

>> Suite à la nouvelle reçue d'Hydro-Québec que leur portail client actuelle ne sera plus disponible à partir du 15 avril et que se plugin s'appuie sur celui-ci, il n'est désormais plus disponible pour le moment. Aucune information d'Hydro-Québec ne nous indique qu'il y aura ou non un API de disponible pour récupérer nos informations. À suivre...

> Le plugin est encore jeune et peut encore comporter quelques bugs, mais il évolue régulièrement : n’hésitez pas à me contacter à mon courriel personnel, sois le fobsoft@gmail.com avec toutes vos remarques et suggestions.

# Présentation
Plugin permettant de récupérer les informations de consommation électrique et des événements d'Hydro-Québec (wwww.hydroquebec.com), et de créer des crons en fonction des événements

# Installation et Configuration du plugins

Dans la section, "Dépendances", vous devrez lancer l'installation des dépendances, ceci ne dureraa que quelque minutes.

Dans la section, "Configuration", se trouve quelques options pour configurer l'affichage des logs du plugin.

Dans la section "Fonctionnalités", vous pouvez constater une cron, elle sert à récupérer vos informations de consommation et les événements à venir.

Une fois le plugin activé, on peut donc passer directement à la création d'un équipement.

# Configuration des équipements
Les équipements sont accessibles à partir du menu Plugins → Energie → Hydro Quebec.

Sur cette page vous retrouvez la liste de vos équipements. Cliquez sur un équipement pour accéder à sa configuration ou sur "Ajouter" pour en créer un nouveau:

## Équipement
* Paramètres généraux
  * Nom de l'équipement : nom de votre équipement.
  * Objet parent : indique l’objet parent auquel appartient l’équipement.
  * Catégorie : indique la oou les catégories auquel l’équipement fait référence.
  * Activer : permet de rendre l’équipement actif.
  * Visible : permet de rendre l’équipement visible sur le dashboard.
* Paramètres spécifiques
  * Nom d'utilisateur : Renseignez votre nom d'utilisateur de votre compte client d'hydro-québec (celui que vous utilisez lorsque vousvous conntez sur le site d'Hydro-Québec)
  * Mot de passe : Renseignez votre mot de passe de votre compte client d'hydro-québec (celui que vous utilisez lorsque vousvous conntez sur le site d'Hydro-Québec)
  * Numéro de client : Renseignez votre numéro de client de votre compte client d'hydro-québec (10 caractères numériques sans espace)
  * Numéro du contrat : Renseignez votre numéro de contrat de votre compte client d'hydro-québec (9 caractères numériques sans espace)

Pour connaître vos informations de client et contrat, connectez-vous à votre compte d'Hydro-Québec, 
   
   Votre numéro de contrat, ce trouve sous l'onglet Sommaire.

  ![contrat](../images/contrat.png)

   Pour votre numéro de client, cliquer sur votre nom.

  ![client1](../images/client1.png)
  ![client2](../images/client2.png)

Et voici un aperçu du résultat

![equipement](../images/equipement.png)
  
## Cédules
Les cédules permettent d'exécuter des consignes à une heure prédéterminé, pour chaque consigne, vous pouvez indiquer si celle-ci doit toujours être exécute ou si elle doit l'être que s'il y a un événement en am et ou en pm.

![Mode1](../images/Mode1.png)

## Commandes
Affiche la liste des commandes d'informations créés selon les informations reçus par Hydro-Québec..

# FAQ
Pour toute question, suggestion ou problème, écrivez-moi au fobsoft@gmail.com 

# Changelog
[Lien vers le changelog](./changelog.md)
