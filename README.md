1) 🧱 Structure d’un composant Angular

Un composant se compose de trois éléments principaux :

Fichier TypeScript (.ts) → Contient la logique du composant.

Fichier HTML (.html) → Contient le template (la vue).

Fichier CSS (.css ou .scss) → Contient le style associé.

2) 🔹 @Input() : permet au parent d’envoyer des données à son enfant.
🔹 @Output() : permet à l’enfant d’envoyer des événements ou données à son parent.

3)🔹 @ViewChild() : permet d’accéder à un élément ou composant enfant présent dans le template du composant lui-même (dans son propre HTML).

🔹 @ContentChild() : permet d’accéder à un élément ou composant passé depuis l’extérieur via le contenu projeté (<ng-content>).

👉 En résumé :

@ViewChild() → élément dans le template interne du composant.

@ContentChild() → élément dans le contenu inséré depuis le parent.

4)🔹 Une directive structurelle est une directive Angular qui modifie la structure du DOM, c’est-à-dire qu’elle ajoute, supprime ou manipule des éléments HTML dans la page.

📘 Exemples de directives structurelles intégrées :

*ngIf → affiche ou masque un élément selon une condition.

*ngFor → répète un élément pour chaque item d’une liste.

*ngSwitch → affiche un élément selon une valeur donnée.

🔹 Une directive d’attribut est une directive Angular qui modifie l’apparence ou le comportement d’un élément HTML existant, sans changer la structure du DOM.

📘 Exemples de directives d’attribut intégrées :

[ngClass] → ajoute ou retire des classes CSS dynamiquement.

[ngStyle] → applique des styles CSS dynamiquement.

[disabled] → active ou désactive un élément HTML.

5)
[hidden]

C’est une directive d’attribut.

Elle masque l’élément via CSS (display: none) mais l’élément reste dans le DOM.

Exemple :

<div [hidden]="!isVisible">Je suis caché mais toujours dans le DOM</div>


⚠️ Inconvénient : l’élément est toujours présent et peut affecter la performance si utilisé massivement.

6)
🔹 Un Pipe dans Angular est un outil qui transforme ou formate des données avant leur affichage dans le template.

Par exemple : convertir une date, mettre du texte en majuscules, formater un nombre ou une devise.

7)Pipe impur

Angular l’exécute à chaque cycle de détection de changement, même si la valeur n’a pas changé.

Utile pour les objets ou tableaux modifiés sans changer la référence.

Exemple :

@Pipe({ name: 'filter', pure: false }) // pipe impur

8)Composant = directive + template + style
Directive = logique qui agit sur un élément existant sans template

9)Change Detection = mécanisme qui synchronise automatiquement le template avec les données du composant.
