---
description: >-
  Cette fonction permet de récupérer la liste des documents transmis du ou des
  locataires.
---

# Liste de documents



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
