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
  * #parentLog#: Objet parent du déclencheur du scénario, si le nom des objets son remplacer dans la spécification des équipements ex: [#parentLog#][Lumiere][On], le scénario peut etre utilise pour n'importe quel objet. (A venir)
* Ajout de block
  * Pour chaque: Permet de réaliser une action pour chaque élément d'un tableau. (A venir)
  * Tant que: Permet de réaliser une action tant que la condition est valide. (A venir)
* Ajout d'opérateur
  * arrayIn(valeur, tableau): Permet de déterminer si une valeur est contenue dans l'array
  * arrayNotin(valeur, tableau): Permet de déterminer si une valeur n'est pas contenue dans l'array
* Ajout de commande
  * Ajout d'une valeur à un tableau: Création/ajout d’une valeur à un tableau (n'existe que pendant l'exécution du scénario.)
  * Supprimer une valeur d'un tableau: Suppression d’une valeur d’un tableau
  * Afficher les tags dans le log: Permet d'afficher dans le log toutes les valeurs associées à l'exécution du scénario (tag, tableau)
  * Afficher les variables dans le log: Permet d'afficher dans le log toutes les variavles
  * Exécuter un type générique: Permet d'exécuter les commandes des équipements d'un type générique (A venir)
  * Rediriger vers: Permet de rediriger le flow vers un noeud
  
