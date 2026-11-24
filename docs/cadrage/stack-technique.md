# Stack Technique & Outillage — Blog des Lauréats

**Projet :** Blog des Lauréats (application web et mobile de lecture d'articles)  
**Méthodologie :** Agile/Scrum et TDD

## 1. Exigences Techniques

Le projet répond aux exigences techniques suivantes :

- Chargement rapide des listes d'articles et des profils des lauréats.
- Séparation claire entre l'interface utilisateur, la logique métier et l'accès aux données.
- Protection contre les injections SQL, les attaques XSS et CSRF.
- Authentification sécurisée des auteurs et des administrateurs.
- Interface responsive adaptée aux ordinateurs, tablettes et smartphones.
- Accès mobile natif Android limité à la consultation et à la lecture des articles.

## 2. Backend

### Laravel

Laravel avec PHP est retenu pour répondre aux besoins techniques du projet :

- Son architecture MVC permet de séparer la présentation, la logique applicative et l'accès aux données.
- L'ORM Eloquent simplifie la gestion des lauréats, des articles, des catégories et des utilisateurs.
- Blade permet de créer des mises en page réutilisables pour l'interface web avec un rendu côté serveur.
- Les Middleware centralisent l'authentification et la gestion des autorisations des administrateurs et des auteurs.
- Les mécanismes de validation et de sécurité intégrés, notamment la protection CSRF, l'échappement des sorties contre les attaques XSS et les requêtes paramétrées, répondent aux exigences de sécurité de l'application.
- Laravel constitue un socle applicatif réutilisable pour l'application web et le développement mobile avec NativePHP.

### MySQL

MySQL est retenu comme système de gestion de base de données relationnelle, adapté au stockage des données structurées du projet.

- Les clés étrangères garantissent l'intégrité des relations entre les utilisateurs, les articles, les catégories et les lauréats.
- Les transactions ACID assurent la fiabilité des opérations de modification des données.
- Son intégration avec Laravel et Eloquent est mature et simple à mettre en œuvre.
- Il prend en charge aussi bien le développement local sous Windows que le déploiement en production.

## 3. Frontend

### Tailwind CSS

Tailwind CSS est retenu pour développer une interface rapide, cohérente et responsive.

- Ses classes utilitaires réduisent le besoin de créer des règles CSS personnalisées tout en assurant une présentation homogène des composants.
- Ses points de rupture responsive permettent d'adapter les interfaces aux ordinateurs, tablettes et smartphones.
- Vite permet de compiler les ressources frontend et de supprimer les styles CSS inutilisés lors de la compilation de production.

### Preline UI

Preline UI est retenu car il fournit des composants Tailwind CSS prêts à l'emploi.

- Il propose des composants tels que les cartes, les menus, les fenêtres de dialogue et les formulaires.
- Il accélère le développement des interfaces sans introduire un framework frontend complexe.
- Il est compatible avec Tailwind CSS et la structure de rendu côté serveur de Blade.

### Alpine.js

Alpine.js est retenu pour gérer les interactions légères nécessaires à l'application.

- Il permet de gérer les menus, les filtres, les fenêtres modales et les notifications.
- Il évite de mettre en place une application SPA complète lorsque les besoins ne le justifient pas.
- Il réduit la complexité JavaScript par rapport à des frameworks comme React ou Vue.js.
- Il s'intègre directement aux pages générées par Blade.

## 4. Développement Mobile

### NativePHP

NativePHP est retenu car le projet nécessite uniquement une application Android native destinée à la lecture des articles.

- Il permet de packager Laravel et PHP sous forme d'application Android sans nécessiter un serveur web distant dédié à l'exécution de l'application.
- Il permet de réutiliser les modèles, les contrôleurs, les routes, les vues Blade et les styles Tailwind CSS compatibles avec l'environnement mobile.
- Il favorise le maintien d'un socle de code commun entre le web et le mobile, au lieu de synchroniser deux applications indépendantes.
- Il limite le développement mobile supplémentaire aux fonctionnalités nécessaires à la navigation et à la lecture des articles.

| Critère | NativePHP | API + Flutter / React Native |
|---|---|---|
| Base de code | Socle Laravel commun | Deux projets distincts |
| Développement | Plus rapide pour ce périmètre | Plus long |
| Maintenance | Centralisée | Synchronisation nécessaire |
| Adaptation au projet | Adapté à la lecture des articles | Plus complexe que nécessaire pour ce besoin |

**Décision :** NativePHP est retenu pour limiter la duplication du code et simplifier la maintenance d'une application mobile dont le périmètre fonctionnel est principalement orienté vers la consultation des articles.

## 5. Qualité et Outillage IA

### Tests Automatisés

Les tests automatisés sont retenus conformément à la méthodologie TDD et afin de prévenir les régressions.

- PHPUnit ou Pest permet de mettre en œuvre le cycle Red-Green-Refactor dans l'écosystème Laravel.
- Les tests unitaires et fonctionnels vérifient la création, l'affichage et le filtrage des articles ainsi que les règles d'accès.
- Les tests permettent de vérifier le comportement des fonctionnalités à chaque incrément de développement.
- Ils sont exécutés avant l'intégration des modifications et le déploiement.

### Assistance par l'IA

#### GitHub Copilot

GitHub Copilot est retenu comme assistant de développement grâce à son intégration dans l'environnement de programmation et à sa compatibilité avec les principales technologies du projet.

- Il assiste dans l'écriture du code PHP et Laravel.
- Il facilite la création des migrations, des factories, des règles de validation et des tests.
- Il réduit les tâches répétitives et la rédaction de code standard.
- Le développeur reste responsable de la vérification et de la validation de chaque proposition.

#### Antigravity

Antigravity est retenu pour faciliter la coordination des tâches impliquant plusieurs fichiers du projet.

- Il aide à générer et organiser la documentation technique.
- Il facilite la cohérence entre les modèles, les contrôleurs, les vues, les routes et les tests.
- Il assiste dans l'exécution des tâches répétitives depuis le terminal.
- Il permet de vérifier l'avancement du développement par rapport aux spécifications du projet.

**Décision :** GitHub Copilot et Antigravity sont utilisés comme outils complémentaires d'assistance. Le développeur conserve le contrôle des modifications, des tests et de la validation finale du code.