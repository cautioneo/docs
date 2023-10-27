# Création du propriétaire

### Création du propriétaire personne physique

Cette fonction permet de créer un propriétaire en personne physique afin de le rattacher à un bien à louer.

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

### Création du propriétaire personne morale

Cette fonction permet de créer un propriétaire en personne morale ( SCI, SARL ... ) afin de le rattacher à un bien à louer existant.

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
