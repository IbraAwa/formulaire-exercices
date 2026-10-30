# 💡 Indices – FormArray

- `new FormArray([ new FormControl('') ])`
- Un petit **getter** qui retourne le FormArray simplifie beaucoup le template.
- Dans le template : `formArrayName`, puis une boucle `@for` sur `.controls`.
- Dans la boucle : `[formControlName]="$index"`.
- Regarde `push()`, `removeAt()` et `length`.
