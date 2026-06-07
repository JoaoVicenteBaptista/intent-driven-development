## Context

"YourNextBestMove" is a greenfield property marketplace MVP. The first release targets property seekers (buyers/renters) with a 6-capability flow: land, search, filter, view details, enquire, all locale-aware. There is no backend API, no database, no authentication — everything runs in a single Next.js frontend backed by mock data. This design captures the technical decisions that turn the proposal's capabilities into a buildable system.

No ADRs exist yet; this design will inform the first ADRs.

### System Context (C4 Level 1)

```text
+-------------------+       browses & enquires       +-------------------------+
|  Property Seeker  | ------------------------------> |  YourNextBestMove       |
|  (Buyer / Renter) |                                 |  (Next.js Web App)      |
+-------------------+                                 +-------------------------+
```

- **Property Seeker** — the sole user role. No agents, no admins in MVP.
- **YourNextBestMove** — self-contained Next.js app. No external systems (no API, no auth provider, no database, no email service).

### Container (C4 Level 2)

```text
+------------------------------------------------------------------+
|                    YourNextBestMove (Next.js)                     |
|                                                                  |
|  +------------------+     serves pages     +------------------+  |
|  |   App Router     | -------------------> |  Route Handlers  |  |
|  |  (pages/layouts) |                      |  (SSR/SSG)       |  |
|  +------------------+                      +------------------+  |
|          |                                         |              |
|          | renders                                 | reads        |
|          v                                         v              |
|  +------------------+                      +------------------+  |
|  |  UI Components   |                      |  Mock Data Store |  |
|  |  (React, TW)     |                      |  (JSON files)    |  |
|  +------------------+                      +------------------+  |
|          |                                                       |
|          | uses                                                  |
|          v                                                       |
|  +------------------+                                            |
|  |  Locale System   |                                            |
|  |  (middleware +    |                                            |
|  |   next-intl)      |                                            |
|  +------------------+                                            |
|                                                                  |
|  +------------------+                                            |
|  |  Static Assets   |                                            |
|  |  (images,        |                                            |
|  |   floorplans)    |                                            |
|  +------------------+                                            |
+------------------------------------------------------------------+
```

- **App Router** — file-based routing using Next.js App Router. Pages are Server Components by default; client interactivity (carousel, form, filters) uses `"use client"` islands.
- **Route Handlers** — server-side loaders that read mock JSON and return data for SSR/SSG pages. Never calls an external API in MVP.
- **Mock Data Store** — one or more JSON files defining properties, agents, and static content. Replicated in-memory at dev time; importable at build time for static pages.
- **UI Components** — React components styled with Tailwind CSS. Shared primitives: `PropertyCard`, `FilterBar`, `PhotoCarousel`, `EnquiryForm`.
- **Locale System** — `next-intl` middleware detects browser language, sets `/:locale` prefix, and provides formatting utilities (currency, dates).
- **Static Assets** — property photos and floorplan images stored in `public/images/`.

**Boundaries**: Everything lives in one container. The App Router is the only entry point. Mock data and static assets are co-located. No outbound network calls at runtime.

**Assumptions**: The mock data set is small enough (<1000 properties) to load synchronously or with minimal server-side filtering. Property images are pre-generated placeholder files.

## Goals / Non-Goals

**Goals:**
- Ship a working, navigable property marketplace UI with mock data
- Support all 6 capabilities: landing, search, filters, detail, contact, locale routing
- Use App Router, TypeScript, and Tailwind as the technical foundation
- Architect locale routing to support additional locales without rework
- Keep the codebase structured so a real API can replace the mock layer later

**Non-Goals:**
- Real backend, database, or auth integration
- Server-side form handling with email delivery
- Image optimization pipeline or CDN
- SEO beyond basic metadata
- Performance tuning for large datasets
- CI/CD, testing infrastructure (handled separately)

## Decisions

### 1. Next.js App Router over Pages Router

**Rationale**: App Router is the current Next.js recommended approach. Server Components align well with property listing pages (SSR for SEO, static generation for detail pages). Client Components ("use client") handle interactive islands like the carousel, filters, and form. Pages Router would work but would need a migration later.

**Alternatives considered**: Pages Router (rejected — legacy direction), Remix (rejected — team uses Next.js), pure Vite + React (rejected — no SSR/locale routing built in).

### 2. TypeScript

**Rationale**: Type safety for mock data shapes, component props, and locale messages. Catches mismatches early. Non-negotiable for a codebase intended to grow.

