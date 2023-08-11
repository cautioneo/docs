---
description: >-
  Cette fonction permet de créer un ou plusieurs locataires. Lesquels seront
  couvert par la garantie.
---

# Créer un locataire

```graphql
mutation {
    createGliRenter(
    input: {
        clientMutationId: "YOUR_CHOICE_NOT_MANDATORY"
        pbiSubscriptionId: "ID"
        firstName: "Pierre"
        lastName: "Henri"
        category: MILITARY
        seniority: MORE_THAN_12_MOUNTHS
        rentSeniority: MORE_THAN_6_MOUNTHS
        employmentContractEndOn: "1990-04-01"
        trialPeriodEndOn: "1990-04-01"
        }
 ) { 
     createGliRenter {
        id 
        }
        errors
        clientMutationId
    }
 }
```
