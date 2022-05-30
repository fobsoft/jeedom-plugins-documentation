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
  * En rapport au scénario:
    * #scenarioObject#: Objet parent du scénario, si le nom des objets son remplacer dans la spécification des équipements ex: #tag(scenarioObject,0)[Lumiere][On]#, le scénario peut etre utilise pour n'importe quel objet.
  * En rapport à la commande qui à déclanché le scénario
    * #trigger#: Son nom (ex:)
    * #triggerGenericType#: Son type générique (ex:)
    * #triggerEq#: Le nom de l'équipement (ex:)
  * En rapport à l'exécution du scénario:
    * #triggerObject#: Le nom de l'object parent de la commande, sinon le nom de l'object parent du scénario
* Ajout de block
  * Pour chaque: Permet de réaliser une action pour chaque élément d'un tableau.
  * Tant que: Permet de réaliser une action tant que la condition est valide.
* Ajout d'opérateur
  * arrayIn(valeur, tableau): Permet de déterminer si une valeur est contenue dans l'array
  * arrayNotin(valeur, tableau): Permet de déterminer si une valeur n'est pas contenue dans l'array
* Ajout de commande
  * Ajout d'une valeur à un tableau: Création/ajout d’une valeur à un tableau (n'existe que pendant l'exécution du scénario.)
  * Supprimer une valeur d'un tableau: Suppression d’une valeur d’un tableau
  * Afficher les tags dans le log: Permet d'afficher dans le log toutes les valeurs associées à l'exécution du scénario (tag, tableau)
  * Afficher les variables dans le log: Permet d'afficher dans le log toutes les variavles
  * Exécuter un type générique: Permet d'exécuter les commandes des équipements d'un type générique
  * Rediriger vers: Permet de rediriger le flow vers un noeud
  * Supprimer un noeud programmé
* Modification général:
  * Ajout de boutons supplémentaire pour facilité la gestion des expressions
  
# Lexique
* Opérande: Un opérande est une commande ou variable, ou tag, ou fonction de type info qui nous retourne une valeur de type info.
* Opérateur de comparaison: Comme leur nom l'indique, ils vous permettent de comparer deux opérandes.
* Expression de comparaison: C'est une expression qui est constituée de deux opérandes sépare par un opérateur de comparaison ou une seul opérande de type booléen.
* Expression conditionnelle: Une expression conditionnel est constitué d'une expression de comparaison ou de plusieurs expression de comparaison séparé par  un liens d'expression de comparaison.

# Installation et Configuration du plugins
Dans la section, "Configuration" se trouve quelques options pour configurer l'affichage des logs du plugin.
Une fois le plugin activé, on peut donc passer directement à la création et modification de ceux-ci.

# Configuration d'un scénario
> Attention, il sera possible de convertir vos scénarios issus de Jeedom vers ce plugin dans une version futur, mais l'inverse ne sera pas possible.

Vous pouvez accéder à la fenêtre de maintenance à partir du menu Plugins → Programmation → Advance Scenario.

Sur cette page, vous retrouvez la liste des groupes issus des scénarios de Jeedom et les scénarios créé à partir du plugin sont affichés avec une icône de couleur grise. Lorsqu'il sera possible de convertir vos scénarios issus de Jeedom, ceux-ci apparaîtront avec une icône verte.

Cliquez sur un scénario pour accéder à sa configuration ou sur "Ajouter" pour en créer un nouveau:

![Config1](../images/Config1.png)

## Général

Dans cette onglet vous disposez des meme information que dans un scénario normal mise à part le fait qu'il n'y a pas de section pour les déclencheurs puisque ceux-ci sont géré directement dans le flow.

Dans l’onglet Général, on retrouve les paramètres principaux de notre scénario :
•	Nom du scénario : Le nom de votre scénario.
•	Nom à afficher : Le nom utilisé pour son affichage.
•	Groupe : Permet d’organiser les scénarios, en les classant dans des groupes.
•	Actif : Permet d’activer le scénario.
•	Visible : Permet de rendre visible le scénario.
•	Objet parent : Affectation à un objet parent.
•	Timeout secondes (0 = illimité) : La durée d’exécution maximale autorisée
•	Multi lancement : Cochez cette case si vous souhaitez que le scénario puisse être lancé plusieurs fois en même temps.
•	Mode synchrone : Lance le scénario dans le thread courant au lieu d’un thread dédié. Ca permet d’augmenter la vitesse de lancement du scénario mais cela peut rendre le système instable.
•	Log : Le type de log souhaité pour le scénario. (bypass la config du pluggin - A faire)
•	Suivre dans la timeline : Permet de garder un suivi du scénario dans la timeline.
•	Description : Permet d’écrire un petit texte pour décrire votre scénario.

