# 💡 Indices – Exercice général Signal Forms

## Le modèle
- Commence par l'interface, puis `model = signal<Reservation>({ ... })`.
- Le formulaire : `reservation = form(this.model, (r) => { ...règles... })`.
- Les champs imbriqués s'utilisent naturellement : `[formField]="reservation.contact.email"`.
- Pour les dates, garde des **strings** (`'2026-12-24'`) avec `<input type="date">` : c'est le plus simple.

## Règles de base
```ts
required(r.contact.nom, { message: 'Le nom est obligatoire' });
email(r.contact.email, { message: 'Email invalide' });
pattern(r.contact.telephone, /^04\d{2} \d{2} \d{2} \d{2}$/, { message: '...' });
maxLength(r.commentaire, 200, { message: '...' });
```

## Validateurs personnalisés
- `validate(chemin, (ctx) => ...)` : `ctx.value()` donne la valeur du champ.
- Retourne `{ kind: 'nomErreur', message: '...' }` si erreur, sinon `null`.
- Pour comparer avec un autre champ : `ctx.valueOf(r.dateDepart)`.
- Pour comparer deux dates en string : `new Date(a) > new Date(b)` ou, au format ISO, simplement `a > b`.
- Pour la règle « bébé → pas de business » : dans le validateur du champ `classe`, lis `valueOf(r.voyageurs)` et utilise `some()`.

## Règles conditionnelles
- `required(chemin, { when: (ctx) => ... })` : obligatoire **seulement** si la condition est vraie.
- `hidden(chemin, (ctx) => ...)` : un champ caché n'est **pas validé** (mais pense à ne pas l'afficher dans le template : `@if (!reservation.dateRetour().hidden())`).
- `disabled(chemin, (ctx) => ...)` : pareil pour la désactivation.
- `applyWhen(...)` permet d'appliquer **tout un groupe de règles** sous condition.

## Liste de voyageurs
- `applyEach(r.voyageurs, (v) => { required(v.prenom); ... })` applique les règles à chaque voyageur.
- Min/max d'éléments : `validate(r.voyageurs, ({ value }) => value().length < 1 ? {...} : null)`.
- Ajouter : `this.model.update(m => ({ ...m, voyageurs: [...m.voyageurs, nouveauVoyageur] }))`.
- Supprimer : même idée avec `filter((_, i) => i !== index)`.
- Template : `@for (v of reservation.voyageurs; track $index) { <input [formField]="v.prenom"> }`.

## Affichage des erreurs
- `reservation.contact.email().errors()` → tableau d'erreurs, chacune a un `message`.
- `touched()` pour n'afficher qu'après interaction.
- État global : `reservation().invalid()`, `reservation().submitting()`.

## Récapitulatif
- Tout est un signal → `computed(() => ...)` sur `this.model()` et le prix se recalcule tout seul.
- Nombre de nuits : différence entre les deux dates en millisecondes / `(1000 * 60 * 60 * 24)`.

## Soumission
```ts
async reserver() {
  await submit(this.reservation, async (form) => {
    // simule le serveur (Promise + setTimeout)
    // erreur serveur → return [{ kind: 'serveur', message: '...', fieldTree: form.destination }]
    // succès → return undefined (ou rien)
  });
}
```
- `submit()` marque tout comme touché et n'appelle l'action **que** si le formulaire est valide.
- Pense à `(submit)="$event.preventDefault(); reserver()"` sur le `<form>` (ou un bouton `type="button"`).

## Bonus
- `schema<Voyageur>((v) => { ... })` crée un schéma réutilisable → `applyEach(r.voyageurs, voyageurSchema)`.
- Composant d'erreurs : un `input.required<FieldTree<unknown>>()` (`FieldTree` vient de `@angular/forms/signals`).
- `effect(() => localStorage.setItem('brouillon', JSON.stringify(this.model())))`.
