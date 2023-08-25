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

#### Mutation

#### Subscription



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
