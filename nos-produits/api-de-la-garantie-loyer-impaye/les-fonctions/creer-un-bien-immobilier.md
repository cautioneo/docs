# Créer un bien immobilier

Cette fonction permet de créer un bien immobilier en location

```graphql
mutation {
  createProperty(
    input: {
      landlordId: "ID"
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
  }
}
```

### Mettre à jour un bien immobilier

Cette fonction permet la mise à jour des données du bien immobilier

```graphql
mutation {
    updateProperty(
        input: {
            landlordId: "ID"
            furnished: false
            address: "33 rue de l'api"
            rentAmount: 1000
            rentWithoutCharges: 900
            rentalCharges: 100
            deposit: 1000
            surface: 35.5
            description: "Magnifique triplex les pieds dans l'eau"
        }
    ) {
     property {
       id
     }
     errors
   }
}
```
