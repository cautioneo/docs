# Créer un dossier Locataire

Cette fonction permet de créer une souscription / un dossier.

```graphql
mutation {
  createSubscription(
    input: {
      renterId: "ID" # Required
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
  }
}
```
