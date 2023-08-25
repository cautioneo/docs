# Liste de documents

Liste des documents à fournir

```graphql
query getPbiSubscriptionDocuments($id: ID!) {
    node(id: $id) {
      ... on PbiSubscription {
        id
        state
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
      }
    }
  }
```

Cette fonction permet de récupérer la liste des documents transmis du ou des locataires.

```graphql
query getPbiSubscriptionDocuments($id: ID!) {
    node(id: $id) {
      ... on PbiSubscription {
        id
        state
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
