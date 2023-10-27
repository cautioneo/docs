# Créer un Conjoint

Pour créer un conjoint rattaché au locataire principal du dossier, vous pouvez soit :&#x20;

* Créer le conjoint avec quelques informations. Puis mettre à jours les informations détaillées de l'User créé par la fonction [`createPartner`](https://studio.apollographql.com/public/Cautioneo-API/variant/staging/schema/reference/inputs/CreatePartnerMutationInput) grâce à la fonction [`updateUser`](https://studio.apollographql.com/public/Cautioneo-API/variant/staging/schema/reference/inputs/UpdateUserMutationInput).
* Créer un compte utilisateur avec une adresse email et réutiliser cette adresse email dans la fonction [`createPartner`](https://studio.apollographql.com/public/Cautioneo-API/variant/staging/schema/reference/inputs/CreatePartnerMutationInput) afin d'associer ce compte utilisateur avec le locataire principal en tant que conjoint.

{% hint style="danger" %}
Définir le statut du couple est obligatoire dans le dossier (champ: [`situation`](https://studio.apollographql.com/public/Cautioneo-API/variant/staging/schema/reference/enums/SubscriptionSituation)).
{% endhint %}

{% hint style="info" %}
Si vous ne disposez pas des informations de contact du conjoint, vous pouvez ne pas renseigner l'`email` de celui-ci un email factice lui sera attribué et vous pourrez le renseigner avec la fonction `updateUser`.
{% endhint %}

```graphql
mutation {
  createPartner(
    input: {
      userId: "ID_DU_LOCATAIRE_PRINCIPAL"
      category: CDI # CSP du conjoint
      civilStatus: MARRIED
      gender: MALE
      email: "conjoint@gmail.com"
    }
  ) {
    partner {
      id
      email
    }
    errors
  }
}
```
