# Obtenir un Accord de Garantie

Cette fonction permet d'obtenir les informations d'un accord de garantie une fois le dossier validé par Cautioneo.

```graphql
query getCertificate($id: ID!) {
  node(id: $id) {
    ... on PbiSubscription {
      id
      certificate {
        id
        fileName
        expired
        url
      }
    }
  }
}
```
