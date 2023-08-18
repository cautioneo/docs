# Lister les documents des ou du  locataires

Cette fonction permet de récupérer la liste des documents du ou des locataires associés à leur souscription

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
