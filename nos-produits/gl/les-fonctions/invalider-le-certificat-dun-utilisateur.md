# Invalider le certificat d'un utilisateur

Cette fonction sert à invalider un certificat avant sa date de péremption la réponse attendu est alors un booléen nous confirmant que le statut `expired` est bien passé à `true`

<pre class="language-graphql"><code class="lang-graphql"><strong>mutation discardCertificate($id: ID!) {
</strong>  discardCertificate(input: { id: $id }) {
    certificate {
      expired
    }
  }
}
</code></pre>
