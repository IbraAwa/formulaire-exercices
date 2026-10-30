# Mini-exercice : FormControl

## 🎯 Objectif
Manipuler **un seul champ** réactif : sa valeur, ses validateurs et son état.

## 🛠️ Mise en place
```bash
ng g c exercices/formulaire-reactive/control-mini-exercice/recherche-fruit
```

## 📋 Consignes
1. Crée un champ **recherche** :
   - obligatoire
   - minimum 3 caractères
2. Affiche une liste de fruits (ex : pomme, poire, banane, fraise, framboise, kiwi...).
3. Quand l'utilisateur tape, la liste se **filtre en direct** selon la recherche.
4. Affiche sous le champ :
   - la valeur actuelle
   - les états `valid`, `touched`, `dirty`
   - un message d'erreur adapté (champ vide **ou** trop court)
5. Ajoute deux boutons :
   - **Vider** : remet le champ à zéro
   - **Exemple** : met la valeur `"fra"` dans le champ depuis le code

## ✅ Résultat attendu
Un champ de recherche qui filtre une liste et qui montre son état en temps réel.
