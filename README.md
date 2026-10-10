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
Glisse une tour sur une autre tour identique (même type, même fusion) pour les fusionner. Les deux tours disparaissent au profit d'une seule, plus forte : fusion +1 et une limite de niveau plus haute. Le niveau est **conservé** : il ne monte de +1 que si les deux tours sont déjà au niveau max (jamais en difficulté Difficile). Il n'y a **aucune limite de fusion** : tu peux fusionner à l'infini. C'est la seule façon de dépasser le niveau maximum d'une tour, et aussi un moyen de libérer de la place sur la grille.

### Transformation
Le panneau **Transformation** (sous la fiche de tour) contient 3 cases. Place-y 3 tours de **fusion 2** (glisse-les, ou sélectionne une tour puis clique une case) : elles deviennent inactives, sont consommées, et débloquent un bouton d'achat de **météorites de fusion 2** (touche **B**). Le bouton d'origine reste (touche **F**), mais son prix, ainsi que la revente des tours de ce niveau de fusion, est divisé par deux.

Avec 3 tours de **fusion 3**, tu débloques la fusion 3 : le bouton à moitié prix devient alors la fusion 2, et ainsi de suite à l'infini. Une météorite de fusion N coûte le prix de base × (1 + (N-1)/10), soit ×1,1 en fusion 2, ×1,2 en fusion 3, etc. ; le palier juste en dessous du plus haut est à moitié prix. Les tours achetées ainsi démarrent au niveau 1, avec la limite de niveau de leur fusion. Clique sur une tour placée dans une case pour la reprendre.

### Tour mythique : le Néant
Chaque météorite a **0,1 %** de chances de contenir le Néant, une tour **Mythique**. Elle ne tire pas : elle ajoute un bouton **Nuke** (touche **N**) qui retire une part des PV max de tous les ennemis à l'écran.

| Niveau | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 (max) |
|---|---|---|---|---|---|---|---|---|---|
| PV max retirés (ennemis) | 20 % | 30 % | 40 % | 50 % | 60 % | 70 % | 80 % | 90 % | 100 % |
| PV max retirés (boss) | 10 % | 15 % | 20 % | 25 % | 30 % | 35 % | 40 % | 45 % | 50 % |

Le Nuke est utilisable **une fois toutes les 3 vagues**. Les dégâts ignorent l'armure et se calculent sur les PV max. Les ennemis tués par un Nuke ne se divisent pas.

### Tour légendaire : l'Aiguilleur
Une tour **Légendaire** qui ne tire pas (0 dégât) et ne peut apparaître que sur les maps possédant au moins un **croisement** de chemins : Îlot, Delta, Carrefour, Double fourche et Échangeur. Un croisement est un point où plusieurs routes se séparent ; il est matérialisé par un cercle ambre avec de petites marques vers chaque branche.
- **Obtention** : via la météorite, comme les autres tours, mais elle se pose automatiquement sur un croisement libre (jamais sur un emplacement normal), et seulement s'il en reste un.
- **Flèche** : elle indique la branche vers laquelle la tour attire les ennemis. Clique sur la tour (ou touche **T**, ou bouton *Tourner la flèche*) pour la faire passer à la branche suivante.
- **Effet** : quand un ennemi franchit le croisement sur une autre branche, il a une chance d'être redirigé vers celle de la flèche : 15 % au niveau 1, +10 % par niveau, jusqu'à 95 %. Un ennemi n'est redirigé qu'une seule fois par croisement.
- **Déplacement** : glisse la tour vers un autre croisement libre (impossible de la poser ailleurs, et les autres tours ne peuvent pas aller sur un croisement). Elle se fusionne comme les autres tours.

### Vagues
Les vagues d'ennemis se suivent, avec un boss toutes les 5 vagues. L'écran de victoire s'affiche une seule fois, à la fin de la vague 30 ; ensuite la partie continue sans limite.

