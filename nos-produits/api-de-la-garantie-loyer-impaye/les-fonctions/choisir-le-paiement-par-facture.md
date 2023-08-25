# Choisir le paiement par facture

Cette fonction permet d'envoyer un mail à l'utilisateur pour lui donner le choix de paiement soit par carte bancaire soit par virement ou prélèvement.

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
