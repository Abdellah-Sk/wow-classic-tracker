# 🗺️ ROADMAP - Devenir Dev Web avec WoW Classic Tracker

## 🎯 Objectif Final
Créer une application web complète de tracking personnel WoW Classic et maîtriser toutes les compétences pour devenir développeur web junior employable.

**Durée estimée** : 6-9 mois (à raison d'1h/jour minimum)

---

# PHASE 1 : FONDATIONS WEB (Semaines 1-12)

## MODULE 1.1 - HTML : Structure et Sémantique (Semaine 1)

### Objectif
Comprendre la structure HTML et créer les premières pages du tracker.

### Compétences à acquérir
- Balises HTML de base (div, p, h1-h6, a, img)
- Structure sémantique (header, nav, main, section, article, footer)
- Formulaires (input, select, textarea, button)
- Listes (ul, ol, li)
- Tableaux (table, tr, td, th)

### Exercice pratique
**Jour 1-2** : Créer `index.html` - Page d'accueil du tracker
- Header avec titre "WoW Classic Tracker"
- Navigation (Mes Personnages, Objectifs, Calculateurs)
- Section hero avec description

**Jour 3-4** : Créer `characters.html` - Liste des personnages
- Tableau avec colonnes : Nom, Classe, Niveau, Serveur, Faction
- Formulaire d'ajout de personnage (tous les champs ci-dessus)

**Jour 5-7** : Créer `character-detail.html` - Détail d'un personnage
- Informations complètes
- Sections : Stuff, Objectifs, Montures, Réputations
- Listes à puces pour chaque section

### Validation (tu sais que c'est acquis quand...)
- ✅ Tu as 3 pages HTML bien structurées
- ✅ Ton code est indenté et lisible
- ✅ Tu utilises les bonnes balises sémantiques
- ✅ Tes formulaires ont tous les attributs nécessaires (name, type, placeholder)

### Feature débloquée
🎮 **v0.1** - Structure HTML du tracker visible dans le navigateur

---

## MODULE 1.2 - CSS : Mise en page et Design (Semaines 2-3)

### Objectif
Styliser le tracker et le rendre visuellement attractif et responsive.

### Compétences à acquérir
- Sélecteurs CSS (class, id, élément, pseudo-classes)
- Box model (margin, padding, border)
- Typography et couleurs
- Flexbox pour layouts
- CSS Grid pour grilles
- Media queries (responsive)
- Positionnement (relative, absolute, fixed, sticky)

### Exercice pratique
**Semaine 2 - Jours 1-3** : Style global et navigation
- Créer `styles.css`
- Palette de couleurs WoW (bleu/or pour Alliance, rouge/noir pour Horde)
- Header fixe avec navigation horizontale
- Typographie claire et lisible

**Semaine 2 - Jours 4-7** : Layout des pages
- Page personnages : Grid pour afficher les cartes de personnages
- Formulaire stylisé avec focus states
- Tableau responsive

**Semaine 3 - Jours 1-4** : Composants réutilisables
- Cartes de personnages (avec hover effects)
- Boutons stylisés (primary, secondary, danger)
- Badges pour classes WoW (couleurs par classe)

**Semaine 3 - Jours 5-7** : Responsive design
- Mobile first approach
- Breakpoints : mobile (< 768px), tablet (768-1024px), desktop (> 1024px)
- Navigation burger sur mobile
- Grid adaptatif

### Validation
- ✅ Ton site est beau et cohérent visuellement
- ✅ Responsive sur mobile, tablet, desktop
- ✅ Tu comprends Flexbox ET Grid
- ✅ Tu as créé des classes réutilisables

### Feature débloquée
🎮 **v0.2** - Interface stylée et responsive

---

## MODULE 1.3 - JavaScript Fondamentaux (Semaine 4)

### Objectif
Ajouter de l'interactivité de base et manipuler le DOM.

### Compétences à acquérir
- Variables (let, const)
- Types de données (string, number, boolean, array, object)
- Fonctions (déclaration, arrow functions)
- Conditions (if/else, switch)
- Boucles (for, forEach, map, filter)
- Manipulation du DOM (querySelector, createElement, addEventListener)
- Events (click, submit, input)

### Exercice pratique
**Jour 1-2** : Bases JavaScript
- Créer `app.js`
- Variables pour stocker des personnages (array d'objets)
- Fonctions pour calculer le level total, compter par classe

**Jour 3-4** : Manipulation DOM
- Afficher dynamiquement les personnages depuis l'array
- Fonction pour créer une carte de personnage
- Boucle pour générer toutes les cartes

**Jour 5-6** : Interactivité
- Formulaire d'ajout : récupérer les données au submit
- Ajouter un personnage à l'array
- Rafraîchir l'affichage
- Bouton "Supprimer" sur chaque carte

**Jour 7** : Filtres et recherche
- Input de recherche (filtrer par nom)
- Filtres par classe (buttons ou select)
- Tri par niveau, nom

### Validation
- ✅ Tes personnages s'affichent dynamiquement
- ✅ Tu peux ajouter/supprimer des personnages
- ✅ Les filtres fonctionnent
- ✅ Tu comprends le concept de DOM

### Feature débloquée
🎮 **v0.3** - Gestion dynamique des personnages (non persistante)

---

## MODULE 1.4 - JavaScript Intermédiaire (Semaine 5)

### Objectif
Gérer les données complexes et persister l'information.

### Compétences à acquérir
- LocalStorage (get, set, remove, clear)
- JSON (parse, stringify)
- Destructuring
- Spread operator
- Template literals
- Modules (import/export)

### Exercice pratique
**Jour 1-2** : LocalStorage
- Sauvegarder les personnages dans localStorage
- Charger les données au démarrage
- Créer des fonctions : saveData(), loadData()

**Jour 3-4** : Structure de données
- Créer un modèle de données complet pour un personnage
```javascript
{
  id: "uuid",
  name: "Legolas",
  class: "Hunter",
  race: "Night Elf",
  level: 60,
  server: "Sulfuron",
  faction: "Alliance",
  professions: ["Engineering", "Mining"],
  objectives: [],
  mounts: [],
  reputations: []
}
```
- Fonction pour générer des IDs uniques

**Jour 5-6** : Page détail personnage
- Router basique (afficher/cacher sections)
- Afficher tous les détails d'un personnage
- Ajouter/modifier des objectifs
- Tracker de réputation avec barres de progression

**Jour 7** : Refactoring
- Organiser le code en modules
- Créer des fichiers séparés (characters.js, storage.js, ui.js)

### Validation
- ✅ Les données persistent après rafraîchissement
- ✅ Tu as une structure de données propre
- ✅ Code organisé en modules
- ✅ Page détail fonctionnelle

### Feature débloquée
🎮 **v0.4** - Données persistantes + Page détail complète

---

## MODULE 1.5 - JavaScript Avancé et Asynchrone (Semaine 6)

### Objectif
Gérer les opérations asynchrones et intégrer des données externes.

### Compétences à acquérir
- Promises
- Async/await
- Fetch API
- Gestion d'erreurs (try/catch)
- API REST (GET, POST)

### Exercice pratique
**Jour 1-2** : Comprendre l'asynchrone
- Simuler des délais (setTimeout)
- Promises basiques
- Chaîner des promises

**Jour 3-5** : Intégration API
- Utiliser une API WoW (ou créer des données mockées)
- Fetch des informations d'objets/items
- Afficher les icônes et stats d'items
- Loading states (spinners)

**Jour 6-7** : Calculateurs
- Calculateur de DPS
- Calculateur de stats (Int → Mana, Agi → Crit)
- Calculateur de gold farming (gold/heure)
- Graphs basiques (avec Chart.js ou canvas)

### Validation
- ✅ Tu comprends async/await
- ✅ Tu gères les erreurs API proprement
- ✅ Loading states implémentés
- ✅ Calculateurs fonctionnels

### Feature débloquée
🎮 **v0.5** - Calculateurs + intégration données externes

---

## MODULE 1.6 - Git & Déploiement (Semaine 7)

### Objectif
Versionner ton code et déployer en ligne.

### Compétences à acquérir
- Git basics (init, add, commit, push)
- Branches (create, merge)
- GitHub (repository, README)
- Déploiement (Netlify ou Vercel)
- Nom de domaine (optionnel)

### Exercice pratique
**Jour 1-2** : Git local
- Initialiser un repo
- Premiers commits
- Créer un .gitignore
- Écrire des messages de commit clairs

**Jour 3-4** : GitHub
- Créer un repo distant
- Push du code
- Écrire un README.md complet
- Créer des branches (dev, feature)

**Jour 5-7** : Déploiement
- Déployer sur Netlify
- Configuration du build
- Tester en production
- Partager ton site !

### Validation
- ✅ Code sur GitHub
- ✅ Commits réguliers et clairs
- ✅ Site déployé et accessible
- ✅ README documenté

### Feature débloquée
🎮 **v0.6** - Site en ligne et versionné ! 🚀

---

## MODULE 1.7 - Projet Vanilla - Finalisation (Semaine 8)

### Objectif
Peaufiner, optimiser et documenter ton projet vanilla.

### Compétences à acquérir
- Debugging (console, breakpoints)
- Performance (optimisation JS/CSS)
- Accessibilité (a11y)
- SEO basique
- Documentation

### Exercice pratique
**Jour 1-2** : Polish UI/UX
- Animations CSS (transitions, keyframes)
- Feedback utilisateur (toasts, confirmations)
- États vides (pas de personnage encore)
- Messages d'erreur clairs

**Jour 3-4** : Accessibilité
- ARIA labels
- Navigation au clavier
- Contraste des couleurs
- Alt sur images

**Jour 5-6** : Optimisation
- Minifier CSS/JS
- Lazy loading des images
- Optimiser les performances

**Jour 7** : Documentation
- Commenter le code
- Guide utilisateur
- Changelog

### Validation
- ✅ Application polie et professionnelle
- ✅ Accessible
- ✅ Performante
- ✅ Bien documentée

### Feature débloquée
🎮 **v1.0** - Version vanilla complète et professionnelle ! 🎉

---

# PHASE 2 : FRAMEWORKS MODERNES (Semaines 9-20)

## MODULE 2.1 - Introduction à React (Semaines 9-10)

### Objectif
Comprendre React et refaire ton tracker avec des composants.

### Compétences à acquérir
- JSX
- Composants (fonctionnels)
- Props
- State (useState)
- Événements en React
- Listes et keys
- Conditional rendering
- Formulaires contrôlés

### Exercice pratique
**Semaine 9** : Setup et bases
- Create React App ou Vite
- Créer les composants de base : Header, CharacterCard, CharacterList
- Passer des props
- State pour la liste de personnages

**Semaine 10** : Recréer les features
- Formulaire d'ajout en React
- Suppression de personnages
- Filtres et recherche
- Composants réutilisables (Button, Input, Badge)

### Validation
- ✅ Application fonctionnelle en React
- ✅ Tu comprends props vs state
- ✅ Composants bien découpés
- ✅ Code plus propre qu'en vanilla

### Feature débloquée
🎮 **v2.0** - Application React fonctionnelle

---

## MODULE 2.2 - React Intermédiaire (Semaines 11-12)

### Objectif
Maîtriser les hooks et la gestion d'état avancée.

### Compétences à acquérir
- useEffect (lifecycle)
- useContext (state global)
- useReducer (state complexe)
- Custom hooks
- React Router (navigation)

### Exercice pratique
**Semaine 11** : Hooks avancés
- useEffect pour localStorage
- Context pour partager les personnages
- Custom hook useLocalStorage
- Custom hook useCharacters

**Semaine 12** : Routing
- React Router setup
- Routes : /, /characters, /characters/:id, /calculators
- Navigation
- 404 page

### Validation
- ✅ Données persistent avec useEffect
- ✅ Context utilisé correctement
- ✅ Custom hooks réutilisables
- ✅ Routing fonctionnel

### Feature débloquée
🎮 **v2.1** - React avec routing et state management

---

## MODULE 2.3 - Styling Moderne : Tailwind CSS (Semaine 13)

### Objectif
Intégrer Tailwind et accélérer le développement UI.

### Compétences à acquérir
- Installation Tailwind
- Utility classes
- Responsive design avec Tailwind
- Configuration (couleurs, fonts)
- Composition de classes

### Exercice pratique
**Jour 1-2** : Setup et migration
- Installer Tailwind
- Migrer quelques composants
- Comprendre la philosophie utility-first

**Jour 3-7** : Refonte complète
- Tous les composants en Tailwind
- Thème WoW (couleurs custom)
- Responsive avec breakpoints Tailwind
- Dark mode (optionnel)

### Validation
- ✅ Plus de CSS custom (ou très peu)
- ✅ Design cohérent avec Tailwind
- ✅ Responsive fluide
- ✅ Tu comprends l'approche utility-first

### Feature débloquée
🎮 **v2.2** - UI moderne avec Tailwind

---

## MODULE 2.4 - Shadcn/ui : Composants Pro (Semaine 14)

### Objectif
Utiliser des composants UI professionnels et accessibles.

### Compétences à acquérir
- Installation Shadcn
- Composants : Button, Input, Select, Dialog, Dropdown, Table, Card
- Accessibilité intégrée
- Customisation de composants

### Exercice pratique
**Jour 1-3** : Intégration Shadcn
- Setup Shadcn
- Remplacer les composants basiques (Button, Input)
- Dialog pour ajout de personnage
- Dropdown menus

**Jour 4-7** : Composants avancés
- Table pour liste de personnages
- Tabs pour sections (Stuff, Objectifs, etc.)
- Accordion pour détails
- Toast notifications

### Validation
- ✅ Interface professionnelle
- ✅ Composants accessibles
- ✅ Interactions fluides
- ✅ Code maintenable

### Feature débloquée
🎮 **v2.3** - UI professionnelle avec Shadcn

---

## MODULE 2.5 - Next.js : Framework Full-Stack (Semaines 15-16)

### Objectif
Migrer vers Next.js et comprendre le rendering côté serveur.

### Compétences à acquérir
- App Router (Next.js 13+)
- Server Components vs Client Components
- Layouts et templates
- Loading et error states
- Metadata et SEO
- Route handlers (API routes)

### Exercice pratique
**Semaine 15** : Migration et structure
- Créer projet Next.js
- Migrer les composants React
- Structure app/ avec layouts
- Server components par défaut

**Semaine 16** : Features Next.js
- Loading.tsx pour états de chargement
- Error.tsx pour gestion d'erreurs
- Metadata pour SEO
- API routes basiques

### Validation
- ✅ Application Next.js fonctionnelle
- ✅ Tu comprends SSR vs CSR
- ✅ Structure propre avec App Router
- ✅ SEO optimisé

### Feature débloquée
🎮 **v3.0** - Application Next.js full-stack

---

## MODULE 2.6 - Backend : Node.js + Express (Semaines 17-18)

### Objectif
Créer une vraie API REST pour ton tracker.

### Compétences à acquérir
- Node.js basics
- Express.js (routes, middleware)
- REST API (GET, POST, PUT, DELETE)
- Validation de données
- Error handling
- CORS

### Exercice pratique
**Semaine 17** : API Setup
- Créer serveur Express
- Routes pour personnages (CRUD complet)
- Middleware (logging, errors)
- Validation avec Zod

**Semaine 18** : Intégration
- Connecter Next.js à l'API
- Remplacer localStorage par API calls
- Gestion des erreurs réseau
- Loading states

### Validation
- ✅ API REST fonctionnelle
- ✅ CRUD complet via API
- ✅ Validation des données
- ✅ Gestion d'erreurs propre

### Feature débloquée
🎮 **v3.1** - API backend fonctionnelle

---

## MODULE 2.7 - Base de Données : PostgreSQL (Semaines 19-20)

### Objectif
Persister les données dans une vraie base de données.

### Compétences à acquérir
- SQL basics (SELECT, INSERT, UPDATE, DELETE)
- PostgreSQL
- Prisma ORM
- Relations (one-to-many, many-to-many)
- Migrations
- Seeds

### Exercice pratique
**Semaine 19** : Setup BDD
- Installer PostgreSQL (local ou Supabase)
- Prisma setup
- Schéma de base de données (User, Character, Objective, etc.)
- Migrations initiales

**Semaine 20** : Intégration
- Remplacer le stockage temporaire par Prisma
- Requêtes complexes (avec relations)
- Seeds pour données de test
- Queries optimisées

### Validation
- ✅ BDD PostgreSQL opérationnelle
- ✅ Données persistantes en DB
- ✅ Relations fonctionnelles
- ✅ Tu comprends SQL et ORMs

### Feature débloquée
🎮 **v3.2** - Base de données complète

---

# PHASE 3 : PROFESSIONNALISATION (Semaines 21-28)

## MODULE 3.1 - Authentification (Semaines 21-22)

### Objectif
Sécuriser l'application avec un système d'authentification.

### Compétences à acquérir
- NextAuth.js (ou Clerk)
- Sessions et tokens
- Protected routes
- Rôles et permissions
- OAuth (Google, Discord)

### Exercice pratique
**Semaine 21** : Auth setup
- NextAuth.js configuration
- Pages login/register
- Provider (credentials + OAuth)
- Sessions

**Semaine 22** : Protection
- Middleware pour routes protégées
- Associer personnages aux users
- Dashboard personnel
- Multi-utilisateurs

### Validation
- ✅ Login/Register fonctionnel
- ✅ Routes protégées
- ✅ Sessions gérées
- ✅ Chaque user voit ses données

### Feature débloquée
🎮 **v4.0** - Application multi-utilisateurs sécurisée

---

## MODULE 3.2 - Tests (Semaines 23-24)

### Objectif
Tester ton code pour éviter les régressions.

### Compétences à acquérir
- Jest (tests unitaires)
- React Testing Library
- Tests de composants
- Tests d'intégration
- Test coverage
- TDD (optionnel)

### Exercice pratique
**Semaine 23** : Tests unitaires
- Setup Jest
- Tester les fonctions utilitaires
- Tester les hooks custom
- Mocks et stubs

**Semaine 24** : Tests composants
- Testing Library setup
- Tester les composants UI
- Tests d'interaction utilisateur
- Tests d'intégration simples

### Validation
- ✅ Coverage > 70%
- ✅ Tests passent en CI
- ✅ Tu comprends l'intérêt des tests
- ✅ Tests maintenables

### Feature débloquée
🎮 **v4.1** - Application testée et robuste

---

## MODULE 3.3 - Performance & Optimisation (Semaine 25)

### Objectif
Optimiser l'application pour de meilleures performances.

### Compétences à acquérir
- Code splitting
- Lazy loading
- Memoization (useMemo, useCallback)
- Image optimization
- Bundle analysis
- Lighthouse audit

### Exercice pratique
**Jour 1-2** : Audit
- Lighthouse report
- Identifier les bottlenecks
- Bundle analyzer

**Jour 3-5** : Optimisations
- Next/Image pour images
- Dynamic imports
- Memoization des calculs
- Virtualization pour longues listes

**Jour 6-7** : Vérification
- Nouveau Lighthouse audit
- Amélioration des scores
- Documentation des optimisations

### Validation
- ✅ Lighthouse score > 90
- ✅ Bundle size optimisé
- ✅ Temps de chargement < 2s
- ✅ Smooth UX

### Feature débloquée
🎮 **v4.2** - Application ultra-performante

---

## MODULE 3.4 - CI/CD & DevOps (Semaine 26)

### Objectif
Automatiser le déploiement et la qualité du code.

### Compétences à acquérir
- GitHub Actions
- CI pipeline (tests, lint)
- CD pipeline (deploy auto)
- Environments (dev, staging, prod)
- Monitoring basique

### Exercice pratique
**Jour 1-3** : CI
- GitHub Actions workflow
- Run tests auto
- Linting auto
- Build verification

**Jour 4-7** : CD
- Auto deploy sur Vercel
- Preview deployments
- Environment variables
- Rollback strategy

### Validation
- ✅ CI/CD fonctionnel
- ✅ Deploy automatique
- ✅ Tests en CI
- ✅ Preview branches

### Feature débloquée
🎮 **v4.3** - Pipeline de déploiement automatisé

---

## MODULE 3.5 - Features Avancées (Semaines 27-28)

### Objectif
Ajouter des features qui font la différence.

### Compétences à acquérir
- WebSockets (temps réel)
- File upload (images)
- Emails (notifications)
- Cron jobs (tâches planifiées)
- Analytics

### Exercice pratique
**Semaine 27** : Features premium
- Upload d'avatar de personnage
- Notifications par email (objectifs complétés)
- Partage de build (URL publique)
- Export de données (JSON/CSV)

**Semaine 28** : Polish final
- Analytics (Vercel Analytics ou Plausible)
- Page de statistiques globales
- Easter eggs WoW
- Documentation utilisateur complète

### Validation
- ✅ Features avancées fonctionnelles
- ✅ Application "production-ready"
- ✅ Analytics en place
- ✅ Docs complètes

### Feature débloquée
🎮 **v5.0** - Application complète et professionnelle ! 🎉🎉🎉

---

# PHASE 4 : EMPLOYABILITÉ (Semaines 29-32)

## MODULE 4.1 - Portfolio & CV (Semaine 29)

### Objectif
Présenter ton travail de manière professionnelle.

### Actions
- Créer un portfolio site (avec Next.js)
- Mettre en avant le WoW Tracker
- Case study du projet (défis, solutions)
- CV tech moderne
- LinkedIn optimisé

---

## MODULE 4.2 - Préparation Entretiens (Semaine 30)

### Objectif
Se préparer aux entretiens techniques.

### Actions
- Réviser les concepts clés
- LeetCode/CodeWars (algo de base)
- Questions d'entretien React/Next
- Mock interviews
- Présentation du projet (pitch 5min)

---

## MODULE 4.3 - Contribution Open Source (Semaine 31)

### Objectif
Montrer ta capacité à collaborer.

### Actions
- Choisir un projet open source
- Faire ta première PR
- Code review
- Documentation de projet

---

## MODULE 4.4 - Candidatures (Semaine 32+)

### Objectif
Décrocher ton premier poste de dev.

### Actions
- Identifier 20 entreprises cibles
- Personnaliser CV/lettre
- Postuler (5-10 par semaine)
- Networking (meetups, Twitter/X)
- Continuer à coder !

---

# 📊 COMPÉTENCES FINALES ACQUISES

## Frontend
- ✅ HTML5 sémantique
- ✅ CSS3 avancé (Flexbox, Grid, animations)
- ✅ JavaScript ES6+ (async, modules, etc.)
- ✅ React (hooks, context, routing)
- ✅ Next.js (App Router, SSR)
- ✅ Tailwind CSS
- ✅ Shadcn/ui

## Backend
- ✅ Node.js
- ✅ Express.js (API REST)
- ✅ PostgreSQL
- ✅ Prisma ORM
- ✅ NextAuth.js

## DevOps & Outils
- ✅ Git/GitHub
- ✅ CI/CD (GitHub Actions)
- ✅ Déploiement (Vercel)
- ✅ Testing (Jest, RTL)

## Soft Skills
- ✅ Documentation
- ✅ Code review
- ✅ Debugging
- ✅ Problem solving
- ✅ Autonomie

---

# 🎯 PROCHAINES ÉTAPES

Après cette roadmap, tu peux :
1. **Spécialiser** : Backend (NestJS, GraphQL), Frontend (animations avancées), DevOps
2. **Élargir** : TypeScript avancé, Mobile (React Native), Desktop (Electron)
3. **Approfondir** : Architecture, Design Patterns, Microservices

---

**Tu es maintenant prêt à devenir un dev de ouf ! 🚀**

*Dernière mise à jour : Février 2026*
