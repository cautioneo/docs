# Lister les documents des ou du  locataires

Cette fonction permet de récupérer la liste des documents que les locataires doivent transmettre lorsque le propriétaire a souhaité que Cautioneo les collecte auprès d'eux.

```graphql
mutation pbiSubscriptionGetDocumentsFromRenters($id: ID!) {
    pbiSubscriptionGetDocumentsFromRenters(input: { id: $id }) {
      errors
      subscription {
        ...PbiSubscriptionFragment
      }
    }
  }
```
