# Obtenir les informations des documents d'une souscription

Cette fonction permet d'avoir un retour concernant les documents transmis. Obtenir une url pour visionner ces derniers, voir leur statut de validation ainsi que pour quel catégorie d'utilisateur ont-il été transmis (Locataire, Référent ...).

Vous pouvez retrouver la liste des status [ici](https://studio.apollographql.com/public/Cautioneo-API/variant/staging/schema/reference/enums/DocumentState?query=Document)

```graphql
query {
  node(id: "ID") {
    ... on CautioneoSubscription {
      documents {
        id
        state
        previewUrl
        fileName
        label {
          category
          title
        }
      }
    }
  }
}
```