**Alternatives considered**: JavaScript (rejected — no type safety for growing team/codebase).

### 3. Tailwind CSS

**Rationale**: Utility-first, fast to prototype, consistent design tokens, small bundle with purging. Well-suited for an MVP that needs to look polished quickly.

**Alternatives considered**: CSS Modules (rejected — more boilerplate), styled-components (rejected — runtime cost, team familiarity with Tailwind).

### 4. Mock data as TypeScript/JSON modules

**Rationale**: Single source of truth for property data. JSON files (`src/data/properties.json`, `src/data/agents.json`) importable directly in server components and route handlers. No fetch mocking needed. When the real API arrives, swap the data access layer without touching UI components.

**Structure**:
- `src/data/properties.json` — array of property objects
- `src/data/agents.json` — array of agent objects
- `public/images/properties/<id>/` — photo and floorplan assets

**Alternatives considered**: MSW (rejected — overkill for static data), inline fixtures (rejected — mixes data with code), `json-server` (rejected — adds a dev dependency and runtime process).

### 5. Locale routing with `next-intl`

**Rationale**: `next-intl` provides middleware for locale detection, `/:locale` path prefixing, and React hooks for translations and formatting (currency, dates, numbers). It is the most mature i18n library for Next.js App Router.

**Architecture**: 
- `middleware.ts` detects `Accept-Language` header, redirects to `/:locale` prefix
- All pages live under `src/app/[locale]/`
- Translation messages in `messages/<locale>.json`
- Formatting via `useFormatter()` hook for currency, dates, numbers

**Alternatives considered**: `next-i18next` (rejected — Pages Router heritage), custom solution (rejected — reinventing locale detection, pluralization, formatting).

### 6. Page-based pagination

**Rationale**: Traditional `?page=N` query parameter. Server component reads `page` from `searchParams`, slices mock data accordingly. Simple, SEO-friendly (each page has a distinct URL), no client-side state management for pagination.

**Alternatives considered**: Infinite scroll (rejected — complex with SSR, harder to deep-link), cursor-based (rejected — overkill for mock data with no real DB).

### 7. Photo carousel — CSS snap scroll with React state

**Rationale**: Lightweight, no dependency. CSS `scroll-snap-type` handles the swipe/scroll UX. React state tracks the active slide index for dot indicators. Avoids adding a carousel library for an MVP.

**Alternatives considered**: Swiper.js (rejected — adds dependency for simple use case), Embla Carousel (rejected — same).

### 8. Contact form — client-side only in MVP

**Rationale**: No backend to POST to. Form validates inputs client-side and "sends" by logging to console + showing a success message. Structured so swapping in a real `fetch` to a future API endpoint is a one-line change.

**Alternatives considered**: Server Actions (rejected — no real backend to persist to), third-party form service (rejected — adds external dependency and cost).

## Risks / Trade-offs

| Risk | Mitigation |
|------|------------|
| Mock data doesn't reflect real search performance (filtering, sorting, pagination at scale) | Keep data access behind a clear interface (`src/lib/properties.ts`) so the real API swap is isolated |
| No auth means contact form has no spam/bot protection | Acceptable for MVP demo. CAPTCHA can be added when the real API lands |
| Locale architecture is untested with real multi-locale content beyond en-GB | Design the message key structure to be generic; adding a new locale is a single JSON file |
| CSS snap-scroll carousel may have accessibility gaps vs. a purpose-built library | Use semantic markup (`<section>`, `aria-label`, focusable slides). Revisit if accessibility audit flags issues |
| No image optimization — mock images served as-is | Acceptable for MVP. `next/image` can be adopted later when assets come from Blob Storage |

## Migration Plan

1. **Deploy**: `npm run build && npm start` on any Node.js host (Vercel, or local dev server for demo). No infrastructure dependencies.
2. **Rollback**: Re-deploy previous build. No database migrations, no API compatibility concerns.
3. **Real API handoff**: Replace `src/lib/properties.ts` functions to call the .NET API instead of reading JSON. UI components are already data-agnostic (they consume typed props).

## Open Questions

- What are the exact property type values for the filter? (house, flat, bungalow, apartment, maisonette, etc.) — determine with product owner before spec writing
- What EPC rating format is expected — a simple A-G badge, or the full SAP chart with numeric score?
- Should the contact form persist enquiries locally (localStorage) so they can be reviewed in-browser for demo purposes?
- How many mock properties should the seed data contain? (recommend 50-100 for realistic pagination and filter demonstration)
