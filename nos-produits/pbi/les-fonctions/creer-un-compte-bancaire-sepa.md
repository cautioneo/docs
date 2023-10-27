# Créer un compte bancaire SEPA

Cette fonction permet de transmettre les informations de compte bancaire de prélèvement, seul un IBAN est nécessaire.

```graphql
mutation createStripeBankAccount(
    $userId: ID!
    $landlordId: ID
    $iban: String!
    $subscriptionId: ID
  ) {
  createBankAccount(
    input: {
      landlordId: $landlordId
      iban: $iban
      provider: STRIPE
      subscriptionId: $subscriptionId
    }
  ) {
    errors
    paymentMethod {
      id
      active
      mandateUrl
      mandateNumber
      name
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
