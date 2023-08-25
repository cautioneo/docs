# Créer un dossier

Cette fonction permet de créer un dossier à la Garantie loyers impayés

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
