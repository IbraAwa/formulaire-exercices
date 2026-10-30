# 💡 Indices – FormControl

- Importer `ReactiveFormsModule`.
- `new FormControl('', [Validators.required, ...])`
- Dans le template : `[formControl]="..."`.
- `hasError('minlength')` pour savoir quelle erreur afficher.
- Pour réagir aux changements : `valueChanges` (ou `toSignal()`).
- Regarde `setValue()` et `reset()`.
