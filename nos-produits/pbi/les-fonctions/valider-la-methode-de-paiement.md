# Valider la méthode de paiement

Cette fonction permet de valider le choix de la méthode de paiement par l'utilisateur.

<pre class="language-graphql"><code class="lang-graphql"><strong>mutation pbiSubscriptionValidatePaymentMethod($id: ID!) {
</strong>    pbiSubscriptionValidatePaymentMethod(input: { id: $id }) {
      errors
      subscription {
        ...PbiSubscriptionFragment
      }
    }
  }

</code></pre>
