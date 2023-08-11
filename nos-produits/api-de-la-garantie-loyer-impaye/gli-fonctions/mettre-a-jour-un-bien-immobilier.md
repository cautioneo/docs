---
description: Cette fonction permet la mise à jour des données du bien immobilier
---

# Mettre à jour  un bien immobilier

```graphql
mutation {
    updateProperty(
    input: {
      clientMutationId: "YOUR_CHOICE_NOT_MANDATORY"
      landlordId: "ID"
      realtorId: "ID"
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
     clientMutationId
   }
 }    
```
