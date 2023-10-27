# Créer un dossier Locataire

Cette fonction permet de créer une souscription / un dossier pour un locataire ici nous devrons passer L'id du dit locataire obligatoirement comme l'annotation `# Required` nous l'indique.

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
