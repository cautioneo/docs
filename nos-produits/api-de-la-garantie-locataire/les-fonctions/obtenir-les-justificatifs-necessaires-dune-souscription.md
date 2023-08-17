---
description: >-
  Chaque situation est différente et les documents justificatifs de celle-ci
  varient. C'est pourquoi cette requête vous permet de connaitre les
  justificatifs nécessaires à une souscription donnée.
---

# Obtenir les justificatifs nécessaires d'une souscription

```graphql
query {
  node(id: "ID") {
    ... on CautioneoSubscription {
      neededDocumentsLabels {
        category
        title
      }
      renter {
        user {
          category
        }
      }
    }
  }
}
```