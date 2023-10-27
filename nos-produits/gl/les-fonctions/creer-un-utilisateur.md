# Créer un Utilisateur

Cette fonction permet de créer un compte utilisateur. Elle prend en paramètre un objet `input` contenant les informations nécessaires au compte.

Les informations obligatoires à transmettre sont marquées ci-dessous par l'annotation **Required.**

```graphql
mutation {
  createUser(
    input: {
      email: "test@test.org" # Required
      password: "********" # Required
      firstName: "John" # Required
      lastName: "Doe" # Required
      acceptTerms: true
      acceptProspecting: true
      birthplace: "Lille"
      birthdate: "1990-04-01"
      phoneNumber: "+3332151606060"
      address: {
        street: "165 avenue de Bretagne"
        postalcode: "59800"
        city: "Lille"
        country: "FR"
      }
      category: CDI
      civilStatus: SINGLE
      gender: MALE
      nationality: "FR"
      employmentContractEndOn: "2022-07-16"
    }
  ) {
    user {
      id
      email
    }
    errors
  }
}
```

Retrouver la listes des :&#x20;

* [`civilStatus`](https://studio.apollographql.com/public/Cautioneo-API/variant/staging/schema/reference/enums/UserCivilStatus)
* [`category`](https://studio.apollographql.com/public/Cautioneo-API/variant/staging/schema/reference/enums/UserCategory)
* [`gender`](https://studio.apollographql.com/public/Cautioneo-API/variant/staging/schema/reference/enums/UserGender)
