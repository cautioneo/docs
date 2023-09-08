# Demander l'évaluation du dossier

Cette fonction permet de demander à Cautioneo de vérifier le dossier et ses justificatifs.

Une fois cette demande faite, l'équipe Cautioneo traitera le dossier sous 48H ouvrés et si le dossier est validé, fournira un Accord de Garantie.

```graphql
mutation {
  pbiSubscriptionSubmit(
    input: { 
      id: "ID" 
      ownerSendDocuments: true 
    }
  ) {
    errors
    subscription {
      id
      state
      situation
      createdAt
      updatedAt
    }
  }
}
```
