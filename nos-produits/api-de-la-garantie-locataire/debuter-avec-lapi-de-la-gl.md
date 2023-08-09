---
description: >-
  Vous avez envie d'en connaitre d'avantage sur notre Api de Garantie Locataire
  ? C'est par Ici !
---

# 🔍 Débuter avec l'api de la GL

Nous allons dans un premier temps vous donner un exemple de requête attendue par notre api.

Ci-dessous un exemple de requête (appelée "Query" en GraphQL ) nous permettant de créer un utilisateur.

{% code fullWidth="false" %}
```graphql
  mutation createUser(
    $email: Email!
    $password: String!
    $accept_terms: Boolean!
    $accept_prospecting: Boolean!
    $category: UserCategory
  ) {
    createUser(
      input: {
        email: $email
        password: $password
        acceptTerms: $accept_terms
        acceptProspecting: $accept_prospecting
        category: $category
      }
    ) {
      user {
        id
        email
      }
    }
  }
```
{% endcode %}

Nous transmettons ici à l'api par la fonction createUser() divers paramètres tel que :&#x20;

* l'email de ce dernier&#x20;
* son mot de passe
* le fait de savoir si oui ou non ce dernier à accepter nos conditions générales ou autres&#x20;
* la catégorie d'utilisateur à laquelle il appartient ( Salarié en CDI , Fonctionnaire .... )
