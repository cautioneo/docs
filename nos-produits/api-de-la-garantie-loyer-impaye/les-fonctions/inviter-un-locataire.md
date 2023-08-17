# Inviter un locataire

Cette fonction permet d'envoyer un email au locataire pour l'inviter à faire créer un dossier.

```graphql
mutation inviteRenter($email: Email, $phone: String, $name: String) {
    inviteUser(
      input: { email: $email, phone: $phone, name: $name, category: RENTER }
    ) {
      invitation {
        id
        acceptUrl
        state
      }
      errors
    }
  }
```
