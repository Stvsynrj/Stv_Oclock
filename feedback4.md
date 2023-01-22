# Apprenant 4 (Leila)

Bonjour Leila, tout d'abords, j'espère que tu as passé de bonnes fêtes de fin d'année.
Je suis plus que content de voir ton avancée sur ce projet de cartes pendant cette période féstive et surtout depuis le peu de temps que tu es sur la formation ! ;)

Ce qui est fondamental, c'est de créer tes routes, même sans front (disponible ou non) cela te permet de les tester avec un outil comme Postman sans te préocuper de l'intégration.

On a un très gros travail devant nous, mais bon c'est le début, cela ne doit pas te faire peur ;)

# Les routes

Toutes les routes sont à faire ne serait-ce que pour faire fonctionner le moteur de recherche.
Je t'en ai crée une pour te donner un exemple:

tout d'abords, modification du controller :

```
cardPage: async (req, res) =>{
    try {
      const card = await dataMapper.getCard(req.params.id);
      res.render('card',{
          card: card, // on renvoit l'objet card
          title: `Carte sélectionnée : ${card.name}` // on en profite pour mettre le nom de la carte dans le titre
      });
    } catch(error) {
      console.error(error);
      res.status(500).send(`An error occured with the database :\n${error.message}`);
    }
  }
```

Ensuite on récupérer tout ça dans notre vue :

```
<h1><%= title %></h1>

<div class="cardsContainer">

    <div class="card">
      <a href="/card/<%= card.id %>">
        <img src="/visuals/<%= card.visual_name %>" alt="<%= card.name %> illustration">
        <p class="cardName"><%= card.name %></p>
      </a>
      <a class="link--addCard" title="Ajouter au deck" href="#">[ + ]</a>
    </div>

</div>

<%- include('footer') %>
```

Tu remarqueras que j'ai enlevé la boucle for(), pas besoin d'itérer puisqu'on est censé avoir qu'une seule carte.

ensuite j'ai créer une route pour lier notre controller à la vue :

```
router.get('/card/:id', mainController.cardPage);
```

Voila, tu as les 3 étapes pour lier les données, le controller et la vue (du MVC quoi :))

Du coup, je te laisse ça pour t'en servir pour les autres routes (mais non déstresse c'est pas si fou que ça ;))
Et comme tu le sais, je suis toujours disponible sur notre serveur discord comme d'habitude, c'est toujours plus rapide qu'un mail ;)

En te souhaitant une bonne semaine et surtout si tu as besoin d'un coup de pouce n'hésite pas !

Steve.
