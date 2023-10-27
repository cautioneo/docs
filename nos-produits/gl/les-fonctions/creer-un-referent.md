# Créer un Référent

Les référents sont nécessaires pour les dossiers d'étudiants sans revenus.

Un seul référent est possible par dossier, même dans le cas d'un couple.

Il faut avant tout créer un compte utilisateur [comme ceci](creer-un-utilisateur.md).

Puis créer un référent rattaché à un dossier. Ici nous pouvons transmettre les informations de ce dernier et renseigner l'id du compte utilisateur auquel il doit être rattacher ainsi qu'a quel dossier. Le référent devra lui aussi transmettre des justificatifs.

```graphql
mutation createReferent($subscriptionId: ID!, $userId: ID!) {
   createReferent(
      input: {
        subscriptionId: $subscriptionId
        userId: $userId
      }
   ) {
    referent {
       id
       email
       firstName
       lastName
    }
}
```

le `userId` est donc l'ID du compte utilisateur "Référent" précédemment créé.
