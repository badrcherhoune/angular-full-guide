# Différence entre Template-Driven et Reactive Forms en Angular

## 1. Template-Driven Forms (Formulaires pilotés par le template)

- **Définition :**  
  Les formulaires sont gérés principalement dans le **template HTML**. La logique côté TypeScript est minimale.

- **Caractéristiques :**  
  - Utilise des directives Angular comme `ngModel`, `ngForm`, `required`, etc.  
  - Idéal pour les formulaires simples.  
  - Validation déclarative directement dans le HTML.  
  - Moins de contrôle sur l’état du formulaire côté TypeScript.  
  - Angular crée automatiquement les objets `FormControl` et `FormGroup` en arrière-plan.

- **Exemple :**  
  ```html
  <form #myForm="ngForm" (ngSubmit)="submit(myForm)">
    <input name="email" ngModel required>
    <button type="submit">Envoyer</button>
  </form>
```
### Avantages

- Simple et rapide pour des formulaires simples.  
- Facile à lire et à maintenir pour des petits projets.  

### Limites

- Difficile à tester.  
- Moins adapté aux formulaires complexes ou dynamiques.
## 2. Reactive Forms (Formulaires réactifs)

### Définition
Les formulaires sont totalement gérés côté TypeScript, et le template se contente de refléter l’état du formulaire.

### Caractéristiques
- Utilise `FormControl`, `FormGroup`, et `FormArray`.  
- Validation définie dans le code TypeScript.  
- Idéal pour les formulaires complexes ou dynamiques.  
- Meilleur contrôle sur l’état du formulaire (`touched`, `dirty`, `valid`, etc.).  
- Facilement testable.  

### Exemple
```ts
this.form = new FormGroup({
  email: new FormControl('', [Validators.required, Validators.email])
});
```

```html
<form [formGroup]="form" (ngSubmit)="submit()">
  <input formControlName="email">
  <button type="submit">Envoyer</button>
</form>
```
### Avantages

- Plus flexible pour les formulaires dynamiques ou complexes.  
- Test unitaire facile.  
- Validation centralisée et réactive aux changements de valeur.  

### Limites

- Plus verbeux et nécessite plus de code.  
- Courbe d’apprentissage plus élevée pour les débutants.
| Caractéristique        | Template-Driven  | Reactive Forms     |
|------------------------|----------------|------------------|
| Gestion                | HTML (template) | TypeScript (code) |
| Contrôle de formulaire | Faible          | Élevé             |
| Validation             | Dans le template| Dans le TypeScript|
| Formulaires dynamiques | Difficile       | Facile            |
| Testabilité            | Difficile       | Facile            |
| Complexité du projet   | Simple          | Complexe          |

