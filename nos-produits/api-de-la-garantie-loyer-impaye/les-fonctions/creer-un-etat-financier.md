# Créer un état financier

Cette fonction permet de créer l'état financier d'un locataire ou d'un référent&#x20;

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
