# Obtenir les informations de l'accord de garantie

Cette fonction de connaitre le statut de l'accord ( expiré ou non ) ainsi que de récupérer l'url grâce à laquelle le visionnage de ce dernier est possible.

```graphql
query {
  node(id: "ID") {
    ... on CautioneoSubscription {
      certificate {
        id
        expired
        fileUrl
      }
    }
  }
}
```
