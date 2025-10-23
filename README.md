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

