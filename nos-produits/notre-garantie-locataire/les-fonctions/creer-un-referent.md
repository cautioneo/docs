# Créer un Référent

Crée un référent rattaché à un locataire et à un dossier. Ici nous pouvons transmettre les informations de ce dernier et renseigner l'id du locataire auquel il doit être rattacher ainsi qu'a quel dossier. Le référent devra lui aussi transmettre des justificatifs.

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
            email
            firstName
            lastName
  }
```
