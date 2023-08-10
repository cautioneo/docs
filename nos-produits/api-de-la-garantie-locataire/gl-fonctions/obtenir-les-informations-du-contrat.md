---
description: >-
  Cette fonction permet de récupérer les informations du contrat d'une
  souscription.
---

# Obtenir les informations du contrat

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
