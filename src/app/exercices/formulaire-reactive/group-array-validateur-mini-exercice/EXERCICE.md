# Mini-exercice : FormGroup + FormArray + validateurs personnalisés

## 🎯 Objectif
Combiner **FormGroup** et **FormArray** et écrire **tes propres validateurs**.

## 🛠️ Mise en place
```bash
ng g c exercices/formulaire-reactive/group-array-validateur-mini-exercice/commande
```
Crée aussi un fichier `commande.validators.ts` pour tes validateurs.

## 📋 Consignes
1. Crée un formulaire de **commande** :
   - **client** (obligatoire)
   - **articles** : un FormArray de FormGroup, chaque article contient :
     - produit (obligatoire)
     - quantité (obligatoire, minimum 1)
     - prix unitaire (obligatoire, minimum 0)
2. Boutons pour **ajouter** / **supprimer** un article.
3. Affiche le **total** de la commande (somme de quantité × prix).
4. Écris **3 validateurs personnalisés** :

   | Validateur | S'applique sur | Règle |
   |---|---|---|
   | `pasDeChiffre` | le champ client | le nom ne peut pas contenir de chiffre |
   | `auMoinsUnArticle` | le FormArray | il faut au minimum 1 article |
   | `totalMax(500)` | le FormGroup principal | le total ne peut pas dépasser 500 € |

5. Affiche un message clair pour chacune de ces erreurs.
6. Le bouton **Commander** est désactivé si le formulaire est invalide.

## ✅ Résultat attendu
Un formulaire de commande dynamique avec un total calculé et des erreurs personnalisées sur un champ, sur une liste et sur le formulaire entier.
