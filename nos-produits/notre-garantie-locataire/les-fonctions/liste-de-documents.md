# Liste des pièces justificatives

Voici comment obtenir la liste des documents justificatifs à fournir pour l'évaluation du dossier par Cautioneo.

{% hint style="warning" %}
Chaque situation est différente les justificatifs nécessaires varient en fonction de la CSP et des revenus complémentaires de chaque locataire ou référent du dossier.

Un bref aperçu des documents demandés est disponible [ici](https://cautioneo.github.io/cautioneo-design/csp.html).

Mais c'est l'API qui vous permettra de déterminer quels justificatifs sont demandés pour chacun des participants au dossier.

Cet appel API est donc très important.
{% endhint %}

```graphql
query getSubscriptionDocuments($id: ID!) {
    node(id: $id) {
      ... on CautioneoSubscription {
        id
        state
        neededDocumentsLabelsByOwner {
          renter { # Le locataire
            title
            category
          }
          partner { # Son conjoint
            title
            category
          }
          referent { # Le référent du dossier pour les étudiants
            title
            category
          }
        }
      }
    }
  }
```

Cette fonction permet de récupérer la liste des documents justificatifs transmis par le·s locataire·s.

```graphql
query getSubscriptionDocuments($id: ID!) {
    node(id: $id) {
      ... on CautioneoSubscription {
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
