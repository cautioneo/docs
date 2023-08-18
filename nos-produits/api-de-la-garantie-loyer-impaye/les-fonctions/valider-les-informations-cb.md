# Valider les informations CB

Cette fonction permet de valider les informations d'une CB rattaché à une souscription.

```graphql
 mutation pbiSubscriptionValidateCb($id: ID!) {
    pbiSubscriptionValidateCb(input: { id: $id }) {
      errors
      subscription {
        ...PbiSubscriptionFragment
      }
    }
  }
```
