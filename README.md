# d3-link-game

Petit jeu utilisant la librairie javascript d3.js, dans lequel il faut trouver des connexions entre éléments.

![screenshot_game.png](screenshot_game.png)

Il s'agit d'un hommage au jeu vidéo "Eye of the Beholder". Le but est d'associer les classes de personnages aux armes et armures qu'elles ont le droit d'utiliser.


## Pour jouer

Cliquez ici : [http://recher.pythonanywhere.com/link_game/link_game.html](http://recher.pythonanywhere.com/link_game/link_game.html)

Les classes et groupes de classes de personnages sont déjà liées ensemble, afin de représenter la manière dont ils sont structurés.

Les éléments peuvent être déplacés dans l'aire de jeu par des drag&drop.

Pour tenter une association, cliquez sur une classe ou un groupe, puis sur un objet, puis sur le bouton "Associer" à droite. Si l'association est correcte, un lien se crée, sinon, un (vilain) message s'affiche.

Attention, malgré le fait qu'il y ait des regroupements de classes, certains objets doivent être associés plusieurs fois. Par exemple, la masse d'armes s'associe avec le groupe "Combattant(e)s" et avec la classe "Prêtre(sse)".

Réussirez-vous à trouver toutes les associations ?


## Pour jouer en local

Téléchargez puis décompressez le contenu de ce repository.

Dans le répertoire "code", cliquez sur le fichier `link_game.html`. Le jeu s'ouvre dans votre navigateur web.


## Customisation du jeu

Le jeu est configurable assez facilement.

Les éléments, leurs descriptions et les associations à trouver entre eux sont modifiables.

Le fait d'avoir deux types d'éléments n'est pas modifiable. Le premier type correspond aux classes/groupes de personnage, le deuxième correspond aux armes et armures, mais rien n'empêche de considérer que cela pourrait correspondre à d'autres choses. Par exemple : des personnes et des hobbies pratiqués par ces personnes, des fruits et leurs couleurs, des recettes de cuisine et leurs ingrédients, etc.

Les associations définies dès le départ peuvent se faire entre n'importe quels éléments. Dans le jeu initial, il y a déjà des associations entre classes/groupes de personnage. On pourrait aussi en ajouter entre des armes, même si ça n'a pas vraiment de sens.

Les associations à trouver sont obligatoirement entre un élément du premier type et un élément du deuxième type. Par exemple, il faut trouver l'association entre la Masse d'armes et la classe "Prêtre(sse)". Il n'est pas possible que le joueur doivent trouver une association entre la classe "Combattant(e)s" et la classe "Guerrier(e)".

TODO : créer un fichier à part avec les infos à définir dans les fichiers pour reconfigurer.

