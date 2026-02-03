# 🗂️ STRUCTURE DU PROJET - WoW Classic Tracker

## 📁 Organisation générale

Ce document explique comment structurer ton code au fur et à mesure de l'évolution du projet.

---

## PHASE 1 : VANILLA (Semaines 1-8)

### Structure initiale (v0.1 - v1.0)

```
wow-classic-tracker/
│
├── index.html              # Page d'accueil
├── characters.html         # Liste des personnages
├── character-detail.html   # Détail d'un personnage
│
├── css/
│   ├── styles.css          # Styles globaux
│   ├── components.css      # Composants réutilisables
│   └── responsive.css      # Media queries
│
├── js/
│   ├── app.js              # Point d'entrée principal
│   ├── characters.js       # Logique des personnages
│   ├── storage.js          # Gestion localStorage
│   ├── ui.js               # Manipulation DOM
│   ├── calculators.js      # Calculateurs (DPS, stats, gold)
│   └── utils.js            # Fonctions utilitaires
│
├── assets/
│   ├── images/
│   │   ├── logo.png
│   │   ├── classes/        # Icônes de classes
│   │   └── icons/          # Icônes diverses
│   └── fonts/              # Fonts custom (optionnel)
│
├── .gitignore
├── README.md
└── LICENSE
```

### Fichiers clés

**index.html**
```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>WoW Classic Tracker</title>
  <link rel="stylesheet" href="css/styles.css">
</head>
<body>
  <header>
    <nav><!-- Navigation --></nav>
  </header>
  <main>
    <!-- Contenu -->
  </main>
  <footer>
    <!-- Footer -->
  </footer>
  <script src="js/app.js" type="module"></script>
</body>
</html>
```

