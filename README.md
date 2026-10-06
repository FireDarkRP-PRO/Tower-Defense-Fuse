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

### Vagues
Les vagues d'ennemis se suivent, avec un boss toutes les 5 vagues. L'écran de victoire s'affiche une seule fois, à la fin de la vague 30 ; ensuite la partie continue sans limite. Dans le menu Options, tu peux choisir si la vague suivante démarre automatiquement ou seulement quand tu appuies sur **Vague suivante** (ou Espace).

### Niveaux et difficultés
Dix niveaux (Zigzag, Serpent, Spirale, Croisement, Demi-tour, Fourche, Îlot, Labyrinthe, Entrelacs, Grand détour), chacun avec sa route et ses propres emplacements de tours, espacés et placés à la main (de 26 à 51 selon le niveau). Trois difficultés :

| | Facile | Moyen | Difficile |
|---|---|---|---|
| Vies au départ | 30 | 20 | 12 |
| Pièces au départ | 180 | 120 | 90 |
| Résistance des ennemis | ×0,75 | ×1 | ×1,4 |
| Vitesse des ennemis | ×0,9 | ×1 | ×1,12 |
| Récompenses | ×1,2 | ×1 | ×0,9 |

### Sauvegarde
Ta partie en cours est **sauvegardée automatiquement** dans le navigateur (ennemis en cours compris) : rafraîchir la page ne la supprime pas. Elle est effacée quand le portail tombe. Depuis le menu Options, tu peux aussi exporter ta partie dans un fichier `.txt` et la réimporter plus tard, y compris sur un autre ordinateur.

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
| E / Échap | Ouvrir ou fermer le menu pause |
| R | Recommencer (après une défaite) |

## Technique

- Un seul fichier `index.html` : HTML, CSS et JavaScript (canvas 2D), sans bibliothèque externe.
- Index, réglages et partie en cours sont sauvegardés dans le navigateur (`localStorage`, clés `cst-dex`, `cst-set`, `cst-prog`, `cst-game`).
