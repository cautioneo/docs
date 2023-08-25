# Créer un dossier

Cette fonction permet de créer un dossier à la Garantie loyers impayés

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
