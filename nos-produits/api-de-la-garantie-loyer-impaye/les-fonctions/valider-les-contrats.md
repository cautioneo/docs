# Valider les contrats

Passer l'état des contrat à : VALIDATED

```graphql
 mutation subscriptionValidateContract($subscriptionId: ID!) {
    subscriptionValidateContract(input: { id: $subscriptionId }) {
      subscription {
        ... on CautioneoSubscription {
          id
          state
        }
        ... on PbiSubscription {
          id
          state
        }
      }
      errors
    }
  }
```
