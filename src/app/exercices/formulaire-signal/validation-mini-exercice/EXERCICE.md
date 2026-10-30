# Mini-exercice : Signal Forms – validation & soumission

## 🎯 Objectif
Ajouter des **règles de validation** (classiques et personnalisées) et gérer la **soumission**.

## 🛠️ Mise en place
```bash
ng g c exercices/formulaire-signal/validation-mini-exercice/inscription-signal
```

## 📋 Consignes
1. Modèle : `email`, `motDePasse`, `confirmation`, `age`.
2. Règles :
   - email : obligatoire + format email
   - mot de passe : obligatoire + minimum 8 caractères
   - confirmation : doit être **identique** au mot de passe (validateur perso)
   - âge : minimum 18
3. Chaque règle a son **propre message** d'erreur (défini dans le schéma, pas dans le HTML).
4. Sous chaque champ, affiche la liste de ses messages d'erreur s'il a été touché.
5. Le bouton **S'inscrire** est désactivé si le formulaire est invalide.
6. À la soumission, simule un envoi au serveur (attente d'1 seconde) puis affiche « Inscription réussie ✅ ».

## ✅ Résultat attendu
Un formulaire qui affiche des messages d'erreur clairs, y compris quand la confirmation ne correspond pas.