![Config2](../images/Config2.png)

## Flow
C'est ici que vous allez construire votre scénario. 

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
  - `Copier`, Ctrl + c
  - `Coller`, Ctrl + v 
- Caractéristiques générales
  - Chaque nœud peut avoir de multiples connections, si tel est le cas, ceux-ci sont exécutés en parallèle.

- Partie Droite
  
  Vous disposez à droite de l'écran, des déclencheurs dans la première boite nommée "Déclencheur" suivi des actions disponibles, il suffit d'un "drag and drop" vers la droite pour en ajouter. Nous verrons plus loin la documentation de chacun.

  ![Left](../images/left.png)

- Partie Gauche
  - Un premier nœud est ajouté par défaut, celui-ci marque le départ du flow. Ne pas supprimer, puisqu'il est utilisé lorsqu'il n'y a pas d'autre déclencheur ou lorsque vous tester le scénario.    
  
    ![NoeudDepart](../images/NoeudDepart.png)
  
  - Chacun des nœuds dispose de certaines fonctionnalités
    - La case à cocher, à gauche, permet de désactiver complètement le bloc sans pour autant le supprimer.
    - Les flèches circulaires permettent d’activer ou non la répétition des actions si l’évaluation de la condition donne le même résultat que la précedente évaluation.
    - Les icônes. (encerclé en rouge).
      - Sélection d'une commande : Permet de chercher une commande dans toutes celles disponibles dans Jeedom
      - Sélection d'une variable : Permet de chercher des variables issues du scénario ou d’un autre scénario
      - Sélection d'un mot-clé : Permet de chercher des tags du scénario ou spécifiques à Jeedom
      - Sélection d'une function: Permet de spécifier une valeur à l'aide d'une fonction (a faire)
      - Une maintenance pour construire une expression conditionnelle complexe
  
    ![NoeudOption1](../images/NoeudOption1.png)

  - Si un nœud est lié à plusieurs nœuds, ceux-ci seront exécutés en parallèle

# Action
<ul>
  <li>
    <h2>Déclencheur (ce qui déclennche le scénario)</h2>
    <ul>
      <li><b>Evénement</b> 
        (dans l'ordre de l'affichage des bouttons)
        <ol>
          <li>Commande de type info</li>
          <li>Type générique de type info</li>
          <li>Tag de déclanchement</li>
          <li>Function de déclanchement</li>
        </ol>
      </li>
      <li><b>Programmation</b> : pour déterminer le moment d'exécuter le scénario et sa récurrence</li>
    </ul>
    <h2>Général</h2>
    <ul>
      <li><b>Si/Alors/Sinon</b> : Permet de réaliser des actions selon une expression conditionnelle.</li>
      <li><b>Switch</b> : Permet de réaliser des actions en comparent la même variable (ou expression conditionnelle) avec un grand nombre de valeurs différentes, et d'exécuter      différentes actions suivant la valeur à laquelle elle est égale. (À venir)</li>
      <li><b>Boucle</b> : Permet de réaliser des actions de manière répétitive de 1 jusqu’à un nombre défini (ou même la valeur d’un capteur, ou un nombre aléatoire…).</li>
      <li><b>Pour chaque</b> : </li>
      <li><b>Tant que</b> : </li>
    </ul>
    <h2>Variable</h2>
    <ul>
      <li><b>Tag</b> : </li>
      <li><b>Ajout d'une valeur à un tableau</b> : </li>
      <li><b>Supprimer une variable d'un tableau</b> : </li>
      <li><b>Variable</b> : </li>
      <li><b>Supprimer une variable</b> : </li>
    </ul>
    <h2>Flux</h2>
    <ul>
      <li><b>Stop</b> : </li>
      <li><b>Pause</b> : </li>
      <li><b>Dans</b> : Permet de lancer une action dans X minute(s) (0 est une valeur possible). La particularité est que les actions sont lancées en arrière-plan, elles ne bloquent donc pas la suite du scénario. C’est donc un bloc non bloquant.</li>
      <li><b>A</b> : Permet de dire à Jeedom de lancer les actions du bloc à une heure donnée (sous la forme hhmm). Ce bloc est non bloquant. Ex : 0030 pour 00h30, ou 0146 pour 1h46 et 1050 pour 10h50.</li>
      <li><b>Retourner un texte/une donnée</b> : </li>
      <li><b>Supprimer tous les noeuds programmé</b> : </li>
      <li><b>Supprimer un noeud programmé</b> : (a venir)</li>
      <li><b>Rediriger vers</b> : </li>
    </ul>
    <h2>Interface</h2>
    <ul>
      <li><b>Aller au design</b> : </li>
      <li><b>Icône</b> : </li>
      <li><b>Coloration des icones</b> : </li>
    </ul>
    <h2>Messagerie</h2>
    <ul>
      <li><b>Ajouter un log</b> : </li>
      <li><b>Afficher les tags dans le log</b> : </li>
      <li><b>Afficher les variables dans le log</b> : </li>
      <li><b>Afficher les noeuds dans le log</b> : </li>
      <li><b>Créer un message</b> : </li>
      <li><b>Faire une demande</b> : </li>
      <li><b>Dire</b> : </li>
      <li><b>Alerte</b> : </li>
      <li><b>Pop-up</b> : </li>
      <li><b>Commentaire</b> : Permet d’ajouter des commentaires à son scénario (À venir)</li>
      <li><b>Rapport</b> : (À venir)</li>
    </ul>
    <h2>Système</h2>
    <ul>
      <li><b>Arrêter</b> : </li>
      <li><b>Redémarrer</b> : </li>
    </ul>
    <h2>Équipement</h2>
    <ul>
      <li><b>Activer un équipement</b> : </li>
      <li><b>Désactiver un équipement</b> : </li>
      <li><b>Masquer un équipement</b> : </li>
      <li><b>Afficher un équipement</b> : </li>
      <li><b>Générer un evènement</b> : </li>
      <li><b>Exécuter une commande</b> : </li>
      <li><b>Exécuter un type générique</b> : (À venir)</li>
    </ul>
    <h2>Programmation</h2>
    <ul>
      <li><b>Code</b> : Permet d’écrire directement en code PHP (demande certaines connaissances et peut être risqué mais permet de n’avoir aucune contrainte). (À venir)</li>
    </ul>
  </li>
