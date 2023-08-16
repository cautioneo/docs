# Créer un référent

### Cette fonction sert à créer un référent Garantie loyer impayé&#x20;

```graphql
mutation {
 createGliReferent(
      input: {
        renterId: $renterId
        firstName: $firstName
        lastName: $lastName
        category: $category
        seniority: $seniority
      }
    ) {
      referent {
        id
      }
    }
    }
```
