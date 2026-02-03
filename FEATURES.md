# 🎮 FEATURES - WoW Classic Tracker

## 📋 Vue d'ensemble

Ce document décrit toutes les fonctionnalités du WoW Classic Tracker, organisées par phase de développement.

---

## 🌱 PHASE 1 : VANILLA (v0.1 → v1.0)

### v0.1 - Structure HTML de base
**Fonctionnalités** :
- ✅ Page d'accueil avec header, nav, hero section
- ✅ Page liste des personnages (tableau statique)
- ✅ Page détail d'un personnage (sections : stuff, objectifs, montures, réputations)

**Pages** :
- `index.html` - Accueil
- `characters.html` - Liste personnages
- `character-detail.html` - Détail personnage

---

### v0.2 - Interface stylée
**Fonctionnalités** :
- ✅ Design cohérent avec palette WoW (bleu/or Alliance, rouge/noir Horde)
- ✅ Header fixe avec navigation
- ✅ Cartes de personnages stylisées
- ✅ Formulaires propres
- ✅ Responsive mobile/tablet/desktop
- ✅ Badges de classe colorés

**Éléments visuels** :
- Navigation horizontale (desktop) / burger (mobile)
- Cards avec hover effects
- Boutons (primary, secondary, danger)
- Inputs stylisés
- Tableaux responsive

---

### v0.3 - Gestion dynamique
**Fonctionnalités** :
- ✅ Affichage dynamique des personnages depuis JavaScript
- ✅ Ajout de personnage via formulaire
- ✅ Suppression de personnage
- ✅ Recherche par nom
- ✅ Filtres par classe
- ✅ Tri (nom, niveau)

**Données gérées** :
```javascript
{
  name: string,
  class: string,
  level: number,
  server: string,
  faction: "Alliance" | "Horde"
}
```

**Limitations** :
- ⚠️ Données non persistantes (disparaissent au refresh)

---

### v0.4 - Persistence et détails
**Fonctionnalités** :
- ✅ Sauvegarde dans localStorage
- ✅ Chargement au démarrage
- ✅ Modèle de données complet
- ✅ Page détail fonctionnelle
- ✅ Gestion des objectifs
- ✅ Tracker de réputation avec barres de progression
- ✅ Code organisé en modules

**Modèle de données complet** :
```javascript
{
  id: string (uuid),
  name: string,
  class: "Warrior" | "Mage" | "Rogue" | "Priest" | "Hunter" | "Warlock" | "Druid" | "Shaman" | "Paladin",
  race: string,
  level: number (1-60),
  server: string,
  faction: "Alliance" | "Horde",
  professions: [string, string],
  objectives: [
    {
      id: string,
      title: string,
      description: string,
      completed: boolean,
      type: "quest" | "item" | "reputation" | "achievement"
    }
  ],
  mounts: [
    {
      name: string,
      obtained: boolean
    }
  ],
  reputations: [
    {
      faction: string,
      standing: "Hated" | "Hostile" | "Unfriendly" | "Neutral" | "Friendly" | "Honored" | "Revered" | "Exalted",
      progress: number (0-100)
    }
  ]
}
```

**Fonctionnalités détail personnage** :
- Vue complète des infos
- Ajout/suppression d'objectifs
- Checkbox pour objectifs complétés
- Barres de progression réputation
- Liste des montures

---

### v0.5 - Calculateurs et API
**Fonctionnalités** :
- ✅ Intégration d'API externe (ou données mockées)
- ✅ Affichage d'icônes d'items
- ✅ Loading states (spinners)
- ✅ Calculateur de DPS
- ✅ Calculateur de stats (Int → Mana, Agi → Crit)
- ✅ Calculateur de gold farming (gold/heure)
- ✅ Graphiques basiques (Chart.js)

**Calculateurs disponibles** :

**1. Calculateur de DPS**
- Input : arme, stats (force/agilité)
- Output : DPS estimé

**2. Calculateur de stats**
- Int → Mana
- Agi → % Crit
- Stam → HP
- Spirit → Regen

**3. Calculateur de gold farming**
- Input : activité (farming spot), temps
- Output : gold/heure, estimation total

**Graphiques** :
- Évolution du level par personnage
- Répartition des classes
- Progression des réputations

---

### v0.6 - Déploiement
**Fonctionnalités** :
- ✅ Code versionné sur GitHub
- ✅ Site déployé sur Netlify/Vercel
- ✅ README complet
- ✅ Branches (main, dev)

**URLs** :
- Repo GitHub : `https://github.com/[username]/wow-classic-tracker`
- Site en ligne : `https://wow-tracker.netlify.app`

---

### v1.0 - Version finale Vanilla
**Fonctionnalités** :
- ✅ Animations CSS (transitions, keyframes)
- ✅ Feedback utilisateur (toasts, confirmations)
- ✅ États vides ("Aucun personnage pour le moment")
- ✅ Messages d'erreur clairs
- ✅ Accessibilité (ARIA, clavier, contraste)
- ✅ Performance optimisée
- ✅ Documentation complète

**Polish UX** :
- Toasts pour succès/erreur
- Confirmations avant suppression
- Placeholder quand aucune donnée
- Animations smooth
- Focus states
- Alt text sur images

**Accessibilité** :
- Navigation au clavier
- Screen reader friendly
- Contraste WCAG AA
- Focus visible

---

## ⚛️ PHASE 2 : FRAMEWORKS MODERNES (v2.0 → v3.2)

### v2.0 - React
**Fonctionnalités** :
- ✅ Application refaite en React
- ✅ Composants réutilisables
- ✅ State management avec useState
- ✅ Formulaires contrôlés
- ✅ Toutes les features de v1.0 recréées en React

**Architecture composants** :
```
App
├── Header
├── Navigation
├── CharacterList
│   ├── CharacterCard
│   └── CharacterFilters
├── CharacterForm
└── CharacterDetail
    ├── ObjectivesList
    ├── ReputationTracker
    └── MountsList
```

**Composants réutilisables** :
- `<Button variant="primary|secondary|danger" />`
- `<Input type="text|number|select" />`
- `<Badge color="warrior|mage|..." />`
- `<Card />`

---

### v2.1 - React + Routing
**Fonctionnalités** :
- ✅ React Router intégré
- ✅ Navigation entre pages
- ✅ URLs dynamiques `/characters/:id`
- ✅ useContext pour state global
- ✅ Custom hooks (useLocalStorage, useCharacters)
- ✅ 404 page

**Routes** :
- `/` - Accueil
- `/characters` - Liste
- `/characters/:id` - Détail
- `/calculators` - Calculateurs
- `/calculators/dps` - Calculateur DPS
- `/calculators/stats` - Calculateur Stats
- `/calculators/gold` - Calculateur Gold
- `*` - 404

**Custom Hooks** :
```javascript
useLocalStorage(key, defaultValue)
useCharacters()
useReputation()
useCalculator()
```

---

### v2.2 - Tailwind CSS
**Fonctionnalités** :
- ✅ Design system avec Tailwind
- ✅ Thème personnalisé WoW
- ✅ Responsive avec utilities
- ✅ Plus de CSS custom
- ✅ Dark mode (optionnel)

**Thème custom** :
```javascript
// tailwind.config.js
colors: {
  alliance: {
    light: '#4A90E2',
    DEFAULT: '#1E5A9E',
    dark: '#0D3A6B'
  },
  horde: {
    light: '#E74C3C',
    DEFAULT: '#C0392B',
    dark: '#7D1F1A'
  },
  // Classes WoW
  warrior: '#C79C6E',
  mage: '#69CCF0',
  // ...
}
```

---

### v2.3 - Shadcn/ui
**Fonctionnalités** :
- ✅ Composants UI professionnels
- ✅ Accessibilité native
- ✅ Dialogs pour ajout/édition
- ✅ Dropdowns menus
- ✅ Tables avancées
- ✅ Tabs pour sections
- ✅ Toast notifications

**Composants Shadcn utilisés** :
- Button
- Input, Select, Textarea
- Dialog (modals)
- DropdownMenu
- Table (sortable, filtrable)
- Tabs
- Accordion
- Toast
- Card

---

### v3.0 - Next.js
**Fonctionnalités** :
- ✅ Migration vers Next.js App Router
- ✅ Server Components
- ✅ Loading states automatiques
- ✅ Error boundaries
- ✅ Metadata et SEO
- ✅ API Routes basiques

**Structure App Router** :
```
app/
├── layout.tsx (global)
├── page.tsx (accueil)
├── characters/
│   ├── layout.tsx
│   ├── page.tsx (liste)
│   ├── loading.tsx
│   ├── error.tsx
│   └── [id]/
│       ├── page.tsx (détail)
│       └── loading.tsx
├── calculators/
│   └── ...
└── api/
    └── characters/
        └── route.ts
```

**SEO** :
- Metadata par page
- Open Graph tags
- Sitemap
- Robots.txt

---

### v3.1 - API Backend
**Fonctionnalités** :
- ✅ API REST complète avec Express
- ✅ CRUD personnages
- ✅ Validation avec Zod
- ✅ Error handling
- ✅ CORS configuré
- ✅ Next.js connecté à l'API

**Endpoints API** :
```
GET    /api/characters          - Liste
GET    /api/characters/:id      - Détail
POST   /api/characters          - Créer
PUT    /api/characters/:id      - Modifier
DELETE /api/characters/:id      - Supprimer

GET    /api/characters/:id/objectives
POST   /api/characters/:id/objectives
DELETE /api/characters/:id/objectives/:objectiveId

GET    /api/characters/:id/reputations
PUT    /api/characters/:id/reputations/:reputationId
```

**Validation Zod** :
```typescript
const characterSchema = z.object({
  name: z.string().min(2).max(12),
  class: z.enum(['Warrior', 'Mage', ...]),
  level: z.number().min(1).max(60),
  // ...
})
```

---

### v3.2 - Base de données
**Fonctionnalités** :
- ✅ PostgreSQL avec Prisma
- ✅ Schéma de données complet
- ✅ Relations entre tables
- ✅ Migrations
- ✅ Seeds de données
- ✅ Queries optimisées

**Schéma Prisma** :
```prisma
model User {
  id         String      @id @default(uuid())
  email      String      @unique
  name       String
  characters Character[]
  createdAt  DateTime    @default(now())
}

model Character {
  id          String       @id @default(uuid())
  name        String
  class       String
  race        String
  level       Int
  server      String
  faction     String
  professions String[]
  userId      String
  user        User         @relation(fields: [userId], references: [id])
  objectives  Objective[]
  mounts      Mount[]
  reputations Reputation[]
  createdAt   DateTime     @default(now())
  updatedAt   DateTime     @updatedAt
}

model Objective {
  id           String    @id @default(uuid())
  title        String
  description  String?
  completed    Boolean   @default(false)
  type         String
  characterId  String
  character    Character @relation(fields: [characterId], references: [id], onDelete: Cascade)
  createdAt    DateTime  @default(now())
}

model Mount {
  id          String    @id @default(uuid())
  name        String
  obtained    Boolean   @default(false)
  characterId String
  character   Character @relation(fields: [characterId], references: [id], onDelete: Cascade)
}

model Reputation {
  id          String    @id @default(uuid())
  faction     String
  standing    String
  progress    Int       @default(0)
  characterId String
  character   Character @relation(fields: [characterId], references: [id], onDelete: Cascade)
}
```

---

## 💼 PHASE 3 : PROFESSIONNALISATION (v4.0 → v5.0)

### v4.0 - Authentification
**Fonctionnalités** :
- ✅ NextAuth.js intégré
- ✅ Login/Register
- ✅ OAuth (Google, Discord)
- ✅ Sessions sécurisées
- ✅ Routes protégées
- ✅ Multi-utilisateurs
- ✅ Dashboard personnel

**Pages auth** :
- `/login` - Connexion
- `/register` - Inscription
- `/profile` - Profil utilisateur

**Features utilisateur** :
- Chaque user voit uniquement ses personnages
- Profil éditable (nom, avatar, email)
- Statistiques personnelles
- Préférences (thème, faction préférée)

**Providers OAuth** :
- Google
- Discord
- Battle.net (optionnel)

---

### v4.1 - Tests
**Fonctionnalités** :
- ✅ Tests unitaires (Jest)
- ✅ Tests composants (React Testing Library)
- ✅ Tests d'intégration
- ✅ Coverage > 70%
- ✅ CI avec tests automatiques

**Tests couverts** :

**Unitaires** :
- Fonctions utils (calculs, formatage)
- Custom hooks
- Validators Zod

**Composants** :
- CharacterCard rendering
- CharacterForm submission
- Filters fonctionnels
- Navigation

**Intégration** :
- Flow complet : ajout personnage → affichage → suppression
- Login → accès dashboard → logout
- Ajout objectif → mise à jour → completion

---

### v4.2 - Performance
**Fonctionnalités** :
- ✅ Code splitting
- ✅ Lazy loading
- ✅ Image optimization (Next/Image)
- ✅ Memoization (useMemo, useCallback)
- ✅ Virtual scrolling (longues listes)
- ✅ Bundle size optimisé
- ✅ Lighthouse score > 90

**Optimisations** :
- Dynamic imports pour routes
- Skeleton loaders
- Prefetching links
- Cache API responses
- Compression images
- Fonts optimisés

**Métriques cibles** :
- First Contentful Paint < 1.5s
- Time to Interactive < 3s
- Lighthouse Performance > 90
- Lighthouse Accessibility > 95
- Lighthouse Best Practices > 90
- Lighthouse SEO > 90

---

### v4.3 - CI/CD
**Fonctionnalités** :
- ✅ GitHub Actions
- ✅ Tests auto sur PR
- ✅ Lint auto
- ✅ Build verification
- ✅ Deploy auto sur Vercel
- ✅ Preview deployments
- ✅ Environments (dev, staging, prod)

**Pipelines** :

**CI (Continuous Integration)** :
```yaml
on: [pull_request]
- Lint code
- Run tests
- Check types
- Build verification
```

**CD (Continuous Deployment)** :
```yaml
on: [push to main]
- Run full test suite
- Build production
- Deploy to Vercel
- Notify on Discord/Slack
```

**Environments** :
- Development (auto-deploy branches)
- Staging (pre-production)
- Production (main branch)

---

### v5.0 - Features avancées (FINALE)
**Fonctionnalités** :

**Upload & médias** :
- ✅ Upload avatar de personnage
- ✅ Compression automatique images
- ✅ Storage (Cloudinary ou S3)

**Notifications** :
- ✅ Emails transactionnels (Resend/SendGrid)
- ✅ Notification completion objectif
- ✅ Rappels hebdomadaires

**Partage** :
- ✅ URL publique de personnage
- ✅ Partage de build
- ✅ Export de données (JSON/CSV)
- ✅ Import de données

**Analytics** :
- ✅ Vercel Analytics ou Plausible
- ✅ Dashboard de stats
- ✅ Tracking événements (ajout perso, objectif complété)

**Stats globales (publiques)** :
- Nombre total de personnages
- Classe la plus jouée
- Niveau moyen
- Serveur le plus populaire
- Objectifs les plus complétés

**Easter eggs WoW** :
- Konami code → animation spéciale
- Commandes secrètes dans search (ex: "/leeroy")
- Références WoW cachées

**Documentation** :
- Guide utilisateur complet
- FAQ
- Changelog
- API documentation

---

## 🔮 FEATURES FUTURES (Post v5.0)

### Ideas avancées
- 🔮 Mode guilde (gestion multi-personnages)
- 🔮 Raid planner avec compositions
- 🔮 DKP/Loot council system
- 🔮 Calendrier d'événements (raids, PvP)
- 🔮 Marketplace items/services
- 🔮 Wiki communautaire (guides, builds)
- 🔮 Chat temps réel (WebSockets)
- 🔮 Notifications push (PWA)
- 🔮 Mobile app (React Native)
- 🔮 Integration Discord bot
- 🔮 Comparateur de builds
- 🔮 Simulateur de combat

---

## 📊 RÉSUMÉ PAR VERSION

| Version | Nom | Features clés | Techno principale |
|---------|-----|---------------|-------------------|
| v0.1 | Structure | HTML statique | HTML |
| v0.2 | Style | Design responsive | CSS |
| v0.3 | Dynamique | JS interactif | JavaScript |
| v0.4 | Persistence | localStorage | JavaScript |
| v0.5 | Calculateurs | API + graphs | JavaScript async |
| v0.6 | En ligne | Déploiement | Git/Netlify |
| v1.0 | **Vanilla complète** | Polie et accessible | HTML/CSS/JS |
| v2.0 | React | Composants | React |
| v2.1 | Routing | Navigation SPA | React Router |
| v2.2 | Tailwind | Design system | Tailwind CSS |
| v2.3 | Shadcn | UI pro | Shadcn/ui |
| v3.0 | Next.js | SSR | Next.js |
| v3.1 | API | Backend | Express |
| v3.2 | BDD | Persistence | PostgreSQL/Prisma |
| v4.0 | Auth | Multi-users | NextAuth |
| v4.1 | Tests | Quality | Jest/RTL |
| v4.2 | Perf | Optimisation | Next optimizations |
| v4.3 | DevOps | Automation | GitHub Actions |
| v5.0 | **FINALE** | Production-ready | Full stack moderne |

---

**Total features** : 150+ fonctionnalités
**Durée développement** : 6-9 mois
**Technologies maîtrisées** : 20+

**🎮 FOR THE HORDE! (ou Alliance, on juge pas) 🎮**
