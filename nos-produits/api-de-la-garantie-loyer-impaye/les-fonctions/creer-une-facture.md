# Créer une facture

Cette fonction permet de générer une facture&#x20;

```graphql
mutation createInvoiceBilling(
    $userId: ID!
    $landlordId: ID
    $subscriptionId: ID
  ) {
    createInvoiceBilling(
      input: { landlordId: $landlordId, subscriptionId: $subscriptionId }
    ) {
      errors
      paymentMethod {
        id
        active
        category
      }
    }
    acceptTerm(input: { id: $userId, name: STRIPE }) {
      user {
        id
      }
    }
  }
```
