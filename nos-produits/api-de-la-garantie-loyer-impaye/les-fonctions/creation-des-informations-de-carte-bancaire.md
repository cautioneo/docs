# Création des informations de carte bancaire

### Cette fonction permet de générer les informations de carte bancaire d'un utilisateur et de les envoyer à STRIPE

```graphql
mutation {
   createCreditCardIntent(
      input: {
        landlordId: $landlordId
        firstName: $firstName
        lastName: $lastName
        provider: STRIPE
        subscriptionId: $subscriptionId
      }
    ) {
      paymentMethod {
        id
      }
      clientSecret
    }

```
