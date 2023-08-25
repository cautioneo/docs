# Qu'est ce que GraphQL ?

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

C'est le mot clé pour définir une requête d'écriture des données de l'API (équivalent en `REST` : `PUT` / `PATCH` / `DELETE`).

Elles permettent donc de récupérer les informations d'un objet ou d'une fonction, mais pas d'en modifier la valeur.

Chez Cautioneo nous utilisons la syntaxe [Relay](quest-ce-que-graphql.md#graphql-relay) pour matérialiser les attributs à enregistrer / modifier via l'argument `input` de la fonction de mutation.

#### Subscription

#### Fragments

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
