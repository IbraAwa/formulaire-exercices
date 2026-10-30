# Mini-exercice : Signal Forms – listes dynamiques

## 🎯 Objectif
Gérer une **liste** dans un Signal Form et appliquer des règles à **chaque élément**.

## 🛠️ Mise en place
```bash
ng g c exercices/formulaire-signal/array-mini-exercice/todo-signal
```

## 📋 Consignes
1. Modèle : un `titre` de liste + un tableau de `taches`. Chaque tâche contient :
   - libellé (obligatoire, minimum 3 caractères)
   - faite (booléen)
2. Boutons **+ Ajouter une tâche** et **🗑 Supprimer** pour chaque tâche.
3. Affiche le compteur : `2 / 5 tâches faites`.
4. Quand une tâche est **faite**, son libellé devient **désactivé** (non modifiable).

## ✅ Résultat attendu
Une todo-list où chaque tâche est validée individuellement.
