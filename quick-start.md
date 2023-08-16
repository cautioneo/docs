---
description: Vous trouverez ici toutes les informations relatives à notre api !
---

# 🧑🎓 Débuter avec Les Api Cautioneo

## GraphQL Docs

{% hint style="info" %}
**Bon à Savoir:** Vous pouvez consulter la documentation GraphQL de cette API, ainsi que la tester via l'outil [Apollo Studio](https://studio.apollographql.com/public/Cautioneo-API/explorer?variant=staging)

Cette API suit les conventions de schema [GraphQL Relay](https://relay.dev/)
{% endhint %}

## Environnement URL

Production: [https://api.cautioneo.com/graphql](https://api.cautioneo.com/graphql)

Staging: [ https://cautioneo-app-staging.caut.io/graphq](https://cautioneo-app-staging.caut.io/graphq)l

## Authorization <a href="#authorization" id="authorization"></a>

Cautioneo vous a transmit un `CLIENT_ID` et un `CLIENT_SECRET`

```
curl -F grant_type=client_credentials \
     -F client_id=YOUR_CLIENT_ID \
     -F client_secret=YOUR_CLIENT_SECRET \
     -F redirect_uri=https://YOUR_HOST \
     -X POST https://{api.cautioneo.com | cautioneo-app-staging.caut.io}/oauth/tok
```

Cette requête OAuth vous retourne donc un JSON contenant un `ACCESS_TOKEN`&#x20;

_Ce token a une validité de 2 heures_

```json
 {
  "access_token": "ACCESS_TOKEN",
  "token_type": "Bearer",
  "expires_in": 7200,
  "scope": "public",
  "created_at": 1580746974
}
```

Vous devez donc transmettre cet `ACCESS_TOKEN` dans toutes vos requêtes GraphQL :

_Dans le header de la requête HTTP_

```json
{ "Authorization": "Bearer ACCESS_TOKEN" }
```

## Envie d'en savoir plus ?&#x20;

Trouvez l'ensemble de la documentions relative à nos Divers Api dans les rubriques ci-dessous.

{% content-ref url="nos-produits/api-de-la-garantie-locataire/" %}
[api-de-la-garantie-locataire](nos-produits/api-de-la-garantie-locataire/)
{% endcontent-ref %}

{% content-ref url="nos-produits/api-de-la-garantie-loyer-impaye/" %}
[api-de-la-garantie-loyer-impaye](nos-produits/api-de-la-garantie-loyer-impaye/)
{% endcontent-ref %}
