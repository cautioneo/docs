# Ajouter un justificatif à un dossier

Cette fonction permet d'ajouter un document justificatif de revenus, de capital ou de situation d'un utilisateur.

Ces informations sont catégorisées selon la situation professionnelle de l'utilisateur, la liste est disponible [ici](https://cautioneo.github.io/cautioneo-design/csp.html).

Une fonction de l'API vous permet également de les connaitre pour une souscription donnée [ici](liste-de-documents.md).

```graphql
mutation {
  addDocumentBase64(
    input: {
      documentableId: "ID"
      ownerId: "ID"
      base64: "iVBORw0KGgoAAAANSUhEUgAAAsAAAAGMAQMAAADuk4YmAAAAA1BMVEX///+nxBvIAAAAAXRSTlMAQObYZgAAADlJREFUeF7twDEBAAAAwiD7p7bGDlgYAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAwAGJrAABgPqdWQAAAABJRU5ErkJggg=="
      label: {
        category: INCOME_PROOF
      }
    }
  ) {
    document {
      id
      category
      state
    }
    errors
  }
}
```

* `documentableId` est l'ID du dossier sur lequel transmettre le document.
* `ownerId` est l'ID du locataire (`GliProfile.id`)
* `base64` est le contenu du document encodé en `base64`
* `category` est le type de document, la liste des types de documents est disponible [ici](https://studio.apollographql.com/public/Cautioneo-API/variant/staging/schema/reference/enums/DocumentCategory)
