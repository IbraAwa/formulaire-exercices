# Exercice général : Signal Forms – Réservation de voyage

## 🎯 Objectif
Construire un formulaire complet avec **Signal Forms** qui réutilise tout :
modèle en signal, `form()`, `[formField]`, validateurs intégrés, validateurs personnalisés, validation entre champs, champs conditionnels, listes et soumission.

## 🛠️ Mise en place
```bash
ng g c general-exercice/signal-form-general/reservation
```
Organisation conseillée :
```
signal-form-general/
├── reservation/              (le composant principal)
├── reservation.schema.ts     (le schéma de validation)
└── reservation.model.ts      (les interfaces TypeScript)
```

## 📋 Consignes

### 1. Le modèle
Crée une interface `Reservation` et un signal initialisé avec des valeurs vides :
```
Reservation
├── contact        { nom, email, telephone }
├── destination    (texte)
├── dateDepart     (texte au format date)
├── dateRetour     (texte au format date)
├── allerSimple    (booléen)
├── classe         'eco' | 'business'
├── voyageurs      [{ prenom, nom, age }]
├── assurance      (booléen)
├── numeroCarte    (texte)
└── commentaire    (texte)
```

### 2. Règles de validation
| Champ | Règles |
|---|---|
| contact.nom | obligatoire |
| contact.email | obligatoire + format email |
| contact.telephone | obligatoire + format `04XX XX XX XX` |
| destination | obligatoire, choisie dans une liste (ex : Paris, Rome, Tokyo, New York) |
| dateDepart | obligatoire, **pas dans le passé** (validateur perso) |
| dateRetour | obligatoire **sauf** si aller simple, et doit être **après** la date de départ |
| voyageurs | au moins **1** voyageur, maximum **6** |
| voyageur.prenom / nom | obligatoires |
| voyageur.age | obligatoire, entre 0 et 120 |
| numeroCarte | obligatoire **seulement** si assurance cochée, 16 chiffres |
| commentaire | maximum 200 caractères |

Chaque règle a un **message** clair défini dans le schéma.

### 3. Champs conditionnels
- Si **aller simple** est coché → le champ date de retour est **caché** et non validé.
- Si **assurance** n'est pas cochée → le champ numéro de carte est **désactivé**.
- S'il y a un voyageur de **moins de 2 ans**, la classe **business** est interdite (erreur sur le champ classe).

### 4. Voyageurs (liste dynamique)
- Boutons **ajouter** / **supprimer** un voyageur.
- Le bouton ajouter se désactive à 6 voyageurs.

### 5. Récapitulatif en direct
Affiche à côté du formulaire (avec des `computed`) :
- le nombre de voyageurs
- le nombre de nuits (si aller-retour)
- un **prix estimé** : 200 €/voyageur en éco, 500 €/voyageur en business, +30 €/voyageur avec assurance, enfants de moins de 12 ans à -50 %.

### 6. Soumission
- Bouton **Réserver** désactivé si le formulaire est invalide ou en cours d'envoi.
- Utilise `submit()` : simule un appel serveur de 1 s.
- Si la destination est « Tokyo », le « serveur » renvoie une erreur « Plus de places disponibles » qui doit s'afficher **sur le champ destination**.
- Sinon : affiche un message de confirmation et réinitialise le modèle.

## ⭐ Bonus
- Mets le schéma dans un fichier séparé avec `schema()` et réutilise un schéma `voyageurSchema` pour chaque voyageur.
- Crée un petit composant `<app-erreurs [champ]="...">` qui affiche les erreurs de n'importe quel champ.
- Sauvegarde automatiquement le brouillon dans le `localStorage` avec un `effect()`.

## ✅ Résultat attendu
Un formulaire de réservation entièrement piloté par des signaux, avec des règles conditionnelles, une liste de voyageurs et un prix qui se recalcule tout seul.
