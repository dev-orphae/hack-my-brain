# La priorisation

La priorisation des différentes tâches va se faire en fonction de l'urgence et de l'importance associée avec les paramètres suivants :

- la **nature** de l'origine de la tâche,
- l' **objet** visé par la tâche,
- le **type** de l'objet auquel répond la tâche,
- le **sujet** bénéficiaire de l'objet de la tâche.

## Les paramètres

### nature

La nature d'une tâche peut être une **demande** explicite de la part du tiers ou bien une **initiative** de mon propre chef.

> *Les demandes qui sont formulées implicitement rentrent dans la définition des initiatives*.

On considère la priorité des demandes au bénéfice d'un tiers comme supérieure à la priorité des initiatives faites au bénéfice d'un tiers.

### objet

L'objet d'une tâche peut être en lien avec les notions de **survie**, d' **intégrité physique**, d' **intégrité mentale**, de **bien-être**, d' **accomplissement**, de **plaisir** ou de **confort**.

On considère l'importance de chaque objet respectivement décroissante suivant l'ordre de la liste précédente

### type

La tâche peut répondre à un **besoin**, un **problème** ou bien être une **envie** en lien avec son objet.

Les tâches répondant à un besoin ou un problème seront les seuls dont on conservera la notion d'urgence, en les classant dans cet ordre respectif.

### sujet

Le sujet est la personne qui va tirer en premier les bénéfices visés par l'objet d'une tâche. Cela peut être **moi** ou bien un **tiers** autre que moi.

> *Il se peut qu'une tâche soit autant dans le but d'apporter un bénéfice à moi et à quelqu'un⋅e d'autre. Dans ce cas on considère le sujet comme étant moi.*

> *Cependant, si une tâche vise en premier quelqu'un d'autre mais dont je tire aussi indirectement ou dans une moindre mesure des bénéfices, on considère alors dans ce cas que le sujet est un tiers.*

On va considérer comme plus importantes les tâches dont le sujet est moi :

## La logique

L'estimation de la priorité d'une tâche peut se résumer ainsi :

1. les taches urgentes sont prioritaires aux taches non urgentes, sans regard de leur importance.
2. les taches plus urgentes sont prioritaires aux taches moins urgentes.
3. les taches plus importantes sont prioritaires aux taches moins importantes.

### La modélisation circulaire

On considère la valeur de la priorité ***p*** comme la position d'un point sur la circonférence d'un cercle de rayon **1**.
Ainsi, la valeur de *p* se situe donc entre 0 et 2π et est dépendante des valeurs de son cosinus *cos(p)* et de son sinus *sin(p)*.

Soit *p* initialement défini comme `p = 0`

**On considère d'abord l'influence de l'objet de la tâche.**

Pour rappel, ici les objets sont : "confort", "plaisir", "accomplissement", "bien-être", "intégrité mentale", "intégrité physique", "survie".

En prenant *tot(obj)* la valeur sortante d'une fonction égale au nombre total d'objets étudiés **en ajoutant 1 à ce nombre**.
Et en prenant *pos(obj)* la valeur sortante d'une fonction égale à la position de l'objet étudié.

En faisant prendre au sinus de *p* la valeur `sin(p) = pos(obj) / tot(obj)` on peut déjà donner à *p* une valeur non nulle, son cosinus restant indéfini on ne sait cependant pas encore si *p* se situe entre 0 et π/2 ou bien s'il se situe entre π/2 et π.

Par exemple, si la tâche est ici en rapport avec l'intégrité mentale, sa position vaut 5 dans une liste d'un total de 7 auquel on ajoute 1. Alors `sin(p) = 5/8`.


**On considère maintenant le type de l'objet de la tâche.**

Pour rappel ici les types d'objets sont : "un besoin", "un problème", "autre chose".

Si l'objet est un besoin, alors `sin(p) = -1 * sin(p)`.

Sinon si l'objet est un problème, alors `cos(p) = -1 * |cos(p)|`.

Sinon l'objet est autre chose, dans ce cas `cos(p) = |cos(p)|`.

**On considère maintenant la nature de l'origine de la tâche**

Pour rappel, une tâche peut ici faire suite à "une demande" ou bien "une initiative" de ma part.

On atténue la valeur de *p* dans le cas où la tâche est une initiative de mon propre chef au bénéfice d'un tiers. En revanche on ne change pas la valeur de *p* lorsqu'il est question d'une initiative de mon propre chef pour mon bénéfice propre.

Si la nature est une initative, alors :

Pour `cos(p) ≤ 0`, si `sin(p) ≤ 0` alors `cos(p) = 2 * cos(p)`

Et pour `cos(p) > 0`, si `sin(p) ≥ 0` alors `cos(p) = 2 * cos(p)`

Sinon la nature est une demande, dans ce cas rien ne change.

**On considère maintenant le sujet recevant la majorité du bénéfice de la tâche**

Si je suis le sujet, alors :

Pour `sin(p) > 0` : `cos(p) = -1 * |cos(p)|`

Pour `sin(p) ≤ 0` : `cos(p) = |cos(p)|`

Sinon le sujet est un tiers, alors :

Pour `sin(p) ≥ 0` : `cos(p) = |cos(p)|`

Pour `sin(p) < 0` : `cos(p) = -1 * |cos(p)|`

**On obtient une valeur de la priorité associée à la tâche**

La priorité *p* a maintenant une valeur définie comme :

`0 < p < π/2` : Ce qui va bénéficier en premier aux autres et qui n'est pas de l'ordre d'un besoin vital. A.k.a "Ni urgent ni important", on le fait après tout le reste.

`π/2 < p < π` : Ce qui va bénéficier en premier à moi mais qui n'est pas de l'ordre d'un besoin vital. C'est "important mais pas urgent" (on verra comment la planifier plus tard).

`π < p < 3π/2` : Ce qui va bénéficier à quelqu'un d'autre en premier, mais dont il ou elle a un besoin vital. Ce n'est "pas important mais urgent" (comprendre ici important de manière très autocentrée).

`3π/2 < p < 2π` : Ce qui va bénéficier en premier à moi, et dont en plus j'ai un besoin vital. "Urgent et Important" voire "Très Urgent et très Important", les tâches avec une telle priorité doivent rester inachevées durant le moins de temps possible.
