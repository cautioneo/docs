# Créer un référent

Cette fonction sert à créer un référent (pour les étudiants sans revenus).

Un locataire peut avoir jusqu'à 2 référents pour un même dossier.

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
