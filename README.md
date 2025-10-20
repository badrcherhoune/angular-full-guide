1)
Angular est un framework front-end basé sur TypeScript, développé par Google.
Il permet de créer des applications web modernes de type Single Page Application (SPA) avec une architecture modulaire, des composants réutilisables et une gestion efficace du data binding, du routing et des services.
2)
AngularJS utilise JavaScript et une architecture MVC. Angular moderne utilise TypeScript, est basé sur des composants, est plus performant, et offre une CLI puissante et une modularité avancée pour construire des SPA.
3)
Un composant Angular est une classe TS avec @Component() qui regroupe template, logique et styles, et contrôle une partie autonome de l’interface utilisateur.
4)
Le décorateur @Component() sert à définir une classe TypeScript comme composant Angular.
Il permet de regrouper la logique (TS), le template (HTML) et les styles (CSS/SCSS) en une unité autonome et réutilisable.
Il définit également des attributs importants comme le selector (nom de la balise HTML), le template/templateUrl, les styles/styleUrls, les providers, les animations, l’encapsulation et la stratégie de détection des changements.
5)
Un module Angular (NgModule) est une unité logique qui regroupe des composants, directives, pipes et services liés entre eux.
Il sert à organiser l’application en parties modulaires et réutilisables.
Chaque application Angular a au moins un module racine (AppModule) et peut avoir des modules fonctionnels (SharedModule, FeatureModule, etc.) pour mieux structurer le code.

Points clés :
**************

Déclaration (declarations) → liste des composants, directives et pipes du module.

Imports (imports) → autres modules nécessaires pour ce module.

Exports (exports) → éléments du module accessibles à d’autres modules.

Providers (providers) → services disponibles pour ce module.

Bootstrap (bootstrap) → composant principal à lancer au démarrage (dans le module racine).

app.module.ts est le module racine qui organise tous les composants et services de l’application et définit le composant principal à lancer.

6)
BrowserModule → utilisé dans le module racine pour lancer l’application dans le navigateur.

CommonModule → utilisé dans les modules enfants pour accéder aux directives de base comme *ngIf et *ngFor.

💡 Astuce : BrowserModule contient déjà CommonModule, donc on ne l’importe pas dans les modules enfants.

7)
main.ts est le point d’entrée de l’application Angular et sert à lancer le module racine (AppModule) dans le navigateur.

8)
Le Data Binding dans Angular est le mécanisme qui permet de lier les données entre le modèle (classe TypeScript) et la vue (template HTML).
Il permet de mettre à jour automatiquement l’interface utilisateur lorsque les données changent, et inversement, selon le type de binding utilisé.

Types de Data Binding :

Interpolation ({{ }}) → pour afficher des données dans le template.

Property Binding ([property]="value") → pour lier des propriétés HTML à des variables TS.

Event Binding ((event)="method()") → pour lier les événements du template à des méthodes TS.

Two-way Binding ([(ngModel)]="variable") → pour synchroniser automatiquement la vue et le modèle.

9)
Template-Driven Forms :

Le formulaire est construit dans le HTML. Angular lit les directives (ngModel) pour gérer la liaison et la validation.
Idéal pour des formulaires simples et rapides à mettre en place.

Reactive Forms :

Le formulaire est construit dans la classe TypeScript avec FormGroup et FormControl.
La logique, les validations et l’état du formulaire sont centralisés et contrôlés dans le code, ce qui le rend plus robuste et testable.
Idéal pour des formulaires complexes ou dynamiques.

10)
La directive ngModel permet de créer une liaison bidirectionnelle (two-way binding) entre une propriété de la classe TypeScript et un élément du template HTML.
Cela signifie que :

La valeur du champ HTML est automatiquement mise à jour lorsque la variable TypeScript change.

La variable TypeScript est automatiquement mise à jour lorsque l’utilisateur modifie la valeur dans le champ HTML."
