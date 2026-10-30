# 💡 Indices – NgForm

- Il faut importer `FormsModule` dans ton composant.
- `#f="ngForm"` sur la balise `<form>` te donne accès au formulaire.
- Chaque champ a besoin de `ngModel` **et** d'un attribut `name`.
- `#email="ngModel"` te donne accès à l'état d'un champ (`touched`, `invalid`...).
- Regarde du côté de `(ngSubmit)` et de `resetForm()`.