</ul>

# Expression conditionnelle
  ## Opérateurs de comparaison, comme leur nom l'indique, ils vous permettent de comparer deux valeurs.</h2>
  <ul>
    <li><b>==</b> : égal à</li>
    <li><b>></b> : strictement supérieur à</li>
    <li><b>>=</b> : supérieur ou égal à</li>
    <li><b><</b> : strictement inférieur à</li>
    <li><b><=</b> : inférieur ou égal à</li>
    <li><b>!=</b> : différent de, n’est pas égal à</li>
    <li><b>&</b> : comparaison binaire</li>
  </ul>

  ## Liens d'expression de comparaison</h2>
  <ul>
    <li><b>&& / ET / et / AND / and</b> : et</li>
    <li><b>| / OU / ou / OR / or</b> : ou</li>
    <li><b>|^ / XOR / xor</b> : ou exclusif</li>
  </ul>

# Tag
Un tag est remplacé lors de l’exécution du scénario par sa valeur

<ul>
  <li>
    <h2>De déclanchement</h2>
    <ul>
      <li><b>#start#</b> : déclenché au (re)démarrage de Jeedom</li>
      <li><b>#begin_backup#</b> : événement envoyé au début d’une sauvegarde</li>
      <li><b>#end_backup#</b> : événement envoyé à la fin d’une sauvegarde</li>
      <li><b>#begin_update#</b> : événement envoyé au début d’une mise à jour</li>
      <li><b>#end_update#</b> : événement envoyé à la fin d’une mise à jour</li>
      <li><b>#begin_restore#</b> : événement envoyé au début d’une restauration</li>
      <li><b>#end_restore#</b> : événement envoyé à la fin d’une restauration</li>
      <li><b>#user_connect#</b> : connexion d’un utilisateur</li>
    </ul>
  </li>
  <li>
    <h2>D'information</h2>
    <ul>
      <li>
        <h3>Temps</h3>
        <ul>
          <li><b>#seconde#</b> : Seconde courante (sans les zéros initiaux, ex : 6 pour 08:07:06)</li>
          <li><b>#heure#</b> : Heure courante au format 24h (sans les zéros initiaux, ex : 8 pour 08:07:06 ou 17 pour 17:15)</li>
          <li><b>#heure12#</b> : Heure courante au format 12h (sans les zéros initiaux, ex : 8 pour 08:07:06)</li>
          <li><b>#minute#</b> : Minute courante (sans les zéros initiaux, ex : 7 pour 08:07:06)</li>
          <li><b>#jour#</b> : Jour courant (sans les zéros initiaux, ex : 6 pour 06/07/2017)</li>
          <li><b>#mois#</b> : Mois courant (sans les zéros initiaux, ex : 7 pour 06/07/2017)</li>
          <li><b>#annee#</b> : Année courante</li>
          <li><b>#time#</b> : Heure et minute courante (ex : 1715 pour 17h15)</li>
          <li><b>#timestamp#</b> : Nombre de secondes depuis le 1er janvier 1970</li>
          <li><b>#date#</b> : Jour et mois. Attention, le premier nombre est le mois. (ex : 1215 pour le 15 décembre)</li>
          <li><b>#semaine#</b> : Numéro de la semaine (ex : 51)</li>
          <li><b>#sjour#</b> : Nom du jour de la semaine (ex : Samedi)</li>
          <li><b>#njour#</b> : Numéro du jour de 0 (dimanche) à 6 (samedi)</li>
          <li><b>#smois#</b> : Nom du mois (ex : Janvier)</li>
        </ul>
      </li>
      <li>
        <h3>Élément liés à l'exécution du scénario</h3>
        <ul>
          <li><b>#trigger#</b> : Peut être le nom de la commande qui a déclenché le scénario, ‘api’ si le lancement a été déclenché par l’API, ‘schedule’ si il a été lancé par une programmation, ‘user’ si il a été lancé manuellement</li>
          <li><b>#triggerValue#</b> : Valeur de la commande qui à déclanché le scénario</li>
          <li><b>#triggerGenericType#</b> : Type générique de la commande qui à déclanché le scénario</li>
          <li><b>#triggerEq#</b> : Le nom de l’équipement de la commande qui à déclanché le scénario</li>
          <li><b>#triggerObject#</b> : Le nom de l’object parent de la commande qui à déclanché le scénario, sinon le nom de l’object parent du scénario</li>
          <li><b>#profil#</b> : Renvoie le profil de l’utilisateur ayant déclenché le scénario (peut être vide)</li>
          <li><b>#query#</b> : Interaction ayant déclenché le scénario</li>
        </ul>
      </li>
      <li>
        <h3>Réseau</h3>
        <ul>
          <li><b>#IP#</b> : IP interne de Jeedom</li>
          <li><b>#hostname#</b> : Nom de la machine Jeedom</li>
        </ul>
      </li>
    </ul>
  </li>
