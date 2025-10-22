# Cours : Les Services Angular

## 1. Définition d'un Service Angular

Un service Angular est une **classe TypeScript** décorée avec `@Injectable` qui :

- Contient des **logiques métier** ou des **requêtes HTTP**
- Fournit des **fonctionnalités réutilisables**
- Permet de **partager des données**
- Peut être **injectée** dans des composants ou d'autres services
- Est **réutilisable** dans toute l'application

**Création d'un service avec Angular CLI :**
```t
ng generate service nom-du-service
# ou version courte :
ng g s nom-du-service
```

# 2. Décorateur @Injectable et Configuration

## 📋 Introduction
Le décorateur `@Injectable()` permet de configurer la portée et la disponibilité des services dans Angular.

## 🎯 Options de providedIn

| Option | Portée | Description |
|--------|--------|-------------|
| `'root'` | **Singleton global** | Service disponible partout dans l'application |
| `'any'` | **Nouvelle instance par injecteur** | Instance séparée pour chaque composant |
| `'platform'` | **Partagé entre applications** | Service partagé entre toutes les apps Angular sur la même plateforme |
| `ModuleName` | **Limitée à un module** | Service limité à un module spécifique |

## 🔄 Comparaison des méthodes

**`providedIn: 'root'`** → Service singleton global, disponible partout dans l'application

# 3. Injection de Dépendances (DI)

L'injection de dépendances (DI) est un mécanisme qui permet à Angular de fournir automatiquement aux composants ou services les objets dont ils ont besoin, sans qu'ils aient à les créer eux-mêmes.

# 4. L'Injector Angular

L'**Injector** est le mécanisme d'Angular qui gère la création et la fourniture des instances des services.

## 🎯 Rôle de l'Injector

- Il sait quelles dépendances fournir à chaque composant ou service
- Il résout automatiquement les services déclarés dans `providedIn` ou `providers`
- C'est le moteur derrière l'injection de dépendances

## 🔄 Fonctionnement

L'Injector maintient un conteneur des dépendances et les fournit lorsqu'elles sont demandées via le constructeur :

```typescript
import { Injectable } from '@angular/core';

export interface User {
  id: number;
  name: string;
}

@Injectable({
  providedIn: 'root' // service singleton global
})
export class UserService {
  private users: User[] = [
    { id: 1, name: 'Alice' },
    { id: 2, name: 'Bob' }
  ];

  constructor() {}

  // Obtenir tous les utilisateurs
  getUsers(): User[] {
    return this.users;
  }

  // Ajouter un utilisateur
  addUser(user: User) {
    this.users.push(user);
  }
}
```
