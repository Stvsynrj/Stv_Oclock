# Le MCD

Il y a une petite erreur sur le **MCD**

En effet, la relation user et product pour les likes est une relation de type many to many et non pas one to many.
Logiquement l'utilisateur peut liker un produit mais qu'une seule fois. Il pourrait spammer le like mais il ne peut pas liker plusieurs fois le même produit. Il faut donc changer le type de relation en one to many.

## Quelques outils

Il existe plusieurs outils pour faire un MCD. Je te conseille d'utiliser [draw.io](https://www.draw.io/). C'est un outil en ligne qui te permet de faire un MCD. Il est très simple d'utilisation et il est gratuit.
[MySql Workbench](https://www.mysql.com/products/workbench/) est aussi un bon outil pour faire un MCD.
Il y a aussi [Lucidchart](https://www.lucidchart.com/) qui est un outil payant mais qui est très bien aussi.

En te souhaitant une bonne soirée.

Steve.
