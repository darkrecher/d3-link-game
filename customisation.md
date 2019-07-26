# Customisation du jeu

## Méthode

Toute la configuration du jeu se trouve dans le fichier `code/link_game.html`.

Ce fichier contient donc à la fois la config, et le "moteur" du jeu. Ce n'est pas génial de mélanger ces deux notions dans un même fichier, mais, hey, c'est pas non plus le jeu du siècle. De plus, en séparant dans de nombreux fichiers, on augmente le risque que le jeu ne fonctionne plus en local, à cause de subtilités en sécurité web, tel que le CORS.


## Définition des éléments de l'aire de jeu

Dans le fichier `code/link_game.html`, chercher le texte `dict_nodes = {` (ligne numéro 140).

Les lignes qui se trouvent entre ce texte et l'accolade fermante (ligne 174) définissent chacune un élément placé dans l'aire de jeu, reliable avec d'autres éléments.

Chacune de ces lignes a le format suivant :

`"id_elem": [ "Nom élément", TYPE_ELEM, "fichier_image" ],`

(Attention de n'oublier aucun des caractères de ponctuation : guillemet, deux-points, crochets, la virgule à la fin, ...

Il faut spécifier les informations suivantes :

 - **id\_elem** : identifiant interne de l'élément. Utilisez seulement des lettres minuscules, des nombres et l'underscore. Cet identifiant sera répété à d'autres endroits du fichier html.
 - **Nom élément** : Nom de l'élément qui sera affiché dans la partie droite, lorsqu'il est sélectionné. Tous les caractères sont autorisés, sauf les guillemets doubles.
 - **TYPE\_ELEM** : Type de l'élément. Indiquez soit PERSON, soit ITEM. Les éléments PERSON peuvent représenter autre chose que des personnes et les ITEM autre chose que des items, en revanche il ne peut y avoir que ces deux types d'éléments. Lorsqu'elles sont sélectionnées, les PERSON s'affichent dans la partie haut-droite de la page web, et les ITEM dans la partie bas-droite.
 - **fichier\_image** : nom du fichier image utilisé pour représenter l'élément dans l'aire de jeu. Le fichier correspondant doit être placé dans le sous-répertoire `code/img`. Il peut être de n'importe quel format supporté par les navigateurs : png, jpg, ...

Il est conseillé de préfixer les id\_elem de type PERSON par le texte `person_` et les id\_elem de type ITEM par le texte `obj_`, mais ce n'est pas obligatoire.

La répartition des éléments dans l'aire de jeu se fait automatiquement. Il n'est pas possible de spécifier où ils seront placés.


## Définition des liens entre les éléments

Toujours dans le même fichier, chercher le texte `answers = [` (ligne numéro 190).

Les lignes qui se trouvent entre ce texte et le crochet fermant correspondant (ligne 237) définissent chacune un lien entre deux éléments du jeu.

Chacune de ces lignes a le format suivant :

`[ "id_elem_1", "id_elem_2", lien_deja_actif ],`

Il faut spécifier les informations suivantes :

 - **id\_elem\_1** : identifiant interne du premier élément à lier. Il faut indiquer l'une des valeurs `id_elem` indiquée précédemment dans la variable `dict_nodes`.
 - **id\_elem\_2** :  identifiant interne du second élément à lier. Même consigne : Il faut indiquer un `id_elem`.
 - **lien\_deja\_actif** : Spécifie si le lien est affiché dès le début du jeu, ou pas. Indiquez true ou false.

L'ordre des deux premières informations n'a pas d'importance. Si on inverse id\_elem\_1 et id\_elem\_2, cela ne change rien dans le jeu.

Pour les liens déjà actifs (true), il est possible d'indiquer n'importe quels éléments (par exemple deux éléments PERSON, ou deux éléments ITEM). Le lien sera, dans tous les cas, affiché dès le début du jeu.

Le joueur ne peut créer des liens que entre une PERSON et un ITEM. Pour les liens non actif (false), il est conseillé de prendre une PERSON et un ITEM. Sinon, le joueur ne pourra pas trouver ce lien, et ne pourra donc pas finir le jeu.

Le nombre de liens à trouver s'affiche en bas à gauche de la page web. Il est calculé automatiquement en fonction des liens définis et se met à jour automatiquement lorsque le joueur trouve un lien. Les liens déjà actifs ne sont pas pris en compte dans le nombre de liens à trouver.

Il n'y a aucune vérification ni aucun message si la définition des liens est mal faite. Les cas d'erreur suivants ne sont pas détectés :
 - id\_elem\_1 ou id\_elem\_2 n'est pas un identifiant correcte d'élément du jeu,
 - deux éléments ont le même identifiant interne,
 - deux liens ont le même couple d'identifiant interne,
 - un lien non actif entre deux éléments de même type.

C'est à vous de faire attention à votre customisation !!


## Définition des informations détaillées de chaque élément

Cette définition est facultative.

Il est possible de définir des informations détaillées pour aucun, une partie, ou tous les éléments du jeu.

Les informations détaillées d'un élément apparaissent dans la partie droite de la page, lorsque l'élément est sélectioné. Elles s'affichent juste en dessous du nom et de l'image de l'élément.

### Définition des infos détaillées des PERSON

Chercher le texte `<img class="person-img detail-img" src="">` (ligne numéro 20).

Après cette ligne, chaque bloc `div` ayant la classe `person-details` correspond aux informations détaillées d'un élément.

Pour ajouter les infos détaillées d'un élément, insérer un bloc de texte de ce type :

    <div class="person-details id_elem_person">
        Les informations détaillées de l'élément
    </div>

Il faut spécifier les informations suivantes :

 - **id\_elem\_person** : identifiant interne de l'élément de type PERSON possédant ces informations détaillées.
 - **Les informations détaillées de l'élément** : informations détaillées de l'élément. On peut indiquer du texte simple ou du code HTML plus structuré. Attention de ne pas mettre trop de choses, au risque de modifier la mise en page globale.

### Définition des infos détaillées des ITEM

Même principe que pour les PERSON, sauf qu'au départ, il faut chercher le texte `<img class="itm-img detail-img" src="">` (ligne numéro 70). Et chaque bloc d'informations détaillées possède la classe `itm-details`.

Il faut insérer un bloc de texte de ce type :

    <div class="itm-details id_elem_item">
        Les informations détaillées de l'élément
    </div>

L'information `id_elem_item` correspond à l'identifiant interne de l'élément de type ITEM dont on veut ajouter des informations détaillées.

Pour que le code HTML soit plus clair, il est conseillé de supprimer toutes les informations détaillées du jeu initial, pour les éléments PERSON et ITEM. Il s'agit de tous les blocs div ayant la classe `person-details` et tous les blocs div ayant la classe `itm-details`.

