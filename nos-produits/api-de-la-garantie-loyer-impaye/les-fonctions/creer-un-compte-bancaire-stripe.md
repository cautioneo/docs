# Créer un compte bancaire STRIPE

Cette fonction permet de créer un compte en banque STRIPE

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
