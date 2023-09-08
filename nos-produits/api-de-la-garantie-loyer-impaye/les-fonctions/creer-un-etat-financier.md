# Créer un État financier

Cette fonction permet de transmettre les informations financières (revenus) d'un locataire ou d'un référent.

```graphql
mutation {
  createFinancialState(
    input: {
      ownerId: $userId
      activityBonus: $activityBonus
      alimony: $alimony
      annuities: $annuities
      intermittentIncome: $intermittentIncome
      licensedProfessionalIncome: $licensedProfessionalIncome
      maternityLeaveBenefit: $maternityLeaveBenefit
      militaryIncome: $militaryIncome
      netMonthlyIncome: $netMonthlyIncome
      netSalaryMonthlyIncome: $netSalaryMonthlyIncome
      propertyIncome: $propertyIncome
      retirementPensionMonthlyIncome: $retirementPensionMonthlyIncome
      savings: $savings
      socialCareBenefit: $socialCareBenefit
      socialFamilyBenefit: $socialFamilyBenefit
      unemploymentAllowance: $unemploymentAllowance
      scholarship: $scholarship
    }
  ) {
    financialState {
      ...FinancialStateFragment
    }
  }
}
```
