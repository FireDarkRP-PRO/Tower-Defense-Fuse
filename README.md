# Constellations – Tower Defense à fusion

Un tower defense navigateur, jouable directement en ouvrant `index.html` ou via GitHub Pages, sans installation ni dépendance : tout tient dans un seul fichier HTML.

## Le jeu

Des créatures venues du Vide avancent le long d'un chemin vers ton portail. Place des tours en forme d'étoiles sur la grille pour les arrêter avant qu'elles ne l'atteignent. Chaque ennemi qui passe te coûte des vies (davantage pour les boss) ; à 0 vie, la partie est terminée.

## Règles

### Météorites
Achète une météorite avec tes pièces pour obtenir une tour aléatoire sur un emplacement libre. Le prix augmente à chaque achat. La rareté d'une tour détermine ses chances d'apparition : Commun et Peu commun sortent souvent, Rare plus rarement, Épique et Légendaire sont exceptionnelles.

### Améliorer une tour
Clique sur une tour posée : sa fiche s'affiche à droite du jeu, avec ses dégâts, son rayon d'action, sa cadence et son pouvoir spécial. Le bouton **Améliorer** augmente son niveau contre des pièces, jusqu'à une limite qui dépend de sa fusion.

### Fusionner
Glisse une tour sur une autre tour identique (même type, même fusion) pour les fusionner. Les deux tours disparaissent au profit d'une seule, plus forte : fusion +1, niveau +1, et une limite de niveau plus haute. C'est la seule façon de dépasser le niveau maximum d'une tour, et aussi un moyen de libérer de la place sur la grille.

### Tour mythique : le Néant
Chaque météorite a **0,1 %** de chances de contenir le Néant, une tour **Mythique**. Elle ne tire pas : elle ajoute un bouton **Nuke** (touche **N**) qui retire une part des PV max de tous les ennemis à l'écran.

| Niveau | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 (max) |
|---|---|---|---|---|---|---|---|---|---|
| PV max retirés (ennemis) | 20 % | 30 % | 40 % | 50 % | 60 % | 70 % | 80 % | 90 % | 100 % |
| PV max retirés (boss) | 10 % | 15 % | 20 % | 25 % | 30 % | 35 % | 40 % | 45 % | 50 % |

Prix d'amélioration du Néant (pièces, cumulés depuis le niveau 1) : niveau 3 → 300, niveau 5 → 975, niveau 7 → 2 494, niveau 9 → 5 911. Une tour Légendaire coûte environ 2,7 fois moins cher.

Le Nuke est utilisable **une fois toutes les 3 vagues**. Les dégâts ignorent l'armure et se calculent sur les PV max. Les ennemis tués par un Nuke ne se divisent pas. Le Néant suit la règle de fusion normale : il faut fusionner deux Néants identiques pour monter sa limite de niveau (le niveau 9 demande la fusion 4, soit 8 Néants).

### Vagues
Les vagues d'ennemis se suivent, avec un boss toutes les 5 vagues. L'écran de victoire s'affiche une seule fois, à la fin de la vague 30 ; ensuite la partie continue sans limite. Dans le menu Options (accessible depuis la pause), tu peux choisir si la vague suivante démarre automatiquement après un délai, ou seulement quand tu appuies sur **Vague suivante** (ou la touche Espace).

### Niveaux
Dix niveaux, chacun avec sa propre route (et ses 26 emplacements), à choisir sur l'écran de départ :

| # | Niveau | Particularité |
|---|---|---|
| 1 | Zigzag | Le parcours classique en trois lignes droites |
| 2 | Serpent | Un long serpent à quatre lignes |
| 3 | Spirale | La route s'enroule jusqu'au portail, au centre |
| 4 | Croisement | La route se recoupe elle-même au centre |
| 5 | Demi-tour | La route repasse sur son premier tronçon à l'envers, puis part vers le bas |
| 6 | Fourche | Deux entrées qui fusionnent sur une seule route |
| 7 | Îlot | La route se sépare en deux autour d'un îlot, puis se rejoint |
| 8 | Labyrinthe | Cinq longs couloirs verticaux |
| 9 | Entrelacs | Une route qui se croise trois fois |
| 10 | Grand détour | Le parcours le plus long |

Quand une route a deux branches, les ennemis alternent entre elles. Le meilleur numéro de vague atteint est retenu pour chaque niveau et chaque difficulté.

### Difficultés
| | Facile | Moyen | Difficile |
|---|---|---|---|
| Vies au départ | 30 | 20 | 12 |
| Pièces au départ | 180 | 120 | 90 |
| Résistance des ennemis | ×0,75 | ×1 | ×1,4 |
| Vitesse des ennemis | ×0,9 | ×1 | ×1,12 |
| Récompenses | ×1,2 | ×1 | ×0,9 |

Pour changer de niveau ou de difficulté en cours de partie : menu pause (**E**) → **Options** → **Changer de niveau / de difficulté**. Cela lance une nouvelle partie.

### Sauvegarde
Depuis le menu Options, tu peux exporter ta partie (niveau et difficulté compris) dans un fichier `.txt` et la réimporter plus tard, y compris sur un autre ordinateur. Au chargement du site, un écran te propose d'importer une sauvegarde ou de commencer une nouvelle partie.

Pour éviter de farmer des pièces en rechargeant une ancienne sauvegarde, le jeu retient la vague la plus avancée déjà atteinte dans le navigateur : une sauvegarde ne peut jamais faire redescendre la partie en dessous de cette vague.

### Index
Le menu pause (touche **E**) donne accès à :
- **Règles** : ce résumé, directement dans le jeu.
- **Bestiaire** : les ennemis déjà vaincus, avec leur nombre de victoires et leurs statistiques.
- **Tours** : les tours déjà obtenues, avec leurs statistiques à chaque niveau débloqué.
- **Options** : le réglage des vagues automatiques, le changement de niveau / difficulté et la sauvegarde.

## Commandes

| Touche | Action |
|---|---|
| Clic gauche | Sélectionner une tour / glisser pour fusionner ou déplacer |
| B | Acheter une météorite |
| N | Nuke (tour mythique) |
| U | Améliorer la tour sélectionnée |
| S | Vendre la tour sélectionnée |
| Espace | Lancer la vague suivante |
| V | Changer la vitesse du jeu |
| E / Échap | Ouvrir ou fermer le menu pause |
| R | Recommencer (après une défaite) |

## Technique

- Un seul fichier `index.html` : HTML, CSS et JavaScript (canvas 2D), sans bibliothèque externe.
- Les index (bestiaire, tours) et les réglages sont sauvegardés automatiquement dans le navigateur (`localStorage`).
- Les sauvegardes de partie sont des fichiers texte au format JSON, à exporter et importer manuellement.
