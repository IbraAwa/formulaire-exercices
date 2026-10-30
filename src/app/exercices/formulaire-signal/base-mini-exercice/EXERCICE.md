# Mini-exercice : Signal Forms – les bases

> ℹ️ Les Signal Forms se trouvent dans `@angular/forms/signals`.
> Le principe : **ton modèle est un signal**, et le formulaire est construit à partir de ce signal.

## 🎯 Objectif
Créer un premier formulaire avec `form()` et le relier au template.

## 🛠️ Mise en place
```bash
ng g c exercices/formulaire-signal/base-mini-exercice/profil
```

## 📋 Consignes
1. Crée un signal `profil` qui contient :
   - prénom (texte)
   - nom (texte)
   - âge (nombre)
   - newsletter (booléen → case à cocher)
2. Crée le formulaire à partir de ce signal et relie chaque champ à un input.
3. Affiche **en direct** sous le formulaire :
   - le modèle complet en JSON
   - une phrase du style : `Bonjour Sara Dupont, tu as 25 ans`
4. Affiche pour le champ **prénom** les états `touched` et `dirty`.
5. Ajoute un bouton **Réinitialiser** qui remet le modèle à ses valeurs de départ.

## ✅ Résultat attendu
Quand on tape dans un input, le signal se met à jour tout seul (et inversement).