</ul>

# Function
<ul>
  <li>
    <h2>De déclanchement</h2>
    <ul>
      <li><b>#variable(nom_variable)#</b> : déclencher un scénario quand une variable est mise à jour (a faire)</li>
    </ul>
  </li>
  <li>
    <h2>D'information</h2>
    <ul>
      <li>
        <h3>Retour aléatoire</h3>
        <ul>
          <li><b>randText(texte1;texte2;...)</b> : Renvoie un des textes aléatoirement (séparer les texte par un ; ). Il n’y a pas de limite dans le nombre de texte</li>
          <li><b>color_gradient(couleur_debut,couleur_fin,valuer_min,valeur_max,valeur)</b> : Renvoie une couleur calculé par rapport à valeur dans l’intervalle couleur_debut/couleur_fin. La valeur doit etre comprise entre valeur_min et valeur_max</li>
        </ul>
      </li>  
      <li>
        <h3>Mathématique</h3>
        <ul>
          <li><b>rand(min,max)</b> : Retourner un nombre aléatoire entre les 2 bornes demandées</li>
          <li><b>randomColor(min,max)</b> : Donne une couleur aléatoire compris entre 2 bornes ( 0 => rouge, 50 => vert, 100 => bleu)</li>
          <li><b>round(valeur,[decimal])</b> : Donne un arrondi au-dessus, [decimal] nombre de décimales après la virgule</li>
          <li><b>odd(valeur)</b> : Permet de savoir si un nombre est impair ou non. Renvoie 1 si impair 0 sinon</li>
          <li><b>average(tableau)</b> : Renvoie la valeur moyenne des éléments contenue dans le tableau}} ** A faire</li>
          <li><b>min(tableau)</b> : Renvoie la valeur minimum des éléments contenue dans le tableau}} ** A faire</li>
          <li><b>max(tableau)</b> : Renvoie la valeur maximum des éléments contenue dans le tableau}} ** A faire</li>
        </ul>
      </li>
      <li>
        <h3>Comparaison</h3>
        <ul>
          <li><b>arrayIn(valeur, tableau)</b> : Renvoie 1, si la veleur spécifié se retrouve dans le tableau spécifié}}</li>
          <li><b>arrayNotIn(valeur, tableau)</b> : Renvoie 1, si la veleur spécifié ne se retrouve pas dans le tableau spécifié}}</li>
          <li><b>not(expression)</b> : Renvoie 1, si le résultat de l'expression est faux (ex: not(1 == 2))}} ** A faire</li>
          <li><b>matches</b> : contient (ex : [Salle de bain][Hydrometrie][etat] matches “/humide/” )</li>
        </ul>
      </li>
      <li>
        <h3>Temps</h3>
        <ul>
          <li><b>time(value)</b> : Spécifier une heure (ex : time(1530))</li>
          <li><b>time_op(time,value)</b> : Permet de faire des opérations sur le temps, avec time=temps (ex : 1530) et value = valeur à ajouter ou à soustraire en minutes, doit êttre de type numérique</li>
          <li><b>time_between(time,start,end)</b> : Permet de tester si un temps est entre deux valeurs avec time=temps (ex : 1530), start=temps, end=temps. Les valeurs start et end peuvent être à cheval sur minuit</li>
          <li><b>time_diff(date1,date1[,format])</b> : Renvoie la différence entre 2 dates (les dates doivent être au format AAAA/MM/JJ HH:MM:SS). Par défaut (si vous ne mettez rien pour format), la méthode retourne le nombre total de jours. Vous pouvez lui demander en secondes (s), minutes (m), heures (h). Exemple en secondes time_diff(2018-02-02 14:55:00,2018-02-25 14:55:00,s)</li>
          <li><b>formatTime(time)</b> : Renvoie le retour d’une chaine #time# formaté</li>
          <li><b>floor(time, baseUnit, destUnit)</b> : Renvoie la conversion des secondes en minutes, ou des minutes en heures)}} ** A faire</li>
        </ul>
      </li>
      <li>
        <h3>Liés à l'exécution du scénario</h3>
        <ul>
          <li><b>tag(tag,valeur par défaut)</b> : Renvoie la valeur d’un tag ou la valeur par défaut si il n’existe pas :</li>
          <li><b>variable(variable,valeur par défaut)</b> : Renvoie la valeur d’une variable ou de la valeur souhaitée par défaut</li>
        </ul>
      </li>
      <li>
        <h3>Commande</h3>
        <ul>
          <li><b>average(commande,période)</b> : Renvoie la valeur moyenne de la commande sur la période (period=[month,day,hour,min] ou expression PHP)</li>
          <li><b>averageBetween(commande,start,end)</b> : Renvoie la moyenne de la commande entre les 2 bornes demandées (sous la forme Y-m-d H:i:s ou expression PHP)</li>
          <li><b>min(commande,période)</b> : Renvoie la valeur minimum de la commande sur la période (period=[month,day,hour,min] ou expression PHP)</li>
          <li><b>minBetween(commande,start,end)</b> : Renvoie la valeur minimum de la commande entre les 2 bornes demandées (sous la forme Y-m-d H:i:s ou expression PHP)</li>
          <li><b>max(commande,période)</b> : Renvoie la valeur maximum de la commande sur la période (period=[month,day,hour,min]</li>
          <li><b>maxBetween(commande,start,end)</b> : Renvoie la valeur maximum de la commande entre les 2 bornes demandées (sous la forme Y-m-d H:i:s ou expression PHP)</li>
          <li><b>duration(commande, valeur, période)</b> : Renvoie la durée en minutes pendant laquelle l’équipement avait la valeur choisie sur la période (period=[month,day,hour,min] ou expression PHP)</li>
          <li><b>durationbetween(commande,valeur,start,end)</b> : Renvoie la durée en minutes pendant laquelle l’équipement avait la valeur choisie entre les 2 bornes demandées (sous la forme Y-m-d H:i:s ou expression PHP)</li>
          <li><b>statistics(commande,calcul,période)</b> : Renvoie le résultat de différents calculs statistiques (sum, count, std, variance, avg, min, max) sur la période (period=[month,day,hour,min] ou expression PHP)</li>
          <li><b>statisticsBetween(commande,calcul,start,end)</b> : Renvoie le résultat de différents calculs statistiques (sum, count, std, variance, avg, min, max) entre les 2 bornes demandées (sous la forme Y-m-d H:i:s ou expression PHP)</li>
          <li><b>tendance(commande,période,seuil)</b> : Renvoie la tendance de la commande sur la période (period=[month,day,hour,min] ou expression PHP)</li>
          <li><b>stateDuration(commande)</b> : Renvoie la durée en secondes depuis le dernier changement de valeur. Retourne -1 si aucun historique n’existe ou si la valeur n’existe pas dans l’historique. Retourne -2 si la commande n’est pas historisée</li>
          <li><b>lastChangeStateDuration(commande,valeur)</b> : Renvoie la durée en secondes depuis le dernier changement d’état à la valeur passée en paramètre. Retourne -1 si aucun historique n’existe ou si la valeur n’existe pas dans l’historique. Retourne -2 si la commande n’est pas historisée</li>
          <li><b>lastStateDuration(commande,valeur)</b> : Renvoie la durée en secondes pendant laquelle l’équipement a dernièrement eu la valeur choisie. Retourne -1 si aucun historique n’existe ou si la valeur n’existe pas dans l’historique. Retourne -2 si la commande n’est pas historisée</li>
          <li><b>stateChanges(commande,[valeur], période)</b> : Renvoie le nombre de changements d’état (vers une certaine valeur si indiquée, ou au total sinon) sur la période (period=[month,day,hour,min]</li>
          <li><b>stateChangesBetween(commande, [valeur], start, end)</b> : Renvoie le nombre de changements d’état (vers une certaine valeur si indiquée, ou au total sinon) entre les 2 bornes demandées (sous la forme Y-m-d H:i:s ou expression PHP)</li>
          <li><b>collectDate(commande,[format])</b> : Renvoie la date de la dernière donnée pour la commande donnée en paramètre, le 2ème paramètre optionnel permet de spécifier le format de retour (détails ici). Un retour de -1 signifie que la commande est introuvable et -2 que la commande n’est pas de type info</li>
          <li><b>valueDate(commande,[format])</b> : Renvoie la date de la dernière donnée pour la commande donnée en paramètre, le 2ème paramètre optionnel permet de spécifier le format de retour (détails ici). Un retour de -1 signifie que la commande est introuvable et -2 que la commande n’est pas de type info</li>
          <li><b>value(commande)</b> : Renvoie la valeur d’une commande si elle n’est pas donnée automatiquement par Jeedom (cas lors du stockage du nom de la commande dans une variable)</li>
          <li><b>median(commande1,commande2…​.commandeN)</b> : Renvoie la médiane des valeurs</li>
          <li><b>lastBetween(commande,start,end)</b> : Donne la dernière valeur enregistrée pour l’équipement entre les 2 bornes demandées (sous la forme Y-m-d H:i:s ou expression PHP)</li>
         <li><b>commandeName(commande)</b> : Renvoie le nom de la commande, ex: commandeName(tag(cmd234))</li>
        </ul>
      </li>
      <li>
        <h3>Équipement</h3>
        <ul>
          <li><b>eqEnable(equipement)</b> : Renvoie l’état de l’équipement. -2 si l’équipement est introuvable, 1 si l’équipement est actif et 0 s’il est inactif</li>
          <li><b>lastCommunication(equipment,[format])</b> : Renvoie la date de la dernière communication pour l’équipement donnée en paramètre, le 2ème paramètre optionnel permet de spécifier le format de retour (détails ici). Un retour de -1 signifie que l’équipment est introuvable</li>
          <li><b>equipementName(commande)</b> : Renvoie le nom de l’équipementt</li>
        </ul>
      </li>
      <li>
        <h3>Object</h3>
        <ul>
          <li><b>objectName(nom de la commande)</b> : Renvoie le nom de l’objet}} ** A faire</li>
          <li><b>objectId(nom de l'object)</b> : Renvoie l'id de l'objet}} ** A faire</li>
        </ul>
      </li>
      <li>
        <h3>Scénario</h3>
        <ul>
          <li><b>scenario(scenario)</b> : Renvoie le statut du scénario. 1 en cours, 0 si arrêté et -1 si désactivé, -2 si le scénario n’existe pas et -3 si l’état n’est pas cohérent.</li>
          <li><b>lastScenarioExecution(scenario)</b> : Renvoie la durée en secondes depuis le dernier lancement du scénario.</li>
        </ul>
      </li>
      <li>
        <h3>Type générique</h3>
        <ul>
          <li><b>genericType(generic,object)</b> : Renvoie la liste des commandes possèdant le type générique spécifié contenue sous l'objet et ses enfants si spécifiés</li>
          <li><b>minGenericType(generic,object)</b> : Renvoie la valeur minimum courante des commandes possédant le type générique spécifié contenue sous l'objet et ses enfants si spécifié</li>
          <li><b>maxGenericType(generic,object)</b> : Renvoie la valeur maximum courante des commandes possédant le type générique spécifié contenue sous l'objet et ses enfants si spécifiés</li>
          <li><b>averageGenericType(generic,object)</b> : Renvoie la valeur moyenne courante des commandes possédant le type générique spécifié contenue sous l'objet et ses enfants si spécifiés</li>
        </ul>
      </li>
    </ul>
  </li>
</ul>

# Exemple d'utilisaion de commande

## Boucle for avec compteur

Comme vous pouvez le constater, vous disposer d'un tag qui est incrémenté à chaque tour dont la syntaxe du nom est "#cntFor[NodeId]#". Le log qui suit l'image n'est que la parti du noeud "Boucle" et de l'exécution des commande sous "DO".

![exFor](../images/exFor.png)

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

## Ajout de valeur à un tableau
  - arrayAdd (21): Ajout de la valeur 1
  - arrayAdd (23): Ajout des valeurs 3,7,10,100,200 sous la forme d'un Json dont les virgules sont remplacées par des ";"
  - arrayAdd (24): Ajout de la valeur de la commande #[RC - Pièce commune][Room config][Max lux for light]#
  - arrayAdd (29): Ajout de la valeur de la variable #pctLight#

![arrayAdd](../images/arrayAdd.png)

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

## Supression d'une valeur d'un tableau
 - arrayRemove (26): Supression de la valeur 3
 - arrayRemove (27): Supression des valeurs 100,200 sous la forme d'un Json dont les virgules sont remplacées par des ;

![arrayRemove](../images/arrayRemove.png)

````html
BEGIN arrayRemove (26)
  Mise à jour du tag tagArrayNum => {"0":1,"2":7,"3":10,"4":100,"5":200,"6":30,"7":95,"8":1}
END 
BEGIN arrayRemove (27)
  Mise à jour du tag tagArrayNum => {"0":1,"2":7,"3":10,"6":30,"7":95,"8":1}
END 
````

## Message 

![message](../images/message.png)
````html
BEGIN message (2)
  Ajout du message suivant dans le centre de message : La consigne est de  21.5
END 
````

## Manipulaion d'un équipement
Voici un exemple de manipultion d'équipement lié à l'obect parent du scénario

![message](../images/eq.png)
````html
BEGIN Scénario [Aucun][E - Chambre][Test Node] : Scenario lance manuellement
  BEGIN start (1)
    BEGIN logTag (24)
      [#scenarioStartDate#] => 2022-03-25 07:25:13
      [#scenarioId#] => 103
      [#scenarioObject#] => [E - Chambre]
      [#scenarioObjectId#] => 13
      [#trigger#] => user
      [#triggerObject#] => [E - Chambre]
      [#triggerObjectId#] => 13
    END 
    BEGIN equipement_act (19)
      Evaluation de la condition :: #tag(scenarioObject,0)[Room config]#
      Evaluation de la condition :: #[E - Chambre][Room config]#
      Evaluation de la condition :: 814
      Equipement activé : [E - Chambre][Room config]
    END 
  END 
END Fin correcte du scénario
````

## Exécution en parallèle
Pour une exécution en parallèle, il ne suffit que de lier toutes les actions au même noeud plus tôt qu'une disposition bout en bout.

![execParallèle](../images/execParallèle.png)

## Déclancheur
Il est possible d'avoir multiple déclancheur et d'avoir un chemin différent pour chacun. Mais comme le scénario ne spécifi pas exactement qu'elle déclancheur à été solicité, le pluggin y va par déduction.

![trigger](../images/trigger.png)
````html
 -- Start : Scenario execute automatiquement sur evenement venant de :  genericType(LIGHT_STATE,#[E - Bureau]#) from [E - Bureau][Lumiere][Etat].
 - Exécution du sous-élément de type [action] : action
 Exécution d'un bloc élément : 554
 - Exécution du sous-élément de type [action] : code
 Exécution d'un bloc code 
   BEGIN Scénario [Aucun][E - Chambre][Test Node] |||#842#
     BEGIN Node (1): {"nodeId":1,"type":"start","subtype":"trigger","options":{},"subelements":{"GO":{"type":"","subtype":"action","expression":"","linkTo":["30"]}},"title":"D\u00e9part"}
       Compare  vs #[E - Bureau][Lumiere][Etat]#
       Compare  vs genericType(LIGHT_STATE,#[E - Bureau]#)
       Compare start == triggerSchedule && [E - Bureau][Lumiere][Etat] == programmation
     END 
     BEGIN Node (34): {"nodeId":34,"type":"triggerEvent","subtype":"trigger","options":{"enable":1},"expression":"#[E - Bureau][Lumiere][Etat]#","subelements":{"GO":{"linkTo":["33"]}},"title":"Ev\u00e9nement"}
       Compare #[E - Bureau][Lumiere][Etat]# vs #[E - Bureau][Lumiere][Etat]#
       Compare #[E - Bureau][Lumiere][Etat]# vs genericType(LIGHT_STATE,#[E - Bureau]#)
       Compare triggerEvent == triggerSchedule && [E - Bureau][Lumiere][Etat] == programmation
     END 
     BEGIN triggerEvent (34)
       BEGIN log (33)
         Scenario exécuté par commande
       END 
       BEGIN logNode (30)
         Node (1): {"nodeId":1,"type":"start","subtype":"trigger","options":{},"subelements":{"GO":{"type":"","subtype":"action","expression":"","linkTo":["30"]}},"title":"D\u00e9part"}
         Node (30): {"nodeId":30,"type":"logNode","subtype":"action","options":{"enable":1},"subelements":{"OK":{"linkTo":["32"]}},"title":"Afficher noeuds dans le log"}
         Node (31): {"nodeId":31,"type":"log","subtype":"action","options":{"enable":1,"value":"Fin du scenario"},"subelements":{"OK":{"linkTo":[]}},"title":"Ajouter un log"}
         Node (32): {"nodeId":32,"type":"logTag","subtype":"action","options":{"enable":1},"subelements":{"OK":{"linkTo":["31"]}},"title":"Afficher tags dans le log"}
         Node (33): {"nodeId":33,"type":"log","subtype":"action","options":{"enable":1,"value":"Scenario ex\u00e9cut\u00e9 par commande"},"subelements":{"OK":{"linkTo":["30"]}},"title":"Ajouter un log"}
         Node (34): {"nodeId":34,"type":"triggerEvent","subtype":"trigger","options":{"enable":1},"expression":"#[E - Bureau][Lumiere][Etat]#","subelements":{"GO":{"linkTo":["33"]}},"title":"Ev\u00e9nement"}
         Node (35): {"nodeId":35,"type":"triggerEvent","subtype":"trigger","options":{"enable":1},"expression":"genericType(LIGHT_STATE,#[E - Bureau]#)","subelements":{"GO":{"linkTo":["36"]}},"title":"Ev\u00e9nement"}
         Node (36): {"nodeId":36,"type":"log","subtype":"action","options":{"enable":1,"value":"Scenario ex\u00e9cut\u00e9 par type g\u00e9n\u00e9rique"},"subelements":{"OK":{"linkTo":["30"]}},"title":"Ajouter un log"}
         Node (38): {"nodeId":38,"type":"log","subtype":"action","options":{"enable":1,"value":"Scenario ex\u00e9cut\u00e9 par programmation"},"subelements":{"OK":{"linkTo":["30"]}},"title":"Ajouter un log"}
         Node (40): {"nodeId":40,"type":"triggerSchedule","subtype":"trigger","options":{"enable":1},"expression":"00 08 31 03 4 2022","subelements":{"GO":{"linkTo":["38"]}},"title":"Programmation"}
         Node (41): {"nodeId":41,"type":"triggerSchedule","subtype":"trigger","options":{"enable":1},"expression":"15 09 27 03 0 2024","subelements":{"GO":{"linkTo":["38"]}},"title":"Programmation"}
       END 
       BEGIN logTag (32)
         [#execByScenarioSys#] => 1
         [#scenarioStartDate#] => 2022-03-31 20:49:56
         [#scenarioId#] => 103
         [#scenarioObject#] => [E - Chambre]
         [#trigger#] => [E - Bureau][Lumiere][Etat]
         [#triggerValue#] => 0
         [#triggerGenericType#] => LIGHT_STATE
         [#triggerEq#] => [E - Bureau][Lumiere]
         [#triggerObject#] => [E - Bureau]
         [#triggerObjectId#] => 12
       END 
       BEGIN log (31)
         Fin du scenario
       END 
     END 
   END Fin correcte du scénario------------------------------------
````
# Exemple de scénario

## Gestion de période
![sc_periode](../images/sc_periode.png)

# Plugin tier
Il sera possible pour d'autre plugin d'appeler celui-ci avec une liste de nœud à exécuter. Il sera donc possible dans un plugin d'établir un flow d'action prédéterminé mais de permettre à l'utilisateur de modifier celui-ci.
