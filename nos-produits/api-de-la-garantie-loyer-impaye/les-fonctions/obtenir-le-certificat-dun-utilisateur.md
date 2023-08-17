# Obtenir le certificat d'un utilisateur

Cette fonction permet la récupération du certificat utilisateur lorsqu'il a été octroyé à ce dernier.

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
