# Créer un Locataire

Cette fonction permet de créer un locataire.

Plusieurs locataires peuvent constituer le dossier :&#x20;

* 1 pour une personne seule
* 2 pour un couple (concubinnage, marié ou pacsé)
* jusqu'à 4 dans le cadre d'une collocation

Lesquels seront couvert par la garantie.

```graphql
mutation {
    createGliRenter(
        input: {
            clientMutationId: "YOUR_CHOICE_NOT_MANDATORY"
            pbiSubscriptionId: "ID"
            firstName: "Pierre"
            lastName: "Henri"
            category: MILITARY
            seniority: MORE_THAN_12_MOUNTHS
            rentSeniority: MORE_THAN_6_MOUNTHS
            employmentContractEndOn: "2023-04-01"
            birthdate: "1990-06-15"
            trialPeriodEndOn: "2023-04-01"
        }
    ) { 
        createGliRenter {
            id 
        }
        errors
        clientMutationId
    }
}
```



{% hint style="info" %}
Un locataire étudiant sans revenu peut présenter jusqu'à deux référents de confiance.

Voir [Créer un référent](creer-un-referent.md).
{% endhint %}
