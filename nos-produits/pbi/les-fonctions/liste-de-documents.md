# Liste des pièces justificatives

Voici comment obtenir la liste des documents justificatifs à fournir pour l'évaluation du dossier par Cautioneo.

{% hint style="warning" %}
Chaque situation est différente les justificatifs nécessaires varient en fonction de la CSP et des revenus complémentaires de chaque locataire ou référent du dossier.

L'API vous permettra de déterminer quels justificatifs sont demandés pour chacun des participants au dossier.

Cet appel API est donc très important.
{% endhint %}

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

{% hint style="info" %}
Il peut arriver que des documents complémentaires soient nécessaires, dans ce cas, seuls les documents complémentaires demandés seront listés dans cet appel (au lieu des documents standards).

Soit il s'agit d'un document standard et donc `category` sera rempli et `title` nulle.

Soit il s'agit d'un document spécial et dans ce cas, `category` sera ``OTHER et `title` sera l'intitulé du document demandé.``

En fonction de ces cas, il faut donc afficher `title` (qui sera en Français) si il est présent, ou dans le cas contraire, afficher votre traduction correspondante à la valeur de `category`.
{% endhint %}

Cette fonction permet de récupérer la liste des documents justificatifs transmis par le bailleur du ou des locataires.

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
