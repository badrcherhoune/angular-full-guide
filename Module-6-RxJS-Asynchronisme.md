# RxJS - Reactive Extensions for JavaScript

RxJS est une bibliothèque pour gérer des **flux de données asynchrones** et **événements** de manière **réactive**. Elle est très utilisée dans Angular pour manipuler des données provenant de différentes sources comme les requêtes HTTP, les événements utilisateur, les WebSockets, etc.

## Points clés

### 1. Flux de données
RxJS permet de représenter des événements ou des données qui arrivent **au fil du temps** comme des flux (Streams).  
Exemples : clics sur un bouton, valeurs reçues depuis une API, ou données en temps réel.

### 2. Observables
- Le cœur de RxJS est l’**Observable**, un objet qui émet des valeurs **à tout moment**.  
- Un Observable peut émettre **zéro, une ou plusieurs valeurs** et se terminer ou produire une erreur.

### 3. Abonnement (`subscribe`)
Pour recevoir les valeurs d’un Observable, on s’y abonne avec `subscribe()`.  
On peut définir trois types de réactions :
- `next` → chaque nouvelle valeur émise  
- `error` → si une erreur survient  
- `complete` → lorsque le flux se termine
  
```typescript
const numbers$ = of(1, 2, 3);

numbers$.subscribe({
  next: value => console.log('Valeur émise :', value),
  error: err => console.error('Erreur :', err),
  complete: () => console.log('Flux terminé')
});
```

# 2) 🧊 Observable froid (Cold Observable)

Un **Observable froid** est un flux **qui démarre uniquement lorsqu’un observer s’y abonne**.  
Chaque abonné reçoit **ses propres données indépendantes**, comme si le flux redémarrait pour lui seul.

### 🧠 Exemple conceptuel
C’est comme **regarder une vidéo en ligne** :  
chaque spectateur commence depuis le début au moment où il clique sur “play”.  
Les données sont **rejouées à chaque nouvelle souscription**.

---

# 2) 🔥 Observable chaud (Hot Observable)

Un **Observable chaud** émet des valeurs **indépendamment du nombre d’abonnés**.  
Autrement dit, il **produit déjà des données avant même qu’un observer s’y abonne**.

### 🧠 Exemple conceptuel
C’est comme **regarder un live (diffusion en direct)** :  
si tu rejoins en retard, tu manques ce qui a déjà été diffusé.  
Tous les abonnés **partagent le même flux**.


### 4. Opérateurs
RxJS fournit de nombreux **opérateurs** pour transformer, filtrer, combiner ou gérer le temps dans les flux.  
Exemples : `map`, `filter`, `merge`, `debounceTime`, `switchMap`.

### 5. Avantages
- Gestion facile des événements asynchrones et de la concurrence.  
- Composition et transformation des flux très flexibles.  
- Permet d’écrire un code plus **déclaratif et lisible** pour des scénarios complexes.

## Résumé
RxJS transforme des événements et données asynchrones en **flux observables**, et fournit des outils puissants pour les **manipuler et réagir à leur évolution**.

# Différences entre map, switchMap, mergeMap et concatMap (RxJS)

| Opérateur    | Type de transformation | Gestion des Observables internes | Parallèle ou séquentiel | Annule les précédents ? |
|--------------|----------------------|---------------------------------|------------------------|------------------------|
| `map`        | Valeur → Valeur      | ❌                               | N/A                    | ❌                     |
| `switchMap`  | Valeur → Observable  | ✔                               | Parallèle mais dernier seul | ✔ (les précédents)   |
| `mergeMap`   | Valeur → Observable  | ✔                               | Parallèle              | ❌                     |
| `concatMap`  | Valeur → Observable  | ✔                               | Séquentiel             | ❌                     |

## Explications

### map
- Transforme chaque valeur émise par un Observable.
- Ne gère pas les Observables internes.

### switchMap
- Transforme chaque valeur en un nouvel Observable.
- S’abonne uniquement au dernier Observable émis.
- Les précédents Observables sont annulés si un nouveau arrive.

### mergeMap
- Transforme chaque valeur en un Observable.
- Fusionne tous les Observables émis en parallèle.
- Les résultats sont émis dès qu’ils arrivent, ordre non garanti.

### concatMap
- Transforme chaque valeur en un Observable.
- Les Observables sont exécutés **séquentiellement**, un par un.
- Le suivant ne commence que lorsque le précédent est terminé.



