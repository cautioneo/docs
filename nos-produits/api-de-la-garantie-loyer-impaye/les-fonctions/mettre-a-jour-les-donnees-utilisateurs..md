# Mettre à jour les données utilisateurs.

### Cette fonction permet de mettre à jour un compte utilisateur. Elle prend en paramètre un objet `input` contenant les informations nécessaires à la mise à jour du compte.

```graphql
mutation {
  updateUser(
    input: {
      id: "ID"
      email: "test@test.org"
      firstName: "John"
      lastName: "Doe"
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
      oauth: {
        uid: ""
        provider: FACEBOOK
      }
    }
  ) {
    user {
      id
      email
    }
    errors
    clientMutationId
  }
}
```
