# Créer un Bien immobilier

Cette fonction permet de transmettre les informations du bien immobilier en location à assurer.

Nous transmettrons donc le montant avec et hors charge, ainsi que des informations complémentaires telles que le type de bien (meublé ou non),  la superficie ou une description plus détaillée de ce dernier.

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
