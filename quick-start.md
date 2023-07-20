---
description: Vous trouverez ici toutes les informations relatives à notre api !
---

# Quick Start

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

{% tabs %}
{% tab title="curl" %}
```
curl -F grant_type=client_credentials \
     -F client_id=YOUR_CLIENT_ID \
     -F client_secret=YOUR_CLIENT_SECRET \
     -F redirect_uri=https://YOUR_HOST \
     -X POST https://{api.cautioneo.com | cautioneo-app-staging.caut.io}/oauth/tok
```
{% endtab %}
{% endtabs %}

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

## Faites votre première requête.

Pour faire votre première requête, envoyez une requête authentifiée a la méthode `createUser` de l'api. Cela créera un nouveau compte utilisateur. &#x20;

```graphql
mutation {
  createUser(
    input: {
      clientMutationId: "YOUR_CHOICE_NOT_MANDATORY"
      email: "test@test.org"
      firstName: "John"
      lastName: "Doe"
      acceptTerms: true
      acceptProspecting: true
      birthplace: "Lille"
      birthdate: "1990-04-01"
      phoneNumber: "+3332151606060"
      address: {
        street: "165 avenue de Bretagne"
        postalcode: "59800"
        city: "Lille"
        country: "FR"
      }
      category: CDI
      civilStatus: SINGLE
      gender: MALE
      nationality: "FR"
      employmentContractEndOn: "2022-07-16"
      oauth: {
        uid: ""
        provider: FACEBOOK
      }
    }
  ) {
    user {
      id
      email
    }
    errors
    clientMutationId
  }
}
```

{% hint style="info" %}
**Good to know:** You can use the API Method block to fully document an API method. You can also sync your API blocks with an OpenAPI file or URL to auto-populate them.
{% endhint %}

Take a look at how you might call this method using our official libraries, or via `curl`:

