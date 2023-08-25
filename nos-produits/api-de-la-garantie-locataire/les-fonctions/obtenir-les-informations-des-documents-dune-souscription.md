# Obtenir les informations des documents d'une souscription

Cette fonction permet de récupérer les informations sur les justificatifs d'une souscription.

```graphql
query {
  node(id: "ID") {
    ... on CautioneoSubscription {
      documents {
        id
        state
        previewUrl
        fileName
        label {
          category
          title
        }
      }
    }
  }
}
```
