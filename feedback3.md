# Apprenant 3 (Sarah)

Bonjour Sarah, tout d'abords, j'espère que tu as passé de bonnes fêtes de fin d'année.  
Je suis plus que content de voir ton avancée sur ce projet de cartes pendant cette période féstive ! ;)

Si mes souvenirs sont bons, on était resté sur le fait de voir la page détails d'une carte, chose, que tu as essayé de faire mais il nous reste cette erreur qui nous dit que 'card' n'est pas déclaré.
Effectivement, tu passes oneCard en paramtres à ta vue et dans la vue tu essayes d'itéter sur la variable 'card'.
Donc ça ne marche pas.

**Attention** même si tu passes le bon paramètres dans ton for() il ne sera pas pour autant itérable, tu vas devoir **utiliser** quelques feintes (comme on dit chez nous => sud-est :))

- Object.keys(onCard)
- ou un oneCard.map()
- ou d'autres solutions.

bien entendu, il va falloir changer toutes les références que tu fais dans ta boucle for() à card pour singleCard.

## Le design

Pour faire bien, il faudrait faire le design d'une seul carte (sur codepen.io par exemple) et ensuite le répercuter sur les autres, tu me connais à force, faire des modifications sur des modifications c'est (excuse moi l'expréssion, faire du caca sur du caca). Mais bon, je fais confiance en ta touche féminine moins bordélique que la notre pour ça ;).

## Les routes

Aucunes routes ne fonctionnent sur le moteur de recherche, il va falloir les rendre fonctionnelles. On pourra faire ça tranquillement ensemble avec Postman sans se soucier du front. Je pense sincèrement qu'il faut priorisé cet objectif, dis moi ce que tu en penses.

Certe il reste pas mal de boulot, mais vu ta motivation, il n'y a pas de raisons pour que tu n'y arrive pas !
Aller, on tien le bon bout, à la semaine prochaine !

Steve.
