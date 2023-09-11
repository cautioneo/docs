# Inviter un locataire

Cette fonction permet d'envoyer un email au locataire pour l'inviter à  créer un dossier.

Elle retourne une invitation ainsi que son statut dont vous pouvez retrouver la liste [ici](https://studio.apollographql.com/public/Cautioneo-API/variant/staging/schema/reference/enums/InvitationState?query=Invitation)

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
