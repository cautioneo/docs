# Valider l'abonnement

Cette fonction permet de valider l'abonnement dans le but de transmettre nos justificatifs

```graphql
mutation {
    pbiSubscriptionSubmit(
      input: { 
          id: "ID" 
          ownerSendDocuments: true 
          }
    ) {
      errors
    subscription {
      id
      state
      situation
      createdAt
      updatedAt
      }
    }  
```
