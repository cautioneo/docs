---
description: >-
  Cette fonction permet de renseigner les informations financières, de revenus
  et de capital d'un utilisateur.
---

# Création des données financières

Ces informations sont catégorisées selon la situation professionnelle de l'utilisateur, la liste est disponible [ici](https://cautioneo.github.io/cautioneo-design/csp.html).

```graphql
mutation {
  createFinancialState(
    input: {
      clientMutationId: "YOUR_CHOICE_NOT_MANDATORY"
      userId: "ID"
      activityBonus: 0
      alimony: 0
      annuities: 0
      savings: 0
      intermittentIncome: 0
      licensedProfessionalIncome: 0
      militaryIncome: 0
      netMonthlyIncome: 0
      netSalaryMonthlyIncome: 0
      propertyIncome: 0
      retirementPensionMonthlyIncome: 0
      maternityLeaveBenefit: 0
      socialCareBenefit: 0
      socialFamilyBenefit: 0
      unemploymentAllowance: 0
    }
  ) {
    financialState {
      id
      user {
        email
      }
    }
    errors
    clientMutationId
  }
}
```
