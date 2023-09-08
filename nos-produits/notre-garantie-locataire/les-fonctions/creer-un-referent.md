# Créer un Référent

Crée un conjoint rattaché a un locataire. Définir le statut du couple est obligatoire dans le dossier (champ: `situation`).

```graphql
mutation {
 createReferent(
      input: {
        subscriptionId: $subscriptionId
        userId: $userId
      }
    ) {
      referent {
        id
  }
```
