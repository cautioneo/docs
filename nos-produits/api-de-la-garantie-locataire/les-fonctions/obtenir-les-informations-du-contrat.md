# Obtenir les informations du contrat

Cette fonction permet de récupérer les informations du contrat d'une souscription.

```graphql
query {
  node(id: "ID") {
    ... on CautioneoSubscription {
      contract {
        id
        state
        fileUrl
      }
    }
  }
}
```
