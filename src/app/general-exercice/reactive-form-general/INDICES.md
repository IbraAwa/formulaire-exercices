# 💡 Indices – Exercice général Reactive Forms

## Structure
- Utilise `inject(FormBuilder)` (ou `NonNullableFormBuilder`) : ça rend le code beaucoup plus lisible et bien typé.
- Construis le formulaire **par blocs** : commence par `identite`, teste, puis ajoute le reste.
```ts
form = this.fb.group({
  identite: this.fb.group({ ... }),
  compte: this.fb.group({ ... }, { validators: [motsDePasseIdentiques] }),
  typeStage: ['dev'],
  portfolio: [''],
  experiences: this.fb.array([], { validators: [...] }),
  langues: this.fb.array([], { validators: [...] }),
  conditions: [false, Validators.requiredTrue],
});
```

## Validateurs personnalisés
- Validateur simple : `(control: AbstractControl): ValidationErrors | null`.
- Validateur avec paramètre (ex. `ageMinimum(16)`) : une fonction qui **retourne** un `ValidatorFn`.
- Validateur de **groupe** : le `control` reçu est le groupe → `control.get('motDePasse')?.value`.
- Validateur de **FormArray** : `(control as FormArray).controls` ou directement `control.value` (un tableau).
- Pour les doublons : compare la taille du tableau avec celle d'un `new Set(...)` des valeurs en minuscules.
- Pour l'âge : calcule la date « aujourd'hui moins 16 ans » et compare.

## Champ conditionnel (portfolio)
- Écoute `form.controls.typeStage.valueChanges`.
- Selon la valeur : `setValidators([...])` ou `clearValidators()`, puis **toujours** `updateValueAndValidity()`.
- Autre approche possible : `enable()` / `disable()` (un champ désactivé n'est pas validé).
- Pense à te désabonner : `takeUntilDestroyed()` est ton ami.

## FormArray de FormGroup
- Crée une méthode `creerExperience()` qui retourne un nouveau `FormGroup` → réutilisable pour l'ajout **et** pour le bonus « Modifier ».
- Getter : `get experiences() { return this.form.controls.experiences; }`
- Template : `formArrayName="experiences"` → `@for` → `[formGroupName]="$index"` → `formControlName`.
- Limite à 5 : `[disabled]="experiences.length >= 5"`.

## Affichage des erreurs
- Crée une petite méthode `aUneErreur(chemin: string, erreur: string)` pour éviter de répéter `form.get(...)?.hasError(...) && form.get(...)?.touched` partout.
- Les erreurs de groupe sont sur le groupe : `form.controls.compte.hasError('motsDifferents')`.
- `markAllAsTouched()` à la soumission si invalide.

## Soumission
- `getRawValue()` récupère aussi les champs désactivés (contrairement à `value`).
- Stocke les candidatures dans un `signal<Candidature[]>([])` et ajoute avec `update()`.
- Pour vider les FormArray au reset : `clear()`.

## Bonus
- Validateur async : `AsyncValidatorFn` qui retourne un `Observable` → `of(...).pipe(delay(500), map(...))`. Il se met dans `asyncValidators`.
- Statut `PENDING` pendant la vérification → affiche « Vérification... ».
- Modifier : vide les FormArray, recrée les bons groupes avec `push()`, puis `patchValue()`.
