---
description: >-
  Cette fonction permet de créer un propriétaire en personne physique afin de le
  rattacher à un bien à louer.
---

# Création du propriétaire personne physique

```graphql
mutation {
  createLandlord(
    input: {
      clientMutationId: "YOUR_CHOICE_NOT_MANDATORY"
      firstName: "John"
      lastName: "Doe"
      birthdate: "1990-01-01"
      birthplace: "Lille"
      gender: MALE
      address: {
        street: "165 avenue de Bretagne"
        postalcode: "59800"
        city: "Lille"
        country: "FR"
      }
    }
  ) {
    property {
      id
    }
    errors
    clientMutationId
  }
}
```
