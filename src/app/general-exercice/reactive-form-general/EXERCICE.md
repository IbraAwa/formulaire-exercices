# Exercice général : Reactive Forms – Candidature de stage

## 🎯 Objectif
Construire un **vrai formulaire complet** qui réutilise **tout** ce que tu as vu :
FormControl, FormGroup, FormArray, validateurs intégrés, validateurs personnalisés, validateurs de groupe et logique dynamique.

## 🛠️ Mise en place
```bash
ng g c general-exercice/reactive-form-general/candidature
```
Organisation conseillée :
```
reactive-form-general/
├── candidature/              (le composant principal)
├── candidature.validators.ts (tes validateurs)
└── candidature.model.ts      (les interfaces TypeScript)
```

## 📋 Consignes

### 1. Informations personnelles (FormGroup `identite`)
| Champ | Règles |
|---|---|
| prénom | obligatoire, pas de chiffre (validateur perso) |
| nom | obligatoire, pas de chiffre |
| email | obligatoire, format email |
| téléphone | obligatoire, format belge `04XX XX XX XX` |
| date de naissance | obligatoire, le candidat doit avoir **au moins 16 ans** (validateur perso) |

### 2. Compte (FormGroup `compte`)
| Champ | Règles |
|---|---|
| mot de passe | obligatoire, min. 8 caractères, au moins 1 majuscule et 1 chiffre (validateur perso) |
| confirmation | doit être identique au mot de passe (**validateur sur le groupe**) |

### 3. Type de stage
- Un `select` : **Développement**, **Design** ou **Réseau**.
- Si **Design** est choisi → un champ `portfolio` (URL) apparaît et devient **obligatoire**.
- Sinon → le champ disparaît et n'est **plus** validé.

### 4. Expériences (FormArray de FormGroup)
Chaque expérience contient :
- entreprise (obligatoire)
- poste (obligatoire)
- date de début (obligatoire)
- date de fin (facultative, mais si elle est remplie elle doit être **après** la date de début → validateur sur le groupe de l'expérience)

Boutons **ajouter** / **supprimer**. Maximum **5** expériences (le bouton ajouter se désactive).

### 5. Langues (FormArray de FormControl)
- Une liste de langues parlées (texte).
- Au moins **1** langue (validateur sur le FormArray).
- Pas de **doublon** (validateur sur le FormArray, insensible à la casse).

### 6. Conditions
- Une case à cocher « J'accepte les conditions » obligatoire (`Validators.requiredTrue`).

### 7. Soumission & affichage
- Les messages d'erreur apparaissent sous chaque champ quand il est touché.
- Si on clique sur **Envoyer** alors que le formulaire est invalide → tous les champs sont marqués comme touchés pour afficher toutes les erreurs.
- Si c'est valide → la candidature est ajoutée à une liste affichée sous le formulaire (récapitulatif), puis le formulaire est réinitialisé.

## ⭐ Bonus
- Un **validateur asynchrone** sur l'email : simule un appel serveur (500 ms) et refuse les emails déjà présents dans la liste des candidatures.
- Un bouton **Modifier** sur une candidature du récapitulatif qui recharge ses données dans le formulaire.
- Une barre de progression : pourcentage de champs valides.

## ✅ Résultat attendu
Un formulaire de candidature robuste, entièrement typé, qui ne peut être envoyé que lorsqu'il est valide, et qui affiche une liste de candidatures envoyées.
