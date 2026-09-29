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

### Vagues
Les vagues d'ennemis se suivent, avec un boss toutes les 5 vagues. Dans le menu Options (accessible depuis la pause), tu peux choisir si la vague suivante démarre automatiquement après un délai, ou seulement quand tu appuies sur **Vague suivante** (ou la touche Espace).

### Sauvegarde
Depuis le menu Options, tu peux exporter ta partie dans un fichier `.txt` et la réimporter plus tard, y compris sur un autre ordinateur. Au chargement du site, un écran te propose d'importer une sauvegarde ou de commencer une nouvelle partie.

Pour éviter de farmer des pièces en rechargeant une ancienne sauvegarde, le jeu retient la vague la plus avancée déjà atteinte dans le navigateur : une sauvegarde ne peut jamais faire redescendre la partie en dessous de cette vague.

### Index
Le menu pause (touche **E**) donne accès à :
- **Règles** : ce résumé, directement dans le jeu.
- **Bestiaire** : les ennemis déjà vaincus, avec leur nombre de victoires et leurs statistiques.
- **Tours** : les tours déjà obtenues, avec leurs statistiques à chaque niveau débloqué.
- **Options** : le réglage des vagues automatiques et la sauvegarde.

## Commandes

| Touche | Action |
|---|---|
| Clic gauche | Sélectionner une tour / glisser pour fusionner ou déplacer |
| B | Acheter une météorite |
| U | Améliorer la tour sélectionnée |
| S | Vendre la tour sélectionnée |
| Espace | Lancer la vague suivante |
| V | Changer la vitesse du jeu |
| E / Échap | Ouvrir ou fermer le menu pause |
| R | Recommencer (après une défaite) |

## Déploiement sur GitHub Pages

1. Place `index.html` (et `README.md`) à la racine du dépôt, ou dans un sous-dossier dédié.
2. Dans les paramètres du dépôt GitHub, section **Pages**, choisis la branche et le dossier à publier.
3. Le jeu est alors accessible à l'URL fournie par GitHub Pages, sans build ni serveur.

Un fichier `meteorite.png` (image carrée, fond transparent) peut être ajouté à côté de `index.html` pour remplacer l'illustration de météorite dessinée par défaut.

## Technique

- Un seul fichier `index.html` : HTML, CSS et JavaScript (canvas 2D), sans bibliothèque externe.
- Les index (bestiaire, tours) et les réglages sont sauvegardés automatiquement dans le navigateur (`localStorage`).
- Les sauvegardes de partie sont des fichiers texte au format JSON, à exporter et importer manuellement.
