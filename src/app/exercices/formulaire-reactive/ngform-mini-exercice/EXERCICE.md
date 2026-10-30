# Mini-exercice : NgForm

> ℹ️ `NgForm` appartient aux formulaires **template-driven** (pas reactive).
> On le voit ici pour pouvoir comparer avec les Reactive Forms qui suivent.

## 🎯 Objectif
Créer un petit **formulaire de connexion** géré entièrement depuis le template.

## 🛠️ Mise en place
```bash
ng g c exercices/formulaire-reactive/ngform-mini-exercice/login-ngform
```

## 📋 Consignes
1. Le formulaire contient deux champs :
   - **email** : obligatoire, format email valide
   - **mot de passe** : obligatoire, minimum 6 caractères
2. Sous chaque champ, affiche un message d'erreur **uniquement** si le champ a été touché et est invalide.
3. Le bouton **Se connecter** est désactivé tant que le formulaire est invalide.
4. À la soumission :
   - affiche les valeurs dans la console
   - vide le formulaire

## ⭐ Bonus
- Affiche en direct sous le formulaire la valeur du formulaire (en JSON) et son statut (`VALID` / `INVALID`).

## ✅ Résultat attendu
Un formulaire de login qui affiche ses erreurs proprement et ne peut pas être envoyé s'il est invalide.
