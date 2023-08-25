# Obtenir un accord de garantie

Cette fonction permet la récupération d'un accord de garantie lorsqu'il a été octroyé à ce dernier.

```graphql
query getCertificate($id: ID!) {
  node(id: $id) {
    ... on Certificate {
      id
      fileName
      expired
    }
  }
}
```
