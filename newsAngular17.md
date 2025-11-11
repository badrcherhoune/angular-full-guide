Voici les **nouvelles fonctionnalités principales** de Angular 17 :

* Support de TypeScript **v5.2** : meilleure vérification des types et nouveaux apports langage. ([GeeksforGeeks][1])
* Nouvel API de **flux de contrôle déclaratif** dans les templates : syntaxe simplifiée comme `@if`, `@for`, `@switch` remplaçant partiellement `*ngIf`, `*ngFor`, `*ngSwitch`. ([GeeksforGeeks][2])
* **Chargement différé / lazy‑loading optimisé** avec un bloc `@defer` (views différables) pour retarder le rendu ou le chargement d’une partie du template. ([GeeksforGeeks][1])
* Meilleure prise en charge du rendu côté serveur (SSR) et de l’hydratation : nouvelle prise en charge, amélioration des performances et SEO. ([GeeksforGeeks][2])
* Améliorations de l’expérience développeur & build : intégration de esbuild/Vite pour des builds plus rapides, réduction de taille de bundle. ([daily.dev][3])
* Meilleure documentation, site refait et playground interactif pour Angular 17. ([Medium][4])
* Meilleure intégration des composants autonomes (standalone components) sans nécessité d’`NgModule`, et modularité renforcée. ([syncfusion.com][5])
* Support renforcé de la réactivité granulaire via Angular Signals : suivi fin des changements d’état, ré‑rendu des composants concernés uniquement. ([positiwise.com][6])
* Support amélioré pour l’internationalisation (i18n), accessibilité et éléments personnalisés (custom elements) dans Angular 17. ([positiwise.com]

| Fonctionnalité                         | Nom de fichier typique                                                        |
| -------------------------------------- | ----------------------------------------------------------------------------- |
| **Standalone component**               | `app.component.ts` ou `home.component.ts`                                     |
| **Bootstrap avec standalone**          | `main.ts` (utilisant `bootstrapApplication(AppComponent)`)                    |
| **Signal**                             | `counter.signal.ts` ou intégré dans un composant comme `counter.component.ts` |
| **Routing avec standalone components** | `app.routes.ts` ou `app-routing.module.ts`                                    |
| **Lazy-loaded route avec standalone**  | `feature.module.ts` ou `feature.component.ts`                                 |
| **i18n simplifié**                     | `messages.xlf` ou `messages.fr.xlf`                                           |
| **Template différé / @defer**          | Intégré directement dans le template du composant : `home.component.html`     |


