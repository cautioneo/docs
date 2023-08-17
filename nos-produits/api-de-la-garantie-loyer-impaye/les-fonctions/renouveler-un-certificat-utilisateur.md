# Renouveler un certificat utilisateur

### Cette fonction sert à renouveler un certificat&#x20;

```graphql
mutation renewCertificate($id: ID!) {
    renewCertificate(input: { id: $id }) {
      certificate {
        expired
      }
    }
  }
```
