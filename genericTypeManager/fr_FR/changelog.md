---
layout: default
title: Changelog Generic Type Manager
lang: fr_FR
pluginId: genericTypeManager
---

<div id="title">
<a href="../../../{{site.baseurl}}/{{page.pluginId}}/{{page.lang}}">Plugin {{page.title}}</a>
</div>

# Beta

## 2022/10/11
- Ajout de la possibiliter de configurer une valeur au variable directement dans la maintenance

## 2022/06/10
- Fixe erreur suite à la verson du 2022/06/07
- Fixe erreur pour le resort du résumé

## 2022/06/09
- Fixe erreur suite à la verson du 2022/06/07

## 2022/06/07
- Ajout d'une configuration de valeur minimum et maximum dans le sommaire. Ainsi lors d'échange avec une commande, une règle de 3 est appliqué pour calculer la valeur de la commande. 

## 2022/06/05
- Correction de l'affichage de la tuile lorsqu'un meme type generic est utilisé plusieurs fois
- Envoi de la valeur trigger lors de l'execution d'un scenario pur utiliser dans celui-ci les tags référent à la commande exécutante

## 2022/05/30
- Correction de fermeture de lumière via  la tuile
## 2022/04/23
- Correction d'effacement de variable
## 2022/04/18
- Ajouter la possibilité d'appliquer une formule pour le calcul des sommaires
- Ajouter la possibilité de ré-ordonner les modes
- Ajouter la possibilité de ré-ordonner les variables
- Ajouter la possibilité de ré-ordonner les taches
- Ajouter la possibilité de ré-ordonner les onglets des résumés
## 2022/04/13
- Ajout d'un champ descripton sous l'onglet "Equipement"
- Permettre d'afficher ou non le temps sous le widget d'un résumé
- Modificaion de l'affichage des log
- Correction d'un bug lors de la sélection d'un onglet d'un résumé si il y a des caractères spéciaux dans le nom de celui-ci
## 2022/03/28
- Accès non autorisé lors de l'affichage des logs
- Correction d'effacement de commande suite à la suppression d'un résumé
## 2022/03/01
- Un listener déclenché est disabler 5 sec, pour éviter le re-declanchement pour une meme valeur
- Sécurité ajouté lorsque l'on tente une ouverture d'un type générique et que le slider est à 0, cette action est annulé
- Sécurité ajouter lorsque la première commande d'un mode est un sleep et que celui-ci est a 0, l'exécution du mode est annulé
## 2022/02/17
- Modification de l'affichage des logs
- Modification des règles de comparaison
## 2022/01/10
- Ajout de modes à l'équipement avec des actions à exécuter
- Ajout d'es 'actions aux changements d'une commande d'information.
- Ajout de variables.
## 2022/01/22
- Ajout du bouton pour dupliquer l'équipement
- Log
-- Modification de l'arborescence des logs selon le type de log le plus élevé
-- Ajout de configurations pour l'affichage des logs dans la configuration du plugin
- Ajout du temps dans les widgets
- Ajout d'une fonctionnalité de tâche (l'exécution de commandes, lorsqu'une commande prédéfinie change de valeur)
  
## À venir
- Ajouter la possibilité de modifier le comportement des calcules via le plugin advanceScenario
- Ajouter l'action d'un mode s'il doit être exécuté que si le mode est déclenché par : (un utilisateur, le système ou les deux)
- Après sauvegarde, retourner au dernier onglet sélecionné
- Ajouter des conditions à l'exécution des modes