# Obtenir les informations de l'accord de garantie

Cette fonction permet la récupération d'un accord de garantie lorsqu'il a été octroyé à ce dernier.

```graphql
query {
  node(id: "ID") {
    ... on CautioneoSubscription {
      certificate {
        id
        state
        url
      }
    }
  }
}
```
