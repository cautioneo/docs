# Lister mes dossiers

Voici comment obtenir la liste des dossiers d'une agence.

Il faut donc disposer de l'ID de cette agence.

Les paramètres `first` et `after` concernent la pagination (ex: first: 100, after: 'abc').
Le paramètre `after` correspond à la valeur retournée par l'API dans `pageInfo.endCursor`.
[Voir la documentation sur la pagination par curseur](https://graphql.org/learn/pagination/#pagination-and-edges)

```graphql
query getInvitationsOrSubscriptions($agencyId: ID!, $first: Int, $after: String) {
  node(id: $agencyId) {
    ...TenantsForRealtorFragment
  }
}

fragment PageInfoFragment on PageInfo {
    hasPreviousPage
    hasNextPage
    endCursor
    startCursor
}

fragment TenantPbiSubscriptionFragment on PbiSubscription {
    archived
    id
    state
    createdAt
    updatedAt
    leaseStartOn
    renters {
      nodes {
        id
        firstName
        lastName
      }
    }
    eligibility {
      eligible
      rentAmount
      maxRentWithoutDeposit
      maxRentWithDeposit
      maxCashDeposit
    }
    contract {
      reference
    }
    property {
      rentAmount
    }
}

fragment TenantInvitationFragment on Invitation {
    id
    acceptUrl
    archived
    category
    guestPhone
    guestName
    guestEmail
    hostName
    state
    createdAt
    updatedAt
}

fragment TenantsForRealtorFragment on Realtor {
    tenants(
      first: $first
      after: $after
    ) {
      edges {
        node {
          id
          ...TenantInvitationFragment
          ...TenantPbiSubscriptionFragment
        }
      }
      pageInfo {
        ...PageInfoFragment
      }
    }
}
```
