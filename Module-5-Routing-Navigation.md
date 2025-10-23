# Module 5 : Routing & Navigation dans Angular

## 1) Qu’est-ce que le routing dans Angular ?

Le routing dans Angular est un mécanisme qui permet de naviguer entre les composants d’une application à l’aide des URL.  
Il relie une route (chemin défini dans l’URL) à un composant spécifique, permettant ainsi d’afficher dynamiquement différentes vues sans recharger toute la page.

---

## 2) Comment définir une route dans Angular ?

Pour définir une route dans Angular, on utilise le module `RouterModule` et on configure un tableau de routes qui associe chaque chemin d’URL à un composant.

### 🧩 Étapes principales :

1. Importer `RouterModule` et `Routes` depuis `@angular/router`.
2. Définir un tableau de routes, où chaque route est un objet avec :  
   - `path` → le chemin dans l’URL  
   - `component` → le composant à afficher
3. Importer `RouterModule.forRoot(routes)` dans le module principal (`AppModule`) ou un module de fonctionnalité.
4. Placer dans le template `<router-outlet></router-outlet>` pour afficher le composant correspondant à la route active.
### Remaque:
routerLink naviguer vers une route spécifique depuis le template, sans recharger la page (SPA).
### Exemple :  

En utilisant la directive `routerLink` dans le template :  

```html
<nav>
  <a routerLink="/home">Accueil</a>
  <a routerLink="/about">À propos</a>
</nav>

<router-outlet></router-outlet>
```

# Angular Routing & Navigation

## Navigation avec le service Router
Le service `Router` permet de naviguer entre les différentes routes d'une application Angular.
```typescript
this.router.navigate(['/about']);
```

## Paramètres dynamiques dans les routes
Les routes peuvent contenir des paramètres dynamiques pour transmettre des informations entre les composants.
```typescript
{ path: 'user/:id', component: UserComponent }
```
## Récupération des paramètres dans le composant
`ActivatedRoute` permet de lire les paramètres de la route actuelle depuis un composant.

```typescript
// Exemple : voir l'utilisateur avec l'ID 5
this.router.navigate(['/user', 5]);
```

## Différence entre `forRoot()` et `forChild()`
- `RouterModule.forRoot()` : utilisé dans le module principal pour initialiser le routeur global.  
- `RouterModule.forChild()` : utilisé dans les modules enfants pour ajouter des routes secondaires.

## 4) Lazy Loading
Le **Lazy Loading** dans Angular est un mécanisme qui charge un module uniquement quand il est nécessaire, c’est-à-dire au moment où l’utilisateur navigue vers une route spécifique.

## 5) Guard
Un **Guard** dans Angular est un service qui contrôle l’accès à une route ou la navigation depuis une route. Il permet d’exécuter une logique avant que la route ne soit activée ou désactivée.
### Types courants de Guard

- **CanActivate**  
  Empêche ou autorise l’accès à une route.  
  **Exemple** : vérifier si l’utilisateur est connecté avant d’entrer sur une page.

- **CanDeactivate**  
  Empêche ou autorise la sortie d’une route.  
  **Exemple** : demander confirmation si un formulaire n’est pas sauvegardé avant de quitter la page.
```typescript
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { HomeComponent } from './home/home.component';
import { UserComponent } from './user/user.component';
import { AdminComponent } from './admin/admin.component';
import { NotFoundComponent } from './not-found/not-found.component';
import { AuthGuard } from './guards/auth.guard';
import { CanDeactivateGuard } from './guards/can-deactivate.guard';

const routes: Routes = [
  // Route par défaut
  { path: '', redirectTo: '/home', pathMatch: 'full' },

  // Route simple
  { path: 'home', component: HomeComponent },

  // Route avec paramètre obligatoire
  { path: 'user/:id', component: UserComponent },

  // Route avec paramètre optionnel
  { path: 'user/:id/:tab?', component: UserComponent },

  // Route avec query params et fragment
  { path: 'admin', component: AdminComponent, canActivate: [AuthGuard] },

  // Route avec enfants
  { 
    path: 'dashboard', 
    loadChildren: () => import('./dashboard/dashboard.module').then(m => m.DashboardModule) 
  },

  // Route avec guard pour empêcher la sortie
  { 
    path: 'edit/:id', 
    component: UserComponent, 
    canDeactivate: [CanDeactivateGuard] 
  },

  // Wildcard pour 404
  { path: '**', component: NotFoundComponent }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
```


