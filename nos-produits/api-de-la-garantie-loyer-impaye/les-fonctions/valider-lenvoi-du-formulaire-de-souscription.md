# Valider l'envoi du formulaire de souscription

Une fois les différents champs remplis et documents transmis cette mutation demande l'étude du dossier par l'équipe Cautioneo.&#x20;

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
