# Demander l'étude du dossier

Pour signaler à Cautioneo que le dossier / souscription est prête à être traitée, vous devez lancer la mutation `evaluateSubscriptionDocuments`.

Une fois cette demande faite, l'équipe Cautioneo traitera le dossier sous 48H ouvrés et si le dossier est validé, fournira un Accord de Garantie.

Si le dossier est incomplet, un mail sera envoyé au locataire pour lui demander des pièces justificatives supplémentaires (voir: [Liste des pièces justificatives](../../api-de-la-garantie-loyer-impaye/les-fonctions/liste-de-documents.md)) ou de modifier une pièce justificative qui n'est pas lisible.

```graphql
mutation {
  evaluateSubscriptionDocuments(
    input: { 
      id: "ID" 
    }
  ) {
    errors
    subscription {
      id
      state
      createdAt
      updatedAt
    }
  }
}
```
