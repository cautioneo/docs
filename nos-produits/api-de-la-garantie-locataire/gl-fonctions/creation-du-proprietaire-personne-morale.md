---
description: >-
  Cette fonction permet de créer un propriétaire en personne morale afin de le
  rattacher à un bien à louer.
---

# Création du propriétaire personne morale

```graphql
mutation {
  createProprietor(
    input: {
      clientMutationId: "YOUR_CHOICE_NOT_MANDATORY"
      company: {
        siren: "XXXXXXXX"
        email: "proprietor@test.org"
        legalName: "Proprietor"
        creationDate: "2020-01-01"
        address: {
          street: "165 avenue de Bretagne"
          postalcode: "59000"
          city: "Lille"
          country: "FR"
        }
        category: SARL
      }
    }
  ) {
    proprietor {
      id
    }
    errors
    clientMutationId
  }
}
```
