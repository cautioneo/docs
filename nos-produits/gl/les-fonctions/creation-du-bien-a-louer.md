# Création du bien à louer

Cette fonction permet de créer un bien locatif rattaché à une souscription elle comprend par exemple le montant du loyer, le type de bien (Appartement, Maison ...) ainsi que des informations relatives à sa gestion ou à son ameublement.

```graphql
mutation {
  createProperty(
    input: {
      subscriptionId: "ID"
      landlordId: "ID"
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
