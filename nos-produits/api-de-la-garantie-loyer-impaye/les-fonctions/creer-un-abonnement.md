# Créer un Dossier

Cette fonction permet a un propriétaire de souscrire à notre GLI (Garantie Loyer Impayé). Ce dernier créera alors son dossier en renseignant pour quel bien il souhaite souscrire.&#x20;

<pre class="language-graphql"><code class="lang-graphql">mutation {
    createPbiSubscription(
        input: {
            clientMutationId: "YOUR_CHOICE_NOT_MANDATORY"
            propertyId: "ID"
            situation: ALONE
            comment: "Je suis très content des services de Cautioneo"
            ownerSendDocuments: true
        }
<strong>    ) { 
</strong>    pbiSubscription {
        id 
    }
    errors
    clientMutationId
  }
}
</code></pre>
