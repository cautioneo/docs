# Abandonner la souscription

Cette fonction sert à abandonner une souscription en cours

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
