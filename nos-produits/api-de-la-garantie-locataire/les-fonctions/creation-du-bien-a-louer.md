# Création du bien à louer

Cette fonction permet de créer un bien locatif rattaché à une souscription.

```graphql
mutation {
  createProperty(
    input: {
      clientMutationId: "YOUR_CHOICE_NOT_MANDATORY"
      subscriptionId: "ID"
      landlordId: "ID"
      floor: 1
      nbRooms: 2
      rentAmount: 555
      rentalCharges: 0
      rentWithoutCharges: 555
      furnished: false
      inManagement: false
      category: APARTMENT
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
