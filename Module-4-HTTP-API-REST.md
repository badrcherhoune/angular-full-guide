# 📡 HttpClient dans Angular

1) **HttpClient** est un service Angular moderne (introduit à partir de la version 4.3) qui permet de faire des requêtes HTTP (**GET, POST, PUT, DELETE**) vers un serveur ou une API.

Il offre :

- La gestion automatique des réponses JSON.  
- La possibilité d’utiliser des types génériques pour typer les réponses.  
- La prise en charge des intercepteurs (**HttpInterceptor**) pour gérer headers, authentification ou logging.  
- Une intégration complète avec **RxJS**, ce qui permet de gérer facilement les flux de données asynchrones et les erreurs.

**En résumé :**  
HttpClient = outil Angular moderne et sécurisé pour communiquer avec des API HTTP.


E) **Exemple**
Voici un exemple clair d’une classe TypeScript Angular qui montre comment effectuer les quatre types de requêtes HTTP avec HttpClient :

```typescript
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { Observable } from 'rxjs';

@Injectable({
  providedIn: 'root'
})
export class ApiService {

  private apiUrl = 'https://api.example.com/items';

  constructor(private http: HttpClient) { }

  // GET - récupérer tous les items
  getItems(): Observable<any> {
    return this.http.get(this.apiUrl);
  }

  // POST - créer un nouvel item
  createItem(item: any): Observable<any> {
    return this.http.post(this.apiUrl, item);
  }

  // PUT - mettre à jour un item existant
  updateItem(id: number, item: any): Observable<any> {
    return this.http.put(`${this.apiUrl}/${id}`, item);
  }

  // DELETE - supprimer un item
  deleteItem(id: number): Observable<any> {
    return this.http.delete(`${this.apiUrl}/${id}`);
  }
}
```

3) **Gestion des erreurs HTTP**

Dans Angular, on gère les erreurs HTTP principalement avec **RxJS** et l’opérateur **catchError**.

**Étapes principales :**

1. Utiliser `pipe()` sur l’Observable retourné par HttpClient.  
2. Appliquer `catchError()` pour intercepter les erreurs.  
3. Traiter ou relancer l’erreur selon le besoin.
```typescript
import { catchError } from 'rxjs/operators';
import { throwError } from 'rxjs';

this.httpClient.get('https://api.example.com/items')
  .pipe(
    catchError(error => {
      console.error('Erreur HTTP détectée :', error);
      // On peut transformer ou relancer l'erreur
      return throwError(() => error);
    })
  )
  .subscribe(
    data => console.log(data),
    err => console.log('Erreur reçue dans subscribe :', err)
  );
```

**Points clés :**
*. catchError intercepte les erreurs au niveau de l’Observable.

*. throwError permet de relancer l’erreur si nécessaire.

*. On peut centraliser la gestion des erreurs via un HttpInterceptor pour toutes les requêtes.

4) **HttpInterceptor**

Un **HttpInterceptor** est une classe spéciale dans Angular qui permet d’intercepter toutes les requêtes et réponses HTTP effectuées avec HttpClient.

**🔍 Son rôle :**

- Agir comme un intermédiaire entre ton application et le serveur.  
- Avant qu’une requête parte ou qu’une réponse arrive, l’intercepteur peut :  
  - Ajouter ou modifier des headers (ex : token d’authentification).  
  - Gérer les erreurs globalement.  
  - Afficher un loader pendant les appels réseau.  
  - Faire du logging ou du monitoring des requêtes.

exemple

```typescript
import { Injectable } from '@angular/core';
import { HttpInterceptor, HttpRequest, HttpHandler, HttpEvent } from '@angular/common/http';
import { Observable } from 'rxjs';

@Injectable()
export class AuthInterceptor implements HttpInterceptor {
  intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
    // Ajouter un header Authorization à chaque requête
    const authReq = req.clone({
      setHeaders: {
        Authorization: 'Bearer mon-token'
      }
    });
    return next.handle(authReq);
  }
}
```

5) **Observable**

Un **Observable** est un flux de données asynchrones que ton application observe et réagit à mesure que les données arrivent.

**👉 Caractéristiques :**

- Il émet des valeurs au fil du temps, contrairement à une valeur unique comme une variable classique.

```typescript
import { Observable } from 'rxjs';

const monObservable = new Observable(observer => {
  observer.next('👋 Bonjour');           // next
  observer.next('🌞 Bienvenue');        // next
  observer.error('⚠️ Une erreur !');    // error
  observer.complete();                  // complete (ne sera pas appelé après error)
});

monObservable.subscribe(
  valeur => console.log('Next :', valeur),      // next
  err => console.error('Erreur :', err),        // error
  () => console.log('Flux terminé ✅')           // complete
);
```



6) **Comparaison Observable vs Promise**

| Caractéristique         | Observable                                               | Promise                                 |
| ----------------------- | -------------------------------------------------------- | --------------------------------------- |
| **Valeurs émises**      | 0 à plusieurs valeurs dans le temps                      | Une seule valeur                        |
| **Lazy**                | Oui, l’Observable ne s’exécute qu’au `subscribe()`       | Non, la Promise s’exécute immédiatement |
| **Annulation**          | Oui, possible avec `unsubscribe()`                       | Non, pas possible                       |
| **Opérateurs RxJS**     | Oui, on peut transformer et combiner les flux            | Non                                     |
| **Flux continu**        | Supporte les flux continus ou événements                 | Ne gère qu’une réponse unique           |
| **Gestion des erreurs** | Peut émettre plusieurs erreurs ou valeurs après un délai | Une seule erreur possible               |

Résumé simple :

Observable = flux de données asynchrone, multiple et annulable.

Promise = résultat asynchrone unique et non annulable.


7) **subscribe() dans Angular / RxJS**

**subscribe()** est une méthode des Observables.

Elle permet de s’abonner à un flux de données pour recevoir ce que l’Observable émet.

On peut passer jusqu’à trois callbacks :  

- **next** → appelé à chaque valeur émise par l’Observable  
- **error** → appelé si l’Observable rencontre une erreur  
- **complete** → appelé quand l’Observable a fini d’émettre toutes ses valeurs