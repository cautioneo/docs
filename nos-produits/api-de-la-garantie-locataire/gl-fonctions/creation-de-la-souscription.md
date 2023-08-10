---
description: Cette fonction permet de créer une souscription / un dossier.
---

# Création de la souscription

```graphql
mutation {
  createSubscription(
    input: {
      clientMutationId: "YOUR_CHOICE_NOT_MANDATORY"
      renterId: "ID"
      rentAmount: 250
      homeFound: false
      situation: ALONE
      leaseStartOn: "2023-07-14"
    }
  ) {
    subscription {
      id
      renter {
        user {
          id
          email
        }
      }
    }
    errors
    clientMutationId
  }
}
```
