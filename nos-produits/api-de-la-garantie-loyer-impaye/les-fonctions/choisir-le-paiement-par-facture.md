# Choisir le paiement par facture

À l'échéance de la cotisation, un mail est envoyé au propriétaire avec la facture et un lien de paiement, afin de lui donner le choix du mode de règlement :&#x20;

* Carte bancaire
* Virement
* Prélèvement SEPA

Cette fonction permet de choisir ce mode de facturation pour un propriétaire (pour l'ensemble de ses contrats rattachés et en cours).

```graphql
mutation createInvoiceBilling(
    $userId: ID!
    $landlordId: ID
    $subscriptionId: ID
  ) {
  createInvoiceBilling(
    input: { landlordId: $landlordId, subscriptionId: $subscriptionId }
  ) {
    errors
    paymentMethod {
      id
      active
      category
    }
  }
  acceptTerm(input: { id: $userId, name: STRIPE }) {
    user {
      id
    }
  }
}
```
