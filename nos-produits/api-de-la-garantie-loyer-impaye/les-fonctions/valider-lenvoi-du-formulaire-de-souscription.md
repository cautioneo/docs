# Valider l'envoi du formulaire de souscription

Cette fonction permet une fois les différents champs et documents remplis et transmis de valider l'envoi du formulaire de souscription&#x20;

```graphql
mutation pbiSubscriptionSubmit($id: ID!, $ownerSendDocuments: Boolean) {
    pbiSubscriptionSubmit(
      input: { id: $id, ownerSendDocuments: $ownerSendDocuments }
    ) {
      errors
      subscription {
        ...PbiSubscriptionFragment
      }
    }
  }

```
