---
description: >-
  Cette page regroupe toutes les foncions inhérentes à l'Api Garantie Loyer
  Impayé.
---

# 🔧 GLI fonctions

{% hint style="info" %}
**Bon à savoir :** Vous pouvez consulter la documentation GraphQL de cette API, ainsi que la tester via l'outil [Apollo Studio](https://studio.apollographql.com/public/Cautioneo-API/explorer?variant=staging)

Cette API suit les conventions de schema [GraphQL Relay](https://relay.dev/)
{% endhint %}

## Mettre à jour les données utilisateurs.

Cette fonction permet de mettre à jour un compte utilisateur. Elle prend en paramètre un objet `input` contenant les informations nécessaires à la mise à jour du compte.

```graphql
mutation {
  updateUser(
    input: {
      id: "ID"
      email: "test@test.org"
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
      civilStatus: SINGLE
      gender: MALE
      nationality: "FR"
      employmentContractEndOn: "2022-07-16"
      oauth: {
        uid: ""
        provider: FACEBOOK
      }
    }
  ) {
    user {
      id
      email
    }
    errors
    clientMutationId
  }
}
```

## Créer un bien immobilier&#x20;

Cette fonction permet de créer une propriété&#x20;

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

## Mettre à jour  un bien immobilier&#x20;

Cette fonction permet la mise à jour des données du bien immobilier&#x20;

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

## Créer un abonnement&#x20;

Cette fonction permet de créer un abonnement à la Garantie loyers impayés

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

## Créer un locataire

Cette fonction permet de créer un ou plusieurs locataires. Lesquels seront couvert par la garantie.

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

## Valider l'abonnement&#x20;

Cette fonction permet de valider l'abonnement dans le but de transmettre nos justificatifs

```graphql
mutation {
    pbiSubscriptionSubmit(
      input: { 
          id: "ID" 
          ownerSendDocuments: true 
          }
    ) {
      errors
    subscription {
      id
      state
      situation
      createdAt
      updatedAt
      }
    }
  
```

## Reception des documents&#x20;

Cette fonction permet de transmettre les documents du ou des locataires.

```graphql
query getPbiSubscriptionDocuments($id: ID!) {
    node(id: $id) {
      ... on PbiSubscription {
        property {
          landlord {
            user {
              firstName
              lastName
            }
          }
        }
        state
        comment
        situation
        renters {
          nodes {
            id
          }
        }
        neededDocumentsLabelsByOwner {
          labels {
            category
            title
          }
          owner {
            id
            category
            firstName
            lastName
          }
          referents {
            labels {
              category
              title
            }
            owner {
              id
              category
              firstName
              lastName
            }
          }
        }
        documents {
          nodes {
            id
            fileName
            previewUrl
            label {
              category
              title
            }
            owner {
              id
              category
              firstName
              lastName
            }
          }
        }
      }
    }
  }
```

