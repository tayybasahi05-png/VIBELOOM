# Global Social Marketplace

A mobile-first social marketplace for discovering creators, products, live rooms, opportunities, and conversations.

## Run & Operate

- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- Required env: `DATABASE_URL` — Postgres connection string

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- API: Express 5
- DB: PostgreSQL + Drizzle ORM
- Validation: Zod (`zod/v4`), `drizzle-zod`
- API codegen: Orval (from OpenAPI spec)
- Build: esbuild (CJS bundle)

## Where things live

- `artifacts/global-social` — React + Vite web application
- `artifacts/api-server` — Express API and Clerk proxy
- `lib/api-spec/openapi.yaml` — API contract and generated client source
- `artifacts/global-social/src/index.css` — cream and olive visual theme

## Architecture decisions

- Clerk provides managed authentication and Google sign-in.
- OpenAPI is the source of truth for frontend hooks and server validation.
- The first product slice establishes typed social, market, inbox, live, wallet, and discovery APIs before expanding into provider-backed streaming, calls, and payments.

## Product

The current product slice includes a branded login experience, personalized social feed, global search and discovery, marketplace browsing and product details, live-room discovery, inbox messaging, notifications, wallet overview, and opportunities.

## User preferences

- Premium, modern, mobile-first design with a cream and olive-green theme.
- Never replace required real functionality with fake buttons, mock flows, or placeholder screens.

## Gotchas

- Regenerate API clients after every OpenAPI change.
- Clerk proxy middleware must be mounted before body parsers.

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
