# StockSense — Smart Inventory Forecasting Dashboard

A modern, responsive dashboard for retail store managers to monitor sales, track inventory, and view AI-powered demand forecasts. Built with React 19, TanStack Start, Tailwind CSS, and Recharts.

![Dashboard preview](https://github.com/user-attachments/assets/e8db6c81-d9d2-4b2e-abda-b3a05943f996)

## Features

- **Sidebar navigation** — Quick access to Overview, Inventory, Forecasting, Analytics, and Settings
- **Sales overview cards** — At-a-glance KPIs: Total Revenue, Orders Today, Active SKUs, and Low Stock Alerts
- **Inventory status table** — Live stock levels, reorder points, and status badges (In Stock / Low Stock / Out of Stock)
- **Demand prediction** — AI-powered 3-day forecast chart with confidence-scored recommendations
- **Sales charts** — Daily (area) and weekly (bar) revenue visualizations
- **Responsive design** — Fully responsive layout that works on desktop and tablet

## Tech Stack

| Layer | Technology |
|-------|------------|
| Framework | [TanStack Start](https://tanstack.com/start) (React 19 + Vite) |
| Styling | Tailwind CSS v4 + native CSS variables |
| UI Components | Radix UI primitives + shadcn/ui |
| Charts | Recharts |
| Routing | TanStack Router (file-based) |
| Package Manager | Bun |
| Language | TypeScript |

## Prerequisites

- [Bun](https://bun.sh) 1.1+ (or Node.js 20+ with `npm`)
- Git

## Setup

1. **Clone the repository**

   ```bash
   git clone https://github.com/forecast-buddy-52.git
   cd forecast-buddy-52
   ```

2. **Install dependencies**

   ```bash
   bun install
   ```

   > If you don't have Bun, you can use `npm install` instead.

3. **Configure environment variables**

   Create a `.env` file in the project root. The app uses Vite's env handling. Public variables need the `VITE_` prefix. Server-only variables (used inside `createServerFn` handlers or `.server.ts` files) do **not** need a prefix and are never exposed to the browser.

   ```bash
   # Public (shipped to the browser)
   VITE_APP_NAME=StockSense

   # Server-only (backend / API keys)
   # Add any external API keys, database URLs, or webhook secrets here.
   # These are read inside server functions, never bundled to the client.
   ```

   > **Security note:** Never commit `.env` to Git. It's already ignored in `.gitignore`.

## Running Locally

Start the development server:

```bash
bun run dev
```

The app will be available at `http://localhost:3000`.

## Available Scripts

| Script | Description |
|--------|-------------|
| `bun run dev` | Start the Vite dev server with SSR |
| `bun run build` | Production build |
| `bun run build:dev` | Development build |
| `bun run preview` | Preview the production build locally |
| `bun run lint` | Run ESLint |
| `bun run format` | Format code with Prettier |

## Project Structure

```
├── src/
│   ├── components/
│   │   ├── dashboard/        # Dashboard-specific components
│   │   │   ├── AppSidebar.tsx
│   │   │   ├── DemandPrediction.tsx
│   │   │   ├── InventoryTable.tsx
│   │   │   ├── SalesCharts.tsx
│   │   │   └── StatCard.tsx
│   │   └── ui/               # shadcn/ui components
│   ├── lib/                  # Utilities, server config, helpers
│   ├── routes/               # TanStack file-based routes
│   │   ├── __root.tsx        # Root layout (HTML shell)
│   │   └── index.tsx         # Dashboard homepage
│   ├── styles.css            # Global styles, CSS variables, Tailwind imports
│   ├── router.tsx            # Router configuration
│   └── start.ts              # TanStack Start instance config
├── package.json
├── tsconfig.json
├── vite.config.ts
└── README.md
```

## Environment Variable Reference

| Variable | Prefix | Scope | Example Use |
|----------|--------|-------|-------------|
| `VITE_*` | `VITE_` | Client + Server | Public config (app name, API base URLs, analytics IDs) |
| `API_KEY`, `DATABASE_URL`, etc. | None | Server only | Secrets read inside `createServerFn` handlers or `.server.ts` helpers |

For server-side configuration, see `src/lib/config.server.ts`.

## Customization

- **Theme / colors:** Edit CSS variables in `src/styles.css`.
- **Routes:** Add new pages by creating `.tsx` files under `src/routes/`. TanStack Router auto-generates the route tree.
- **Charts data:** Swap out the static demo data in the dashboard components with real API calls using `createServerFn`.

## License

MIT
