# 💡 Indices – Signal Forms (validation)

- Les règles se mettent dans le 2e argument de `form()` : `form(model, (chemin) => { ... })`.
- Regarde `required`, `email`, `minLength`, `min` (importés de `@angular/forms/signals`).
- Ces fonctions acceptent une option `{ message: '...' }`.
- Pour la confirmation : `validate()` + `valueOf()` pour lire la valeur d'un autre champ.
- Un validateur perso retourne `{ kind: '...', message: '...' }` ou `null`.
- Les erreurs d'un champ : `monForm.email().errors()`.
- Regarde la fonction `submit()`.