**js/app.js** (point d'entrée)
```javascript
import { loadCharacters, displayCharacters } from './characters.js';
import { initFilters } from './ui.js';

document.addEventListener('DOMContentLoaded', () => {
  const characters = loadCharacters();
  displayCharacters(characters);
  initFilters();
});
```

**js/storage.js**
```javascript
export function saveData(key, data) {
  localStorage.setItem(key, JSON.stringify(data));
}

export function loadData(key) {
  const data = localStorage.getItem(key);
  return data ? JSON.parse(data) : null;
}

export function removeData(key) {
  localStorage.removeItem(key);
}
```

**js/characters.js**
```javascript
import { saveData, loadData } from './storage.js';

export function loadCharacters() {
  return loadData('characters') || [];
}

export function addCharacter(character) {
  const characters = loadCharacters();
  characters.push({ ...character, id: generateId() });
  saveData('characters', characters);
}

export function deleteCharacter(id) {
  const characters = loadCharacters();
  const filtered = characters.filter(c => c.id !== id);
  saveData('characters', filtered);
}

// ...
```

---

## PHASE 2 : REACT (Semaines 9-14)

### Structure React/Vite (v2.0 - v2.3)

```
wow-classic-tracker/
│
├── public/
│   ├── favicon.ico
│   └── images/
│
├── src/
│   ├── main.jsx            # Point d'entrée
│   ├── App.jsx             # Composant racine
│   │
│   ├── components/
│   │   ├── ui/             # Composants UI réutilisables
│   │   │   ├── Button.jsx
│   │   │   ├── Input.jsx
│   │   │   ├── Card.jsx
│   │   │   └── Badge.jsx
│   │   │
│   │   ├── layout/
│   │   │   ├── Header.jsx
│   │   │   ├── Navigation.jsx
│   │   │   └── Footer.jsx
│   │   │
│   │   └── characters/
│   │       ├── CharacterCard.jsx
│   │       ├── CharacterList.jsx
│   │       ├── CharacterForm.jsx
│   │       ├── CharacterDetail.jsx
│   │       ├── CharacterFilters.jsx
│   │       ├── ObjectivesList.jsx
│   │       ├── ReputationTracker.jsx
│   │       └── MountsList.jsx
│   │
│   ├── pages/              # Pages (avec React Router)
│   │   ├── Home.jsx
│   │   ├── Characters.jsx
│   │   ├── CharacterDetailPage.jsx
│   │   ├── Calculators.jsx
│   │   └── NotFound.jsx
│   │
│   ├── hooks/              # Custom hooks
│   │   ├── useLocalStorage.js
│   │   ├── useCharacters.js
│   │   ├── useReputation.js
│   │   └── useCalculator.js
│   │
│   ├── context/            # Context API
│   │   └── CharactersContext.jsx
│   │
│   ├── utils/              # Fonctions utilitaires
│   │   ├── calculations.js
│   │   ├── formatters.js
│   │   └── validators.js
│   │
│   ├── data/               # Données statiques
│   │   ├── classes.js
│   │   ├── reputations.js
│   │   └── mounts.js
│   │
│   └── styles/             # Styles (si pas full Tailwind)
│       └── index.css
│
├── .gitignore
├── package.json
├── vite.config.js
├── tailwind.config.js      # Config Tailwind
├── components.json         # Config Shadcn
└── README.md
```

### Exemple de composant

**CharacterCard.jsx**
```jsx
import { Card } from '@/components/ui/card';
import { Badge } from '@/components/ui/badge';

export function CharacterCard({ character, onDelete }) {
  return (
    <Card className="p-4 hover:shadow-lg transition">
      <div className="flex justify-between items-start">
        <div>
          <h3 className="text-xl font-bold">{character.name}</h3>
          <Badge className={`class-${character.class.toLowerCase()}`}>
            {character.class}
          </Badge>
        </div>
        <span className="text-2xl font-bold">
          {character.level}
        </span>
      </div>
      <div className="mt-4 flex gap-2">
        <Button variant="outline" asChild>
          <Link to={`/characters/${character.id}`}>Voir</Link>
        </Button>
        <Button variant="destructive" onClick={() => onDelete(character.id)}>
          Supprimer
        </Button>
      </div>
    </Card>
  );
}
```

**Custom Hook : useCharacters.js**
```javascript
import { useState, useEffect } from 'react';
import { useLocalStorage } from './useLocalStorage';

export function useCharacters() {
  const [characters, setCharacters] = useLocalStorage('characters', []);

  const addCharacter = (character) => {
    setCharacters([...characters, { ...character, id: crypto.randomUUID() }]);
  };

  const deleteCharacter = (id) => {
    setCharacters(characters.filter(c => c.id !== id));
  };

  const updateCharacter = (id, updates) => {
    setCharacters(
      characters.map(c => c.id === id ? { ...c, ...updates } : c)
    );
  };

  return {
    characters,
    addCharacter,
    deleteCharacter,
    updateCharacter
  };
}
```

---

## PHASE 2 : NEXT.JS (Semaines 15-20)

### Structure Next.js App Router (v3.0 - v3.2)

```
wow-classic-tracker/
│
├── app/
│   ├── layout.tsx              # Layout global
│   ├── page.tsx                # Page d'accueil (/)
│   ├── globals.css             # Styles globaux
│   │
│   ├── characters/
│   │   ├── layout.tsx          # Layout pour /characters
│   │   ├── page.tsx            # Liste personnages (/characters)
│   │   ├── loading.tsx         # Loading state
│   │   ├── error.tsx           # Error boundary
│   │   │
│   │   ├── new/
│   │   │   └── page.tsx        # Nouveau personnage
│   │   │
│   │   └── [id]/
│   │       ├── page.tsx        # Détail personnage
│   │       ├── loading.tsx
│   │       └── edit/
│   │           └── page.tsx    # Édition
│   │
│   ├── calculators/
│   │   ├── page.tsx            # Liste calculateurs
│   │   ├── dps/
│   │   │   └── page.tsx
│   │   ├── stats/
│   │   │   └── page.tsx
│   │   └── gold/
│   │       └── page.tsx
│   │
│   ├── profile/
│   │   └── page.tsx            # Profil utilisateur
│   │
│   └── api/                    # API Routes
│       ├── characters/
│       │   ├── route.ts        # GET, POST /api/characters
│       │   └── [id]/
│       │       ├── route.ts    # GET, PUT, DELETE /api/characters/:id
│       │       └── objectives/
│       │           └── route.ts
│       └── auth/
│           └── [...nextauth]/
│               └── route.ts
│
├── components/
│   ├── ui/                     # Shadcn components
│   │   ├── button.tsx
│   │   ├── input.tsx
│   │   ├── card.tsx
│   │   └── ...
│   │
│   ├── characters/
│   │   ├── character-card.tsx
│   │   ├── character-form.tsx
│   │   ├── character-list.tsx
│   │   └── ...
│   │
│   └── layout/
│       ├── header.tsx
│       ├── navigation.tsx
│       └── footer.tsx
│
├── lib/
│   ├── db.ts                   # Prisma client
│   ├── auth.ts                 # NextAuth config
│   ├── validations.ts          # Zod schemas
│   └── utils.ts                # Utilities
│
├── hooks/
│   ├── use-characters.ts
│   └── use-toast.ts
│
├── types/
│   └── index.ts                # TypeScript types
│
├── prisma/
│   ├── schema.prisma           # Schéma BDD
│   ├── migrations/             # Migrations
│   └── seed.ts                 # Seeds
│
├── public/
│   ├── images/
│   └── favicon.ico
│
├── .env.local                  # Variables d'environnement
├── .gitignore
├── next.config.js
├── tailwind.config.ts
├── tsconfig.json
├── package.json
└── README.md
```

### Fichiers clés Next.js

**app/layout.tsx**
```tsx
import './globals.css';
import { Header } from '@/components/layout/header';
import { Footer } from '@/components/layout/footer';

export const metadata = {
  title: 'WoW Classic Tracker',
  description: 'Gérez vos personnages WoW Classic',
};

export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html lang="fr">
      <body>
        <Header />
        <main className="min-h-screen container mx-auto px-4 py-8">
          {children}
        </main>
        <Footer />
      </body>
    </html>
  );
}
```

**app/api/characters/route.ts**
```typescript
import { NextResponse } from 'next/server';
import { prisma } from '@/lib/db';
import { characterSchema } from '@/lib/validations';

export async function GET() {
  const characters = await prisma.character.findMany({
    include: {
      objectives: true,
      reputations: true,
    },
  });
  return NextResponse.json(characters);
}

export async function POST(request: Request) {
  const body = await request.json();
  const validated = characterSchema.parse(body);
  
  const character = await prisma.character.create({
    data: validated,
  });
  
  return NextResponse.json(character, { status: 201 });
}
```

**lib/db.ts**
```typescript
import { PrismaClient } from '@prisma/client';

const globalForPrisma = global as unknown as { prisma: PrismaClient };

export const prisma =
  globalForPrisma.prisma ||
  new PrismaClient({
    log: ['query'],
  });

if (process.env.NODE_ENV !== 'production') globalForPrisma.prisma = prisma;
```

**prisma/schema.prisma**
```prisma
generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model User {
  id         String      @id @default(uuid())
  email      String      @unique
  name       String
  image      String?
  characters Character[]
  createdAt  DateTime    @default(now())
  updatedAt  DateTime    @updatedAt
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

// ... autres modèles
```

---

## PHASE 3 : PROFESSIONNALISATION (Semaines 21-28)

### Ajouts structure finale (v4.0 - v5.0)

```
wow-classic-tracker/
│
├── (structure Next.js précédente)
│
├── __tests__/              # Tests
│   ├── unit/
│   │   ├── utils.test.ts
│   │   └── calculations.test.ts
│   ├── components/
│   │   ├── character-card.test.tsx
│   │   └── character-form.test.tsx
│   └── integration/
│       └── characters.test.tsx
│
├── .github/
│   └── workflows/
│       ├── ci.yml          # Tests + Lint
│       └── cd.yml          # Deploy
│
├── docs/
│   ├── API.md              # Documentation API
│   ├── CONTRIBUTING.md     # Guide contribution
│   └── CHANGELOG.md        # Historique versions
│
├── scripts/
│   ├── seed.ts             # Script de seed
│   └── migrate.ts          # Migrations custom
│
├── .env.example            # Template env vars
├── .eslintrc.json          # Config ESLint
├── .prettierrc             # Config Prettier
├── jest.config.js          # Config Jest
└── vercel.json             # Config Vercel
```

---

## 📋 CONVENTIONS DE NOMMAGE

### Fichiers
- **Composants React** : PascalCase → `CharacterCard.jsx`
- **Hooks** : camelCase avec préfixe use → `useCharacters.js`
- **Utils/Lib** : camelCase → `calculations.js`
- **Types** : PascalCase → `Character.ts`
- **Pages Next.js** : kebab-case → `character-detail.tsx`

### Dossiers
- kebab-case → `character-list/`, `api-routes/`

### Code
- **Variables/Fonctions** : camelCase → `const characterName`, `function addCharacter()`
- **Constantes** : UPPER_SNAKE_CASE → `const MAX_LEVEL = 60`
- **Classes/Types** : PascalCase → `class Character`, `type UserType`
- **Composants** : PascalCase → `function CharacterCard()`

---

## 🗃️ GESTION DES BRANCHES GIT

```
main            # Production (déployée)
├── develop     # Développement principal
    ├── feature/character-detail
    ├── feature/calculators
    ├── feature/authentication
    └── fix/bug-level-validation
```

**Convention commits** :
```
feat: ajout calculateur de DPS
fix: correction bug niveau max
docs: mise à jour README
style: formatage code
refactor: restructuration composants
test: ajout tests CharacterCard
chore: update dependencies
```

---

## 📦 GESTION DES DÉPENDANCES

### Phase Vanilla
```json
// Aucune dépendance (vanilla JS)
```

### Phase React
```json
{
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-router-dom": "^6.x"
  },
  "devDependencies": {
    "vite": "^5.x",
    "@vitejs/plugin-react": "^4.x"
  }
}
```

### Phase React + Tailwind + Shadcn
```json
{
  "dependencies": {
    // ... React
    "tailwindcss": "^3.x",
    "@radix-ui/react-*": "^1.x",  // Shadcn dependencies
    "class-variance-authority": "^0.7.x",
    "clsx": "^2.x",
    "tailwind-merge": "^2.x"
  }
}
```

### Phase Next.js Full Stack
```json
{
  "dependencies": {
    "next": "^14.x",
    "react": "^18.x",
    "react-dom": "^18.x",
    "@prisma/client": "^5.x",
    "next-auth": "^4.x",
    "zod": "^3.x",
    "recharts": "^2.x"  // Graphiques
  },
  "devDependencies": {
    "prisma": "^5.x",
    "typescript": "^5.x",
    "@types/react": "^18.x",
    "@types/node": "^20.x",
    "eslint": "^8.x",
    "prettier": "^3.x",
    "jest": "^29.x",
    "@testing-library/react": "^14.x"
  }
}
```

---

## 🔐 VARIABLES D'ENVIRONNEMENT

**.env.local**
```env
# Database
DATABASE_URL="postgresql://user:password@localhost:5432/wowtracker"

# NextAuth
NEXTAUTH_SECRET="ton-secret-super-secure"
NEXTAUTH_URL="http://localhost:3000"

# OAuth Providers
GOOGLE_CLIENT_ID="..."
GOOGLE_CLIENT_SECRET="..."
DISCORD_CLIENT_ID="..."
DISCORD_CLIENT_SECRET="..."

# Email
RESEND_API_KEY="..."

# Storage
CLOUDINARY_URL="..."

# Analytics
NEXT_PUBLIC_ANALYTICS_ID="..."
```

**.env.example** (commit ce fichier, pas .env.local)
```env
DATABASE_URL=
NEXTAUTH_SECRET=
NEXTAUTH_URL=
GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=
```

---

## 🚀 SCRIPTS UTILES

**package.json**
```json
{
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "eslint . --ext .ts,.tsx",
    "format": "prettier --write .",
    "test": "jest",
    "test:watch": "jest --watch",
    "test:coverage": "jest --coverage",
    "db:push": "prisma db push",
    "db:migrate": "prisma migrate dev",
    "db:seed": "prisma db seed",
    "db:studio": "prisma studio",
    "prepare": "husky install"
  }
}
```

---

## 📚 ORGANISATION DU README

**README.md structure recommandée** :
```markdown
# 🎮 WoW Classic Tracker

Description du projet

## 🚀 Démarrage rapide

Installation et lancement

## 🛠️ Technologies

Stack technique

## 📸 Screenshots

Captures d'écran

## ✨ Fonctionnalités

Liste des features

## 🗺️ Roadmap

Lien vers ROADMAP.md

## 🤝 Contribution

Guide de contribution

## 📄 Licence

MIT
```

---

**Cette structure évoluera au fil des phases. Commence simple et complexifie progressivement ! 🚀**
