# Créer un Bailleur

### Création du propriétaire personne physique

```graphql
mutation {
  createLandlord(
    input: {
      userId: "ID" # Required
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
  }
}
```

### Création du propriétaire personne morale (ex:  SCI)

```graphql
mutation {
  createProprietor(
    input: {
      company: {
        userId: "ID" # Required
        siren: "XXXXXXXX" # Required
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
  }
}
```
