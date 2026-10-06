# InfoVault

InfoVault is a private, searchable personal information vault for the details
you repeatedly use in applications, profiles, forms, and other workflows.
Store your information once, find it quickly, and copy exactly what you need
without keeping sensitive details scattered across documents and notes.

## Highlights

- **One organized vault** for personal details, education, experience, skills,
  projects, applications, documents, and reusable snippets.
- **Fast navigation and search** across vault sections from a focused dashboard.
- **Quick copy workflows** for frequently used profile fields and records.
- **Favorites and history controls** for the information you use most often.
- **Import and export** using a validated, versioned JSON format so your data
  remains portable.
- **Account-based privacy** with Supabase authentication and per-user data
  access.
- **Responsive interface** with accessible dialogs, command navigation, and
  reduced-motion support.

## Tech stack

- React 19 and TypeScript
- TanStack Start and TanStack Router
- Vite 8
- Tailwind CSS 4
- Supabase Auth and Postgres
- Drizzle ORM and Drizzle Kit
- Radix UI primitives
- Recharts
- GSAP

## Getting started

### Prerequisites

- Node.js 18 or newer
- npm
- A Supabase project

### Installation

```bash
git clone <your-repository-url>
cd infovault
npm install
```

Create a local `.env` file with the public Supabase settings for your project:

```dotenv
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_PUBLISHABLE_KEY=your-publishable-key
```

Do not commit `.env` or server-side credentials. The publishable key is
intended for browser use; database access must still be protected by Supabase
Row Level Security policies.

Start the development server:

```bash
npm run dev
```

Then open the local URL printed by Vite.

## Available commands

| Command | Description |
| --- | --- |
| `npm run dev` | Start the Vite development server |
| `npm run build` | Create a production build |
| `npm run build:dev` | Create a development-mode build |
| `npm run preview` | Preview the production build locally |
| `npm run lint` | Run ESLint |
| `npm run format` | Format the project with Prettier |

## Data and database

The database schema and migration history are in [`drizzle/`](./drizzle).
Supabase integration code lives in
[`src/integrations/supabase/`](./src/integrations/supabase), while vault data
access and import/export validation are handled in
[`src/lib/data/vault.ts`](./src/lib/data/vault.ts).

If you need to generate or apply database migrations, configure the migration
database URL expected by [`drizzle.config.ts`](./drizzle.config.ts) before
running Drizzle Kit commands.

## Project structure

```text
src/
├── components/       Reusable UI, landing, auth, and vault components
├── integrations/     Supabase and authentication integrations
├── lib/               Vault models, validation, data access, and utilities
├── routes/            TanStack Start application routes
└── styles.css        Global styles and design tokens

drizzle/
└── migrations/       Database migration history
```

## Security and privacy

InfoVault is designed for personal data, so treat configuration and database
access as production-sensitive:

- Keep service-role and migration credentials on the server only.
- Enable and review Row Level Security for every user-owned table.
- Never commit `.env`, exported vault files, or real personal information.
- Use the import/export feature carefully because exported JSON contains vault
  data in readable form.

## Deployment

The project is configured for TanStack Start and a Node.js-compatible server
build through [`vite.config.ts`](./vite.config.ts). Build the application with:

```bash
npm run build
```

The generated `dist/` directory can then be deployed to a Node.js-compatible
hosting provider.

## Contributing

1. Create a feature branch.
2. Make focused changes and keep user data out of commits.
3. Run `npm run build` and `npm run lint` before opening a pull request.
4. Include a short description of behavior changes and any migration impact.

## License

No license has been added to this repository yet. Until one is provided, all
rights are reserved by the repository owner.
