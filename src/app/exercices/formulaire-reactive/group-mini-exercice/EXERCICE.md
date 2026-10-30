# Mini-exercice : FormGroup

## 🎯 Objectif
Regrouper plusieurs champs dans un **FormGroup**, y compris un **groupe imbriqué**.

## 🛠️ Mise en place
```bash
ng g c exercices/formulaire-reactive/group-mini-exercice/inscription
```

## 📋 Consignes
1. Crée un formulaire d'**inscription** avec :
   - prénom (obligatoire)
   - nom (obligatoire)
   - email (obligatoire + format email)
   - âge (obligatoire, minimum 18)
2. Ajoute un **sous-groupe `adresse`** avec :
   - rue
   - ville (obligatoire)
   - code postal (obligatoire, exactement 4 chiffres)
3. Affiche les erreurs sous chaque champ (seulement si touché).
4. Ajoute un bouton **Pré-remplir** qui remplit **seulement** le prénom et la ville.
5. À la soumission, si le formulaire est valide, affiche l'objet complet dans la console.

## ✅ Résultat attendu
À la soumission, on obtient un objet du style :
```json
{
  "prenom": "Sara",
  "nom": "Dupont",
  "email": "sara@mail.com",
  "age": 25,
  "adresse": { "rue": "Rue de la Loi 1", "ville": "Bruxelles", "codePostal": "1000" }
}
```
