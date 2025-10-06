# Architecture Système MyGlowSkill (MVP)

## Composants principaux

### Frontend
- **Technologie** : React.js
- **Rôle** : Interface utilisateur pour la gestion des comptes, données à surveiller et alertes
- **Communication** : Requêtes HTTP via REST API vers le backend

### Backend
- **Technologie** : Node.js avec Express
- **Rôle** : Logique métier, gestion des utilisateurs, traitement des données, authentification, gestion des alertes, traitement des abonnements
- **Communication** : API REST, gestion sécurisée des sessions / JWT

### Base de données
- **Technologie** : MongoDB (NoSQL)
- **Rôle** : Stockage sécurisé des utilisateurs, données surveillées, alertes, abonnements
- **Accès** : via ORM/ODM (Mongoose)

### Services externes
- **Exemples possibles** : fournisseur d’envoi d’email (SendGrid), fournisseurs d’authentification (Auth0 si externalisé), API externalisées pour données complémentaires (ex : monitoring, alerting)
- **Rôle** : intégrations tierces pour enrichir la plateforme

## Flux de données

1. L'utilisateur interagit avec le **Frontend React** : navigation, saisie de données, gestion de compte.
2. Le frontend envoie des requêtes REST sécurisées via JWT au **Backend Node.js/Express**.
3. Le backend valide ces requêtes, applique la logique métier, interagit avec la **base MongoDB** pour lire/écrire les données.
4. En cas d’alerte ou événement spécifique, le backend génère une notification qui peut être envoyée via un **service d’envoi d’emails** ou internalisée dans la base pour être affichée dans l’interface.
5. Le frontend reçoit les réponses et met à jour l’interface en conséquence.

## Diagramme haut niveau (textuel)
+------------+ HTTPS/REST +--------------+
| | --------------------------> | |
| Frontend | | Backend | ---+
| React.js | <-------------------------- | Node.js/Express |
+------------+ +--------------+ |
|
MongoDB (ODM)
+--------------+
| |
| Database |
+--------------+

![Diagramme d'architecture du système MyGlowSkill MVP](https://ppl-ai-code-interpreter-files.s3.amazonaws.com/web/direct-files/79731407bbd598cdf8da23bc6ef11db0/0529703c-e5b1-4cb7-ad8d-e58c3a6e8b81/059b4cc6.png)
