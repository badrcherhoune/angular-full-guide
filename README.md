1)Le routing dans Angular est un mécanisme qui permet de naviguer entre les composants d’une application à l’aide des URL.
Il relie une route (chemin défini dans l’URL) à un composant spécifique, permettant ainsi d’afficher dynamiquement différentes vues sans recharger toute la page.

2)Pour définir une route dans Angular, on utilise le module RouterModule et on configure un tableau de routes qui associe chaque chemin d’URL à un composant.

🧩 Étapes principales :

Importer RouterModule et Routes depuis @angular/router.

Définir un tableau de routes, où chaque route est un objet avec :

path → le chemin dans l’URL,

component → le composant à afficher.

Importer RouterModule.forRoot(routes) dans le module principal (AppModule ou un module de fonctionnalité).

Placer <router-outlet></router-outlet> dans le template pour afficher le composant correspondant à la route active.

exemple:
En utilisant la directive routerLink dans le template :
```html
<a routerLink="/about">Aller à la page À propos</a>
remaque routerLink naviguer vers une route spécifique depuis le template, sans recharger la page (SPA).
```


En utilisant le service Router dans le code TypeScript :
this.router.navigate(['/about']);

En définissant un paramètre dynamique dans la route avec :id :

{ path: 'user/:id', component: UserComponent }


En naviguant avec une valeur de paramètre :

<a routerLink="/user/5">Voir l’utilisateur 5</a>


ou en TypeScript :

this.router.navigate(['/user', 5]);


En récupérant le paramètre dans le composant avec ActivatedRoute :pour lire les infos de la route actuelle.

this.route.snapshot.paramMap.get('id');
3)RouterModule.forRoot() : utilisé dans le module principal pour initialiser le routeur global.
RouterModule.forChild() : utilisé dans les modules enfants pour ajouter des routes secondaires.

4)Le Lazy Loading dans Angular est un mécanisme qui charge un module uniquement quand il est nécessaire, 
c’est-à-dire au moment où l’utilisateur navigue vers une route spécifique.

5) Un Guard dans Angular est un service qui contrôle l’accès à une route ou la navigation depuis une route. Il permet d’exécuter une logique avant
que la route ne soit activée ou désactivée.

🔹 Types courants :

CanActivate
Empêche ou autorise l’accès à une route.

Exemple : vérifier si l’utilisateur est connecté avant d’entrer sur une page.

CanDeactivate
Empêche ou autorise la sortie d’une route.

Exemple : demander confirmation si un formulaire n’est pas sauvegardé avant de quitter la page.
