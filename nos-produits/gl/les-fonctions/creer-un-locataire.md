# Créer un Locataire

Cette fonction permet de créer un locataire pour un compte utilisateur.

Ainsi après la création d'un utilisateur vous pouvez transmettre son id, ici =>`userId` à travers cette mutation pour créer un locataire à partir de ce dernier.

```graphql
mutation {
  createRenter(
    input: {
      userId: "ID"
    }
  ) {
    renter {
      id
      user {
        id
        email
      }
    }
    errors
  }
}
```
