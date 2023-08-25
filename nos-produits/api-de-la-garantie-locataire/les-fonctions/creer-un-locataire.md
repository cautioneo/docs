# Créer un locataire

Cette fonction permet de créer un locataire pour un compte utilisateur.

```graphql
mutation {
  createRenter(
    input: {
      clientMutationId: "YOUR_CHOICE_NOT_MANDATORY"
      userId: "ID"
    }
  ) {
    renter {
      id
      user {
        email
      }
    }
    errors
    clientMutationId
  }
}
```
