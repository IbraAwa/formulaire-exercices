# Formulaire – Exercices Angular

Projet d'entraînement sur les formulaires Angular : **Reactive Forms** et **Signal Forms**.

## 🚀 Lancer le projet
```bash
npm install
ng serve
```
Puis ouvre http://localhost:4200

## 📁 Organisation

```
src/app/
├── exercices/                          → mini-exercices, un concept à la fois
│   ├── formulaire-reactive/
│   │   ├── ngform-mini-exercice/                 NgForm (template-driven, pour comparer)
│   │   ├── control-mini-exercice/                FormControl
│   │   ├── group-mini-exercice/                  FormGroup
│   │   ├── array-mini-exercice/                  FormArray
│   │   └── group-array-validateur-mini-exercice/ FormGroup + FormArray + validateurs perso
│   └── formulaire-signal/
│       ├── base-mini-exercice/                   form(), [formField], état des champs
│       ├── validation-mini-exercice/             règles, validateurs perso, submit()
│       └── array-mini-exercice/                  listes, applyEach(), disabled()
└── general-exercice/                   → gros exercices qui reprennent tout
    ├── reactive-form-general/          Candidature de stage (Reactive Forms)
    └── signal-form-general/            Réservation de voyage (Signal Forms)
```

Chaque dossier d'exercice contient :
- `EXERCICE.md` → l'énoncé
- `INDICES.md` → des indices (à lire seulement si tu bloques 😉)
- `fantome.ts` → fichier vide qui garde le dossier sur GitHub, à supprimer quand tu crées ton composant

## 🧭 Ordre conseillé
1. Les mini-exercices **Reactive Forms** dans l'ordre : ngform → control → group → array → group-array-validateur
2. L'exercice général **Reactive Forms**
3. Les mini-exercices **Signal Forms** : base → validation → array
4. L'exercice général **Signal Forms**

## 🔗 Afficher un exercice
Ajoute une route vers ton composant dans `src/app/app.routes.ts`, par exemple :
```ts
{ path: 'form-control', component: RechercheFruit },
```
puis ajoute un lien dans `src/app/app.html`.
