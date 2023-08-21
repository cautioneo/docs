# Créer un bien immobilier

Cette fonction permet de créer une propriété

```graphql
mutation {
  createProperty(
    input: {
      clientMutationId: "YOUR_CHOICE_NOT_MANDATORY"
      landlordId: "ID"
      realtorId: "ID"
      furnished: false
      address: "33 rue de l'api"
      rentAmount: 950
      rentWithoutCharges: 900
      rentalCharges: 50
      deposit: 1000
      surface: 35.5
      description: "Magnifique triplex avec vue sur la mer"
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
