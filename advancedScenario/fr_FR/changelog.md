---
layout: default
title: Changelog Advanced Scenario
lang: fr_FR
pluginId: advancedScenario
---

<div id="title">
<a href="../../../{{site.baseurl}}/{{page.pluginId}}/{{page.lang}}">Plugin {{page.pluginId}}</a>
</div>

# Beta

## 2022/11/03
- Création d'une maintenance dans le panel pour créer de nouveau type générique
- Correction mineur

## 2022/06/06
- Action
  - Équipement
    - Exécuter un type générique
- Function
  - D'information
    - Équipement
      - getListEquipement(object,includeChild): Renvoie la liste des équipements contenue sous l'objet et ses enfants si spécifiés
    - Type générique
      - getListCmdByGenericType(generic,object,includeChild) : Renvoie la liste des commandes possèdant le type générique spécifié contenue sous l'objet et ses enfants si spécifiés

## 2022/05/05
- Permettre le copier coller d'un noeud
 
## 2021/12/25
- Création du plugin

# A faire
* Général
  * Empécher la suppression du node "Départ" puisque celui-ci est le point d'entré général
* Noeud
  * Aciver/Désactiver un noeud
  * Permettent d’activer ou non la répétition des actions si l’évaluation de la condition donne le même résultat que la précedente évaluation.
  * Ajouter une mainenance pour avoir plus d'option pour la création de l'expression du noeud sans trop charger la page principal.
  * Ajouter un bouton pour sélectionner les tags disponible
  * Ajouter un bouton pour sélectionner une fonction mathématique
* Commande
  * Boucle: Ajouter la possibilité de sélectionné un type générique
  * Si/Alors/Sinon: Autoriser ou non la répétition des actions si l\'évaluation de la condition est la même que la précédente
  * Switch: Ajouter cette commande pour éviter d'avoir des Si / Sinon bout en bout 
* Log
  * Travailler le visuel du log lors d'exécution en parallèle
* Déclencheurs
  * Ajouter un bouton pour sélectionner un déclancheur
  * Ajouter un bouton pour sélectionner une variable