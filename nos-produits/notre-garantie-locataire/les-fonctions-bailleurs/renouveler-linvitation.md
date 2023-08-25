# Renouveler l'invitation

Cette fonction permet de renvoyer un email d'invitation quand le précédent est devenu obsololète.

<pre class="language-graphql"><code class="lang-graphql"><strong>mutation renewInvitation($invitationId: ID!) {
</strong>    renewInvitation(input: { id: $invitationId }) {
      invitation {
        createdAt
        acceptUrl
      }
      errors
    }
  }
</code></pre>