# Table des matières
- [Présentation](#présentation)
- [Table des matières](#table-des-matières)
- [Installation et Configuration du plugins](#installation-et-configuration-du-plugins)
- [Configuration d'un scénario](#configuration-dun-scénario)
  - [Général](#général)
  - [Flow](#flow)
- [Exemple](#exemple)
  - [Exemple d'une boucle for avec compteur](#exemple-dune-boucle-for-avec-compteur)
  - [Exemple d'ajout de valeur à un tableau](#exemple-dajout-de-valeur-à-un-tableau)
  - [Exemple de supression d'une valeur d'un tableau](#exemple-de-supression-dune-valeur-dun-tableau)
- [A Tester](#a-tester)
- [A faire](#a-faire)

# Installation et Configuration du plugins
Dans la section, "Configuration" se trouve quelques options pour configurer l'affichage des logs du plugin.
Une fois le plugin activé, on peut donc passer directement à la création et modification de ceux-ci.

# Configuration d'un scénario
> Attention, il sera possible de convertir vos scénarios issus de Jeedom vers ce plugin, mais l'inverse ne sera pas possible.

Vous pouvez accéder à la fenêtre de maintenance à partir du menu Plugins → Programmation → Advance Scenario.

Sur cette page, vous retrouvez la liste de vos scénarios comme à l'habituelle. Ceux avec un icône vert son des scénarios qui ne sont pas convertis, et ceux de couleur gris sont des scénarios converti.
Une fois converti l'édition d'un scénario via la maintenance de Jeedom n'aura pas d'effet sur celui-ci.
Cliquez sur un scénario pour accéder à sa configuration ou sur "Ajouter" pour en créer un nouveau:

![Config1](../images/Config1.png)

## Général

Dans cette oonglet vous disposer des meme information que dans un scenario normal mise à par le fait qu'il n'y a pas de section pour les declancheur puisue ceux-ci sont gere directement dans le flow.

![Config2](../images/Config2.png)

## Flow

- Fonctionnalité
  - `Supprimer un noeud`: Touches "Effacer" du clavier une fois le noeud ou la connection sélectionné.
  - `Supprimer une connection`: Touches "Effacer" du clavier une fois la connection sélectionnée.
  - `Option d'édition d'un noeud`: Clic droit de la sourie sur le noeud pour afficher l'éditeur du noeud (Appui long pour mobile) (à venir)
  - `Déplacer un noeud`: Clic gauche de la sourie appuyez sur le noeud
  - `Zoom avant/arrière`: Ctrl + Molette de la souris (Pincement pour mobile)
  - `Masquer le block`: Dans notre cas, il n'y a aucune manière de le masquer
  - `Autoriser ou non la répétition`: Dans notre cas, cette option se trouve en haut à gauche du titre du noeud
  - `Aciver/Désactiver un noeud`: dans notre cas, cette options se trouve en haut à gauche du titre du noeud sous forme d'un crochet
  - `Bouton de rechercher`: dans notre cas, les options de recherche se trouve en haut à droite du titre
  - `Copier`, aucune option de disponible pour le moment
  - `Coller`, aucune option de disponible pour le moment      

  Voici un exemple comparatif
    
  ![NoeudSiAvant](../images/NoeudSiAvant.png)![NoeudSiApres](../images/NoeudSiApres.png)

- Partie Droite
  Vous disposez à droite de l'écran des actions habituel d'un scénario, il suffit d'un "drag and drop" vers la droite pour en ajouter. Je ne documenterais pas le fonctionnement de chacune de ces actions, puisqu'il y a déjà une documentation dédiée à ceux-ci.
  Les déclencheurs du scénario se trouvent dans la première boite nommée "Déclencheur".

- Partie Gauche
  - Caractéristiques générales
    - Chaque nœud peut avoir de multiples connections, si tel est le cas, ceux-ci sont exécutés en parallèle.
    - Un premier nœud est ajouté par défaut, celui marque le départ du flow. Ne pas supprimer, puisqu'il est utilisé lorsqu'il n'y a pas d'autre déclencheur ou lorsque vous tester le scénario.
    
      ![NoeudDepart](../images/NoeudDepart.png)
  - Option général d'un block
    - Et dans un block d'un scénario, nous disposons de certaines options avec ces icônes. ![NoeudOption1](../images/NoeudOption1.png)

# Exemple

## Exemple d'une boucle for avec compteur

Comme vous pouvez le constater, vous disposer d'un tag qui est incrémenté à chaque tour portant dont la syntaxe du nom est "#cntFor[NodeId]#".

![Flow1](../images/exFor.png)

```html
BEGIN for (15)
  BEGIN DO
    BEGIN logTag (19)
      Tag:
       [#cntFor15#] => 1
    END 
  END DO
  BEGIN DO
    BEGIN logTag (19)
      Tag:
       [#cntFor15#] => 2
    END 
  END DO
END 
```

## Exemple d'ajout de valeur à un tableau
  - arrayAdd (21): Ajout de la valeur 1
  - arrayAdd (23): Ajout des valeurs 3,7,10,100,200 sous la forme d'un Json dont les virgules sont remplacées par des ;
  - arrayAdd (24): Ajout de la valeur de la commande #[RC - Pièce commune][Room config][Max lux for light]#
  - arrayAdd (29): Ajout de la valeur de la variable #pctLight#

![Flow1](../images/arrayAdd.png)

```html
BEGIN log (22)
  Test avec valeur numerique
END 
BEGIN arrayAdd (21)
  Mise à jour du tag tagArrayNum => [1]
END 
BEGIN arrayAdd (23)
  Mise à jour du tag tagArrayNum => [1,3,7,10,100,200]
END 
BEGIN arrayAdd (24)
  Mise à jour du tag tagArrayNum => [1,3,7,10,100,200,30]
END 
BEGIN arrayAdd (29)
  Mise à jour du tag tagArrayNum => [1,3,7,10,100,200,30,95]
END 
BEGIN logTag (28)
  Tag:
   [#tagArrayNum#] => [1,3,7,10,100,200,30,95]
END 
```

## Exemple de supression d'une valeur d'un tableau
 - arrayRemove (26): Supression de la valeur 3
 - arrayRemove (27): Supression des valeurs 100,200 sous la forme d'un Json dont les virgules sont remplacées par des ;

![Flow1](../images/arrayRemove.png)

````html
BEGIN arrayRemove (26)
  Mise à jour du tag tagArrayNum => {"0":1,"2":7,"3":10,"4":100,"5":200,"6":30,"7":95,"8":1}
END 
BEGIN arrayRemove (27)
  Mise à jour du tag tagArrayNum => {"0":1,"2":7,"3":10,"6":30,"7":95,"8":1}
END 
````

# A Tester

| Déclencheur |  |  |
| :------- | :------- | :--- |
|   | `Evénement` | À venir | 
|   | `Programmation` | À venir | 
| Général |  |  |
| :------- | :------- | :--- |
|   | `Si/Alors/Sinon` | <span style="color:green">Pass</span> | 
|   | `Boucle` | <span style="color:green">Pass</span> | 
|   | `Pour chaque` | À venir | 
|   | `Tant que` | À venir | 
| Variable |  |  |
| :-  | :------- | :--- |
|     | `Tag`                                 | <span style="color:green">Pass</span> | 
|     | `Ajout d'une valeur à un tableau`     | <span style="color:green">Pass</span> | 
|     | `Supprimer une variable d'un tableau` | <span style="color:green">Pass</span> | 
|     | `Variable`                            | <span style="color:green">Pass</span> | 
|     | `Rediriger vers`                      | <span style="color:green">Pass</span> | 
| Flux |  |  |
| :------- | :------- | :--- |
|   | `Stop` | À venir | 
|   | `Attendre` | À venir | 
|   | `Pause` | À venir | 
|   | `Dans` | À venir | 
|   | `A` | À venir | 
|   | `Scénario` | À venir | 
|   | `Retourner un texte/une donnée` | À venir | 
|   | `Supprimer tous les bloc programmé` | À venir | 
|   | `Supprimer un bloc programmé` | À venir | 
|   | `Supprimer un bloc programmé` | À venir | 
| Interface |  |  |
| :------- | :------- | :--- |
|   | `Aller au design` | À venir | 
|   | `Icône` | À venir | 
|   | `Coloration des icones` | À venir | 
| Messagerie |  |  |
| :------- | :------- | :--- |
|   | `Ajouter un log` | <span style="color:green">Pass</span> | 
|   | `Afficher les tags dans le log` | <span style="color:green">Pass</span> | 
|   | `Afficher les variables dans le log` | <span style="color:green">Pass</span> | 
|   | `Afficher les noeuds dans le log` | <span style="color:green">Pass</span> | 
|   | `Créer un message` | À venir | 
|   | `Faire une demande` | À venir | 
|   | `Dire` | À venir | 
|   | `Alerte` | À venir | 
|   | `Pop-up` | À venir | 
|   | `Commentaire` | À venir | 
|   | `Rapport` | À venir | 
| Système |  |  |
| :------- | :------- | :--- |
|   | `Arrêter` | À venir | 
|   | `Redémarrer` | À venir | 
| Équipement |  |  |
| :------- | :------- | :--- |
|   | `Activer un équipement` | À venir | 
|   | `Désactiver un équipement` | À venir | 
|   | `Masquer un équipement` | À venir | 
|   | `Afficher un équipement` | À venir | 
|   | `Générer un evènement` | À venir | 
|   | `Exécuter une commande` | À venir | 
|   | `Exécuter un type générique` | À venir | 
| Programmation |  |  |
| :------- | :------- | :--- |
|   | `code` | À venir |
| Autre |  |  |
| :------- | :------- | :--- |
|   | Scenario | À venir |

# A faire
* Empécher la suppression du node "Départ" puisque celui-ci est le point d'entré général
* Ajouter un bouton test, pour tester le flow du scénario et ainsi voir son issue
* Aciver/Désactiver un noeud
* Autoriser ou non la répétition des actions si l\'évaluation de la condition est la même que la précédente
* Copier/Coller un noeud