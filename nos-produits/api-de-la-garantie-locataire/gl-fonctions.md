---
description: Cette page regroupe toutes les foncions inhérentes à l'Api Garantie locataire.
---

# 🔧 GL fonctions

{% hint style="info" %}
**Bon à Savoir:** Vous pouvez consulter la documentation GraphQL de cette API, ainsi que la tester via l'outil [Apollo Studio](https://studio.apollographql.com/public/Cautioneo-API/explorer?variant=staging)

Cette API suit les conventions de schema [GraphQL Relay](https://relay.dev/)
{% endhint %}

## Créer un utilisateur

Cette fonction permet de créer un compte utilisateur. Elle prend en paramètre un objet `input` contenant les informations nécessaires au compte.

```graphql
mutation {
  createUser(
    input: {
      clientMutationId: "YOUR_CHOICE_NOT_MANDATORY"
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

## Créer un locataire

Cette fonction permet de créer un locataire pour un compte utilisateur.

```graphql
mutation {
  createRenter(
    input: {
      clientMutationId: "YOUR_CHOICE_NOT_MANDATORY"
      userId: "ID"
    }
  ) {
    renter {
      id
      user {
        email
      }
    }
    errors
    clientMutationId
  }
}
```

## Création des données financières&#x20;

Cette fonction permet de renseigner les informations financières, de revenus et de capital d'un utilisateur.

Ces informations sont catégorisées selon la situation professionnelle de l'utilisateur, la liste est disponible [ici](https://cautioneo.github.io/cautioneo-design/csp.html).

```graphql
mutation {
  createFinancialState(
    input: {
      clientMutationId: "YOUR_CHOICE_NOT_MANDATORY"
      userId: "ID"
      activityBonus: 0
      alimony: 0
      annuities: 0
      savings: 0
      intermittentIncome: 0
      licensedProfessionalIncome: 0
      militaryIncome: 0
      netMonthlyIncome: 0
      netSalaryMonthlyIncome: 0
      propertyIncome: 0
      retirementPensionMonthlyIncome: 0
      maternityLeaveBenefit: 0
      socialCareBenefit: 0
      socialFamilyBenefit: 0
      unemploymentAllowance: 0
    }
  ) {
    financialState {
      id
      user {
        email
      }
    }
    errors
    clientMutationId
  }
}
```

## Création de la souscription

Cette fonction permet de créer une souscription / un dossier.

```graphql
mutation {
  createSubscription(
    input: {
      clientMutationId: "YOUR_CHOICE_NOT_MANDATORY"
      renterId: "ID"
      rentAmount: 250
      homeFound: false
      situation: ALONE
      leaseStartOn: "2023-07-14"
    }
  ) {
    subscription {
      id
      renter {
        user {
          id
          email
        }
      }
    }
    errors
    clientMutationId
  }
}
```

## Ajouter un justificatif à une souscription

Cette fonction permet d'ajouter un document justificatif de revenus, de capital ou de situation d'un utilisateur.

Ces informations sont catégorisées selon la situation professionnelle de l'utilisateur, la liste est disponible [ici](https://cautioneo.github.io/cautioneo-design/csp.html).

Une fonction de l'API vous permet également de les connaitre pour une souscription donnée [ici](https://cautioneo.github.io/cautioneo-design/fr-api-doc.html#getSubscriptionNeededDocumentsCategories).

```graphql
mutation {
  addDocumentBase64(
    input: {
      clientMutationId: "YOUR_CHOICE_NOT_MANDATORY"
      documentableId: "ID"
      ownerId: "ID"
      base64: "iVBORw0KGgoAAAANSUhEUgAAAsAAAAGMAQMAAADuk4YmAAAAA1BMVEX///+nxBvIAAAAAXRSTlMAQObYZgAAADlJREFUeF7twDEBAAAAwiD7p7bGDlgYAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAwAGJrAABgPqdWQAAAABJRU5ErkJggg=="
      category: INCOME_PROOF
    }
  ) {
    document {
      id
      category
      state
    }
    errors
    clientMutationId
  }
}
```

## Obtenir les informations d'un compte utilisateur

Cette fonction permet de récupérer les informations d'un compte utilisateur ainsi que les entités rattachées à celui-ci : `address`, `oauth`, `renter.currentSubscription`, ...

```graphql
query {
  node(id: "ID") {
    ... on User {
      id
      email
      civilStatus
      category
      renter {
        id
      }
      address {
        city
        country
        street
        postalcode
      }
      oauth {
        provider
        uid
      }
    }
  }
}
```

## Obtenir les informations d'une souscription

Cette fonction permet de récupérer les informations d'une souscription ainsi que les entités rattachées à celui-ci : `property`, `renter`, ...

```graphql
query {
  node(id: "ID") {
    ... on CautioneoSubscription {
      id
      state
      renter {
        user {
          email
          civilStatus
          category
        }
      }
      property {
        address {
          street
          postalcode
          city
          country
        }
      }
    }
  }
}
```

## Obtenir les justificatifs nécessaires d'une souscription

Chaque situation est différente et les documents justificatifs de celle-ci varient. C'est pourquoi cette requête vous permet de connaitre les justificatifs nécessaires à une souscription donnée.

```graphql
query {
  node(id: "ID") {
    ... on CautioneoSubscription {
      neededDocumentsLabels {
        category
        title
      }
      renter {
        user {
          category
        }
      }
    }
  }
}
```

## Obtenir les informations des documents d'une souscription

Cette fonction permet de récupérer les informations sur les justificatifs d'une souscription.

```graphql
query {
  node(id: "ID") {
    ... on CautioneoSubscription {
      documents {
        id
        state
        previewUrl
        fileName
        label {
          category
          title
        }
      }
    }
  }
}
```

## Création du propriétaire personne physique

Cette fonction permet de créer un propriétaire en personne physique afin de le rattacher à un bien à louer.

```graphql
mutation {
  createLandlord(
    input: {
      clientMutationId: "YOUR_CHOICE_NOT_MANDATORY"
      firstName: "John"
      lastName: "Doe"
      birthdate: "1990-01-01"
      birthplace: "Lille"
      gender: MALE
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

## Création du propriétaire personne morale

Cette fonction permet de créer un propriétaire en personne morale afin de le rattacher à un bien à louer.

```graphql
mutation {
  createProprietor(
    input: {
      clientMutationId: "YOUR_CHOICE_NOT_MANDATORY"
      company: {
        siren: "XXXXXXXX"
        email: "proprietor@test.org"
        legalName: "Proprietor"
        creationDate: "2020-01-01"
        address: {
          street: "165 avenue de Bretagne"
          postalcode: "59000"
          city: "Lille"
          country: "FR"
        }
        category: SARL
      }
    }
  ) {
    proprietor {
      id
    }
    errors
    clientMutationId
  }
}
```

## Création du bien à louer

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

## Obtenir les informations du contrat

Cette fonction permet de récupérer les informations du contrat d'une souscription.

<pre class="language-graphql"><code class="lang-graphql"><strong>query {
</strong>  node(id: "ID") {
    ... on CautioneoSubscription {
      contract {
        id
        state
        fileUrl
      }
    }
  }
}
</code></pre>
