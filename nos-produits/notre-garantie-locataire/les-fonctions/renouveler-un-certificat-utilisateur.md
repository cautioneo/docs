# Renouveler un certificat utilisateur

Cette fonction sert à renouveler un certificat quand ce dernier à expiré il retourne alors un booléen confirmant ou infirmant le statut expiré de ce dernier la réponse attentu ici est donc que le booléen `expired` soit passé à `false`

```graphql
mutation renewCertificate($id: ID!) {
    renewCertificate(input: { id: $id }) {
      certificate {
        expired
      }
    }
  }
```