**Équilibrage après la vague 30.** Jusqu'à la vague 30, la résistance des ennemis augmente de 15 % par vague et leurs récompenses de 4 % de la valeur de base. Au-delà, pour que l'argent ne devienne pas un frein (la partie était auparavant très difficile à poursuivre après la vague 35), la courbe change :

| Après la vague 30 | Avant | Maintenant |
|---|---|---|
| Résistance des ennemis | +15 % par vague | +6 % par vague |
| Récompenses | +4 % de la base par vague | +7 % par vague |
| Taille de la vague | +2 ennemis par vague | +1 ennemi par vague |

Les réglages se trouvent dans l'objet `TUNE` du fichier `index.html` (`softW`, `hpGrow2`, `rwGrow2`, `cnt2`). Dans le menu Options, tu peux choisir si la vague suivante démarre automatiquement ou seulement quand tu appuies sur **Vague suivante** (ou Espace).

### Niveaux et difficultés
Quatorze niveaux (Zigzag, Serpent, Spirale, Croisement, Demi-tour, Fourche, Îlot, Labyrinthe, Entrelacs, Grand détour, puis les maps à croisements Delta, Carrefour, Double fourche et Échangeur), chacun avec sa route et ses propres emplacements de tours (de 26 à 51 selon le niveau ; ceux des quatre dernières maps sont générés automatiquement). Trois difficultés :

| | Facile | Moyen | Difficile |
|---|---|---|---|
| Vies au départ | 30 | 20 | 12 |
| Pièces au départ | 180 | 120 | 90 |
| Résistance des ennemis | ×0,75 | ×1 | ×1,4 |
| Vitesse des ennemis | ×0,9 | ×1 | ×1,12 |
| Récompenses | ×1,2 | ×1 | ×0,9 |

### Sauvegarde
Le fichier de sauvegarde (`.txt`, exporté depuis le menu Options) contient **exactement** ce que le navigateur enregistre automatiquement, et inversement :
- l'**index** (bestiaire et tours débloquées) ;
- les **réglages** (vagues automatiques, niveau et difficulté choisis) ;
- les **records** de vague par niveau et par difficulté ;
- la **partie en cours**, au complet : pièces, vies, vague, ennemis à l'écran et file de la vague, tours (même celles dont la météorite n'est pas encore ouverte), cases de Transformation, palier de fusion, compte à rebours du Nuke.

Ta partie en cours est sauvegardée automatiquement dans le navigateur : rafraîchir la page ne la supprime pas, et elle est reprise là où tu l'avais laissée. Elle est effacée quand le portail tombe.

Importer un fichier remplace tout ce contenu dans le navigateur par celui du fichier, y compris sur un autre ordinateur. Un fichier exporté après une défaite ne contient pas de partie : l'import remet l'index, les réglages et les records, puis lance une nouvelle partie. Les anciens fichiers de sauvegarde restent lisibles.

## Commandes

| Touche | Action |
|---|---|
| Clic gauche | Sélectionner une tour / glisser pour fusionner, déplacer ou placer dans la Transformation |
| B | Acheter une météorite du palier le plus haut |
| F | Acheter une météorite du palier à moitié prix (après transformation) |
| N | Nuke (tour mythique) |
| U | Améliorer la tour sélectionnée |
| S | Vendre la tour sélectionnée |
| Espace | Lancer la vague suivante |
| V | Changer la vitesse du jeu (×1, ×2, ×3, ×4) |
| T | Tourner la flèche de l'Aiguilleur sélectionné |
| E / Échap | Ouvrir ou fermer le menu pause |
| R | Recommencer (après une défaite) |

## Technique

- Un seul fichier `index.html` : HTML, CSS et JavaScript (canvas 2D), sans bibliothèque externe.
- Index, réglages, records et partie en cours sont sauvegardés dans le navigateur (`localStorage`, clés `cst-dex`, `cst-set`, `cst-prog`, `cst-game`) ; le fichier d'export en est la copie exacte.
