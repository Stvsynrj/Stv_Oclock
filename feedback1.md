# Apprenant 1 (Anthony)

Bonjour Anthony, tout d'abords, j'espère que tu as passé de bonnes fêtes de fin d'année.  
Je suis plus que content de voir ton avancée sur ce projet de cartes pendant cette période féstive ! ;)

Après avoir testé ton application, je voudrais voir avec toi quelque points, tu me diras ce que tu en penses et bien entendu, on pourra en parler de vive voix.

---

### Voila ce que j'ai pu retenir.

#### 1. Lorsque l'on recherche des cartes via un élément, dans le titre on se retrouve avec 'Nombre de carte(s) trouvée(s) : NaN' (Not A Number)

Voila la ligne incriminée à la ligne 22 du searchController.js :

`title: 'Résultat de la recherche : ' + searchedElement === 'null' ? ' sans élément' : + searchedElement)`

Que l'on pourrait remplacer par :

`` title: `Résultat de la recherche : ${searchedResults.length} carte(s) trouvée(s) pour ${searchedElement}`  ``

Attention, cela ne va pas nous sauver, mais niveau UX cela sera plus propre (c'est juste une rustine). Il reste le cas ou `searchedResults.length` est à 0 (et non null, on teste bien sa taille), le ternaire est ton copain, je te laisse gèrer la crise par toi même de plus, tu as déjà la solution, je le sais ;)

#### 2. La requéte ou tu as hésité pour l'ecrire au vu des commentaires laissés dans dataMapper.js à la ligne 66.

Je te propose cette solution (attention, je ne l'ai pas implémenté, c'est de tête, le champage et le foie gras faisant foi, je t'es laissé la proposion de correction).

```javascrtip
searchByValues: async(direction,value) => {
    const valueColumn = `value_${direction.replace(/'/g, "''")}`;

    let $query = "SELECT * FROM card WHERE 1=1"; // requête de base qu'on à passé de type const en let pour pouvoir ajouter des critères de filtre sachant qu'en const elle ne peut pas être modifiée (WHERE 1=1 oracle me poursui :) ) .

    /*
    * On va switcher sur la direction pour ajouter un critère de filtre
    * par defaut on selectionne toutes les cartes (default dans le switch)
    */

    switch (direction) {
        case 'north':
            $query += ` AND value_north >= ${valueColumn}`; // pour le nord, on ajoute un critère de filtre value_north
            break;
        case 'south':
            $query += ` AND value_south >= ${valueColumn}`; // pour le sud, on ajoute un critère de filtre value_south
            break;
        case 'east':
            $query += ` AND value_east >= ${valueColumn}`; // pour l'est, on ajoute un critère de filtre value_east
            break;
        case 'west':
            $query += ` AND value_west >= ${valueColumn}`; // pour l'ouest, on ajoute un critère de filtre value_west
            break;
        default:
            break; // si direction n'est pas une direction valide, on selectionne toutes les cartes
    }

    // Proposition de requete de la correction
    // SELECT * FROM card WHERE
    // // -- on teste la valeur de $1, $1 = 'xxx' va renvoyer true ou false
    // // --si $1 vaut 'north', on ajoute un critère de filtre value_north
	  // $1 = 'north' AND value_north >= $2
    // // --sinon, si $1 vaut 'south', on ajoute un critère de filtre value_south
    // OR	$1 = 'south' AND value_south >= $2
    // // --sinon, si $1 vaut 'east', on ajoute un critère de filtre value_east
    // OR	$1 = 'east' AND value_east >= $2
    // // --sinon, si $1 vaut 'west', on ajoute un critère de filtre value_west
    // OR	$1 = 'west' AND value_west >= $2;'

const result = await database.query(query, [value]);
    return result.rows;
  }
```

on aurait pu le faire avec un case directement dans la requéte voir avec du PL/SQL, pour l'instant c'est censé marcher, on optimisera après.

#### 3. Le moteur de recherche

Pour celui-ci ce qui est dommage, c'est que si on veut chercher une carte par un élément et un niveau, on est obligé de faire 2 recherches. on pourrait faire comme la requéte au dessus (concaténer les conditions), grouper les champs et avoir un seul boutton rechercher pour les 5 critères donc, en soit, un seul formulaire. On pourra regarder ensemble comme l'intégrer dans notre prochaine session.

#### 4. L'UX

- L'ajout et suppréssio-n de carte, pour l'utilisateur, il serait agréable d'avoir une alert (c'est pas top, une modal serait la classe internationnale) mais un petit "Voulez-vous ajouter cette carte à votre deck ?" et "Voulez-vous retirer cette carte de votre deck ?" serait un plus.
- Un autre point, la frontière entre le deck plein et/ou l'ajout d'une carte déjà existante dans le deck n'est pas claire, il faudrait bien informer l'utilisateur différemment pour ces 2 cas. ex: 'Votre deck contient déjà 5 cartes' et 'Cette carte est déjà dans votre deck'.

Voila, Anthony, je pense avoir fait le tour (plus ou moins), je pense que l'on aura pas mal de choses à voir ensemble la prochaine fois. Et encore bravo pour ton avancée pendant cette periode festive ! En te souhaitant encore mes meilleurs voeux pour cette année.

Steve.
