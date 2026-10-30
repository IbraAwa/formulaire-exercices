# 💡 Indices – Signal Forms (bases)

- Le modèle : `signal({ prenom: '', ... })`.
- Le formulaire : `form(tonSignal)`.
- Il faut importer la directive `FormField` dans le composant.
- Dans le template : `[formField]="monForm.prenom"`.
- L'état d'un champ s'obtient en **appelant** le champ : `monForm.prenom().touched()`.
- Pour réinitialiser : modifie simplement le signal (`set()`).
