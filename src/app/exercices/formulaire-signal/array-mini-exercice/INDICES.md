# 💡 Indices – Signal Forms (listes)

- Une liste dans le modèle = un simple tableau.
- Pour ajouter / supprimer : modifie le signal avec `update()` (et crée un **nouveau** tableau).
- Dans le template, on peut faire un `@for` directement sur `monForm.taches`.
- `applyEach()` applique des règles à chaque élément du tableau.
- Regarde `disabled()` avec l'option `when`.
- Un `computed()` est parfait pour le compteur.
