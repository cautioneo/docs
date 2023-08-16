# Créer un abonnement

### Cette fonction permet de créer un abonnement à la Garantie loyers impayés

```graphql
mutation {
    createPbiSubscription(
    input: {
        clientMutationId: "YOUR_CHOICE_NOT_MANDATORY"
        propertyId: "ID"
        situation: ALONE
        comment: "Je suis très content des services de Cautioneo"
        ownerSendDocuments: true
        }
 ) { 
     pbiSubscription {
        id 
        }
        errors
        clientMutationId
    }
 }
```
