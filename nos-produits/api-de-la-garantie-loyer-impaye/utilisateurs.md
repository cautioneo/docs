# Utilisateurs

{% hint style="info" %}
**Good to know:** All the methods shown below are synced to an example Swagger file URL and are kept up to date automatically with changes to the API.
{% endhint %}

## Créer un utilisateur

Cette fonction permet de créer un compte utilisateur. Elle prend en paramètre un objet `input` contenant les informations nécessaires au compte.

```graphql
mutation {
  createUser(
    input: {
      clientMutationId: "YOUR_CHOICE_NOT_MANDATORY"
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

## Créer un locataire

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
