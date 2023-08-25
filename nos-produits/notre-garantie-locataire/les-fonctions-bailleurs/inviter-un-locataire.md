# Inviter un locataire

Cette fonction permet d'envoyer un email au locataire pour l'inviter à faire créer un dossier.

<pre class="language-graphql"><code class="lang-graphql">mutation inviteRenter($email: Email, $phone: String, $name: String) {
<strong>  inviteUser(
</strong>    input: { email: $email, phone: $phone, name: $name, category: RENTER }
  ) {
    invitation {
      id
      acceptUrl
      state
    }
    errors
  }
}
</code></pre>
