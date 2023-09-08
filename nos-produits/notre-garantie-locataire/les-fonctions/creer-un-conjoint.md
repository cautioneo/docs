# Créer un conjoint

Crée un conjoint rattaché a un locataire. Définir le statut du couple est obligatoire dans le dossier (champ: `situation`).

```graphql
mutation {
  createUser(
    input: {
      email: "test@test.org"
      password:"********"
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
      civilStatus: MARRIED
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
