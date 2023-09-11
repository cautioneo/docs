# Obtenir les informations du contrat

Cette fonction permet de connaitre le statut d'un contrat ainsi que d'en récupérer l'url pour le visionner lorsque ce dernier a été édité.

Vous pouvez retrouver les status de ce dernier [ici](https://studio.apollographql.com/public/Cautioneo-API/variant/staging/schema/reference/enums/ContractState)

```graphql
query {
  node(id: "ID") {
    ... on CautioneoSubscription {
      contract {
        id
        state
        fileUrl
      }
    }
  }
}
```
