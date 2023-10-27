# Abandonner le dossier

Afin d'abandonner une souscription en cours, vous pouvez utiliser cette fonction :&#x20;

```graphql
mutation pbiSubscriptionAbandon($id: ID!, $reason: String) {
    pbiSubscriptionAbandon(input: { id: $id, reason: $reason }) {
      errors
      subscription {
        ...PbiSubscriptionFragment
      }
    }
  }

```
