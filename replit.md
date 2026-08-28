# MedQorix

MedQorix is a responsive biomedical-waste operations workspace for hospital teams, with AI-assisted identification, collection coordination, traceability, and facility insights.

## Run & Operate

- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm --filter @workspace/medqorix run dev` — run the MedQorix web app
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

- `artifacts/medqorix/src/App.tsx` — role-aware app shell, routes, demo data, and workflows
- `artifacts/medqorix/src/index.css` — MedQorix theme tokens, responsive utilities, and motion
- `artifacts/medqorix/index.html` — page metadata and product title
- `lib/api-spec/openapi.yaml` — shared API contract when backend capabilities are added

## Architecture decisions

- The first release is demo-first and works without external credentials or a configured Firebase project.
- Demo state is persisted in browser localStorage so the complete workflow can be demonstrated across navigation and reloads.
- Role switching is available from Profile to make all three operational perspectives easy to demonstrate.
- The visual language uses deep teal/navy for operational focus, aqua for positive flow, amber for attention, and red for urgent states.

## Product

- Hospital Staff can review facility activity, run an AI-assisted sample scan, and create collection requests.
- Collection Staff can advance requests through assignment, route, and completion states.
- Administrators can review analytics, manage people, configure waste categories, and read notifications.
- Waste History includes a traceability timeline for each record.
- Dark mode, mobile bottom navigation, desktop sidebar navigation, search/filter states, dialogs, and empty states are included.

## User preferences

- The product name is MedQorix and must remain the only product name used in the app.

## Gotchas

- The demo data is intentionally local-only and is not a substitute for a production persistence or authentication layer.
- AI scan copy must remain clearly AI-assisted and non-authoritative; hospital protocol verification is the final decision point.

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
