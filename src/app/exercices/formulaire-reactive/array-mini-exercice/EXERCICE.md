# Mini-exercice : FormArray

## 🎯 Objectif
Gérer une **liste dynamique** de champs.

## 🛠️ Mise en place
```bash
ng g c exercices/formulaire-reactive/array-mini-exercice/competences
```

## 📋 Consignes
1. Crée un formulaire avec :
   - un champ **nom** (obligatoire)
   - une liste de **compétences** (FormArray)
2. Au départ, la liste contient **une** compétence vide.
3. Un bouton **+ Ajouter** ajoute un nouveau champ compétence.
4. Chaque compétence a un bouton **🗑 Supprimer** à côté.
5. Chaque compétence est obligatoire.
6. Affiche le nombre de compétences (ex : `3 compétence(s)`).
7. À la soumission, affiche les valeurs dans la console.

## ⭐ Bonus
- Empêche de supprimer la dernière compétence.

## ✅ Résultat attendu
```json
{ "nom": "Sara", "competences": ["Angular", "TypeScript", "CSS"] }
```
