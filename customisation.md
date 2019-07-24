# Customisation du jeu

## Méthode

Toute la configuration du jeu se trouve dans le fichier `code/link_game.html`.

Ce fichier contient donc à la fois la config, et le "moteur" du jeu. C'est pas génial de mélanger ces deux notions dans un même fichier, mais, hey, c'est pas non plus le jeu du siècle. De plus, en séparant dans de nombreux fichiers, on augmente le risque que le jeu ne fonctionne plus en local, à cause d'histoire de CORS ou autres subtilités de sécurité web.


## Définition des éléments de l'aire de jeu

dans le fichier `code/link_game.html`, chercher la ligne `dict_nodes = {`. Ligne numéro 140.

Les lignes qui se trouvent entre cette ligne et l'accolade fermante (ligne 174) définissent chacune un élément qui se déplace dans l'aire de jeu, reliable avec d'autres éléments.

Chacune de ces lignes a le format suivant :

"**id_elem**": [ "**Nom élément**", **TYPE_ELEM**, "**fichier_image**" ],

(Attention de n'oublier aucun des caractères de ponctuation : guillemet, deux-points, crochets, la virgule à la fin, ...

Il faut spécifier les éléments suivants :

 - **id_elem** : identifiant interne de l'élément. Utilisez seulement des lettres minuscules, des nombres et l'underscore. Cet identifiant sera répété à d'autres endroits de la customisation.
 - **Nom élément** : Nom de l'élément qui sera affiché dans la partie droite, lorsqu'il est sélectionné. Tous les caractères sont autorisés, sauf les guillemets doubles.
 - **TYPE_ELEM** : Type de l'élément. Indiquez soit PERSON, soit ITEM. Les éléments PERSON peuvent représenter autre chose que des personnes et les éléments ITEM autre chose que des items, mais il ne peut y avoir que ces deux types d'éléments. Lorsqu'elles sont sélectionnées, les PERSON s'affichent dans la partie haut-droite de la page web, et les ITEM dans la partie bas-droite.
 - **fichier_image** :
