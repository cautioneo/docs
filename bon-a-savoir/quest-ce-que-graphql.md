# 🧑🏫 Qu'est ce que GraphQL ?

### Introduction

[GraphQL](https://graphql.org/) est un protocole d'API créé par 2 ingénieurs de Facebook, qui souhaitaient répondre à des soucis de chargement de données et de réduction de bande passante.

C'est pourquoi on peut y retrouver des fonctionnalités de base que l'ont ne retrouve pas systématiquement dans d'autres protocoles d'API qui sont :&#x20;

* Sélection des champs retournés par le serveur (optimisation du payload et du volume de la réponse)
* Imbrication de champs (aka: Nesting, possibilité de demander des attributs d'une entité rattachée à une autre)
* Mutualisation des requêtes en un appel HTTP (aka: Batch)
* Temp réel grâce à un système PUB/SUB basé sur WebSocket
* Schéma déclaratif des données et des fonctions (toutes les entités de l'API sont décrites en un fichier disponible sur demande et qui permet donc de la documenter)
* Gestion d'erreur côté client (si la requête est mal formée, en regard de la syntaxe et du Schéma de l'API, c'est le client qui détecte l'erreur et non le serveur)

### Principes

#### Query

C'est le mot clé pour définir une requête de lecture des données de l'API (équivalent en `REST`: `GET`).

Elles permettent donc de récupérer les informations d'un objet ou d'une fonction, mais pas d'en modifier la valeur.

{% hint style="warning" %}
**Spécificité de l'API Cautioneo**

Les `ID` des objets sont uniques et sont encapsulés dans une chaîne de caractère base64 contenant l'ID interne (uuid) de l'objet et comportant une date d'expiration et une signature.

Ainsi les`ID` obtenus depuis l'API ne peuvent être utilisés que dans cette API et ne peuvent provenir que de cette API, ils ne peuvent donc être générés / devinés par un acteur extérieur.

Certains objets comme `User` ont une date d'expiration dans leur `ID` ce qui les protège d'une fuite de donnée ou d'une interception par un acteur extérieur.
{% endhint %}

#### Mutation

C'est le mot clé pour définir une requête d'écriture des données de l'API (équivalent en `REST` : `POST` / `PUT` / `PATCH` / `DELETE`).

Elles permettent donc de modifier un objet et de récupérer comme dans une `query` les valeurs de cet objet.

Chez Cautioneo nous utilisons la syntaxe [Relay](quest-ce-que-graphql.md#graphql-relay) pour matérialiser les attributs à enregistrer / modifier via l'argument `input` de la fonction de mutation.

Afin de marquer si un argument est obligatoire ou non, la syntaxe GraphQL utilise un `!` après le type d'argument lorsqu'il est obligatoire. Ce qui donne :&#x20;

```graphql
mutation uneMutation(
  $arg1: ID! # Required
  $arg2: String # Optional
)
```

**ClientMutationId**

Les mutations peuvent être effectuées en Batch (ex: créer plusieurs comptes utilisateur en 1 requête), cependant l'ordre dans lequel sont traitées ses mutations n'est pas nécessairement l'ordre transmit par le client au serveur.

Afin de faire la corrélation entre les mutations d'une même requête, chaque fonctione de mutation peut inclure un argument `clientMutationId` qui est une chaîne de caratère choisie par le client de l'API.

Cette valeur sera retournée à l'identique par le serveur dans la réponse de chaque mutation, ce qui permet au client de ne pas mélanger les résultats des mutations.

```graphql
mutation createTwoUsers($email1: String!, $email2: String!) {
  createUser(input: { email: $email1, clientMutationId: "fonction1" }) {
    user {
      id
      email
    }
    clientMutationId
  }
  createUser(input: { email: $email2, clientMutationId: "fonction2" }) {
    user {
      id
      email
    }
    clientMutationId
  }
}
```

#### Subscription

Les `Subscription` sont des requêtes Pub/Sub qui vous permettent d'être alerté en temps réel d'un événement. C'est le serveur d'API qui détermine les types de `Subscription` possibles, leur nomenclature et leurs arguments.

Elles ont la même syntaxe qu'une mutation.

{% hint style="info" %}
Le mot clé `Subscription` étant réservé à cet usage, c'est pour cela que l'objet représentant un dossier Cautioneo s'appelle `CautioneoSubscription` ou `PbiSubscription`.
{% endhint %}

#### Fragments

Les fragments sont des éléments de requête pré-construits et réutilisables.

Ils peuvent être fournis par l'API elle-même ou définie côté client afin de simplifier l'écriture des requêtes.

Elles se présente sous cette forme :&#x20;

```graphql
fragment UserFragment on User {
  email
  firstName
  lastName
  gender
}
```

Et peuvent être utilisé dans les requêtes comme ceci :&#x20;

```graphql
query getUserWithFragment($id: ID!) {
  node(id: $id) {
    id
    ...UserFragment
  }
}
```

### [GraphQL Relay](https://relay.dev/docs/)

C'est une extension du protocole GraphQL qui a pour but de définir certains principes qui restent libres dans l'utilisation du protocole. En voici une liste non exhaustive, mais qui est utilisée dans l'API Cautioneo

#### Node

Chaque objet de l'API Cautioneo dérive de l'interface Node et peut donc être obtenu via son ID par une seule et même query : `node`

Ainsi pour obtenir un `User` on peut s'addresser à l'API comme ceci :&#x20;

```graphql
query getUser($id: ID!) {
  node(id: $id) {
    ... on User {
      email
    }
  }
}
```

#### Pagination

La pagination se fait par curseur et non pas numéro de page.

Cela permet de garder une cohérence lors du parcours d'une collection si celle-ci est amenée à changer.

Cette technique est souvent appliquée lors de l'implémentation de fil d'actualité (Twitter, Facebook, Instagram, etc...)

Une explication très complète est disponible [ici](https://relay.dev/graphql/connections.htm), mais en voici un résumé :&#x20;

```graphql
# Nous souhaitons obtenir la liste des documents d'un dossier :
query {
  node(id: "ID") {
    ... on CautioneoSubscription {
      documents(
        first: 10 # Obtenir les 10 premiers enregistrements
        last: 10 # Obtenir les 10 derniers enregistrements
        after: "CURSOR" # Marqueur de début de liste (pour obtenir les enregistrements après ce marqueur)
        before: "CURSOR" # Marqueur de fin de liste (pour obtenir les enregistrements avant ce marqueur)
      ) {
        edges { # collection des enregistrements
          cursor # identifiant de l'enregistrement dans la liste afin de pouvoir la parcourir à partir de cet enregistrement
          node { # un enregistrement auquel il faut demander les attributs souhaités
            id
          }
        }
        totalCount # Nombre total d'enregistrements
        pageInfo {
          hasNextPage # Y-a-t-il d'autres enregistrement après ?
          hasPreviousPage # Y-a-t-il d'autres enregistrement avant ?
          startCursor # Premier curseur de la liste
          endCursor # Dernier curseur de la liste
        }
      }
    }
}
```

### Implémentations

Vous pouvez retrouver l'ensemble des implémentations de GraphQL côté client ou côté serveur sur le site de [graphql.org](https://graphql.org/code/)

En voici une liste non exhaustive :

| Langage    | Librairie la plus répandue                                   |
| ---------- | ------------------------------------------------------------ |
| PHP        | [API Platform](https://api-platform.com/)                    |
| JavaScript | [ApolloGraphQL](https://www.apollographql.com/)              |
| Python     | [Graphene](https://graphene-python.org/)                     |
| Java       | [GraphQL-Java](https://github.com/graphql-java/graphql-java) |
| Ruby       | [GraphQL-Ruby](https://graphql-ruby.org/)                    |
| Go         | [GraphQL-Go](https://github.com/graphql-go/graphql)          |
