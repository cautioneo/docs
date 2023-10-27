# Obtenir les informations de l'accord de garantie

Cette fonction vous permet de connaitre le statut de l'accord (expiré ou non) ainsi que de récupérer son URL grâce à laquelle le visionnage / téléchargement de ce dernier est possible.

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
