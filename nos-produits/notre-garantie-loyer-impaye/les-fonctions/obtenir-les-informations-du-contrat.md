# Obtenir les informations du contrat

Cette fonction permet de connaitre le statut d'un contrat ainsi que d'en récupérer l'url pour le visionner lorsque ce dernier a été édité.

Si l'attribut `signable` est `true`, alors vous pouvez récupérer le `signUrl` afin de rediriger le locataire ou le propriétaire vers la page de signature électronique du contrat.

Vous pouvez retrouver les status de ce dernier [ici](https://studio.apollographql.com/public/Cautioneo-API/variant/staging/schema/reference/enums/ContractState)

```graphql
query {
  node(id: "ID") {
    ... on PbiSubscription {
      contract {
        id
        state
        fileUrl
        signable
        signUrl
      }
    }
  }
}
```
