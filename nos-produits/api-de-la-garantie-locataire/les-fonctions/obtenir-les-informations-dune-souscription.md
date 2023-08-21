# Obtenir les informations d'une souscription

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
