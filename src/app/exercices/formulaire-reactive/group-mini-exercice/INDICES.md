# 💡 Indices – FormGroup

- `new FormGroup({ ... })` ou `inject(FormBuilder).group({ ... })`.
- Un groupe peut contenir un autre groupe.
- Dans le template : `[formGroup]`, `formControlName` et `formGroupName`.
- Pour accéder à un champ imbriqué : `form.get('adresse.ville')`.
- `patchValue()` permet de remplir **une partie** du formulaire (contrairement à `setValue()`).
- `Validators.pattern()` pour le code postal.
