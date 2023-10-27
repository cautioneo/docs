# Demander l'étude du dossier

Cette fonction permet de demander à Cautioneo de vérifier le dossier et ses justificatifs.

Une fois cette demande faite, l'équipe Cautioneo traitera le dossier sous 48H ouvrés et si le dossier est validé, fournira un Accord de Garantie.

Si le dossier est incomplet, un mail sera envoyé au propriétaire pour lui demander des pièces justificatives supplémentaires (voir: [Liste des pièces justificatives](liste-de-documents.md)) ou de modifier une pièce justificative qui n'est pas lisible.

```graphql
mutation {
  pbiSubscriptionSubmit(
    input: { 
      id: "ID"
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
