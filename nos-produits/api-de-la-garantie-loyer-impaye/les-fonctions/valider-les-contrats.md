# Valider les contrats

Une fois le document de Bail transmis, vous pouvez passer l'état du contrat à : `VALIDATED`

[Liste des états d'un Contrat](https://studio.apollographql.com/public/Cautioneo-API/variant/staging/schema/reference/enums/ContractState)

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
