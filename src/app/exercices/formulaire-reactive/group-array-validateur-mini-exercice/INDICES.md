# 💡 Indices – Validateurs personnalisés

- Un validateur est une fonction : `(control: AbstractControl): ValidationErrors | null`.
- Elle retourne `null` si tout va bien, sinon un objet comme `{ pasDeChiffre: true }`.
- `totalMax(500)` prend un paramètre → c'est une fonction qui **retourne** un `ValidatorFn`.
- On peut mettre un validateur sur un FormArray ou un FormGroup : `{ validators: [...] }` en 2e argument.
- Les erreurs d'un groupe se lisent avec `form.errors?.['totalMax']`.
