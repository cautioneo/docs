# Ajouter un justificatif à une souscription

Cette fonction permet d'ajouter un document justificatif de revenus, de capital ou de situation d'un utilisateur.

Ces informations sont catégorisées selon la situation professionnelle de l'utilisateur, la liste est disponible [ici](https://cautioneo.github.io/cautioneo-design/csp.html).

Une fonction de l'API vous permet également de les connaitre pour une souscription donnée [ici](https://cautioneo.github.io/cautioneo-design/fr-api-doc.html#getSubscriptionNeededDocumentsCategories).

```graphql
mutation {
  addDocumentBase64(
    input: {
      documentableId: "ID"
      ownerId: "ID"
      base64: "iVBORw0KGgoAAAANSUhEUgAAAsAAAAGMAQMAAADuk4YmAAAAA1BMVEX///+nxBvIAAAAAXRSTlMAQObYZgAAADlJREFUeF7twDEBAAAAwiD7p7bGDlgYAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAwAGJrAABgPqdWQAAAABJRU5ErkJggg=="
      category: INCOME_PROOF
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
