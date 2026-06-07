## Why

"YourNextBestMove" is a new online estate agency launching a property marketplace. The MVP targets buyers and renters — delivering the core search-to-enquiry flow without authentication barriers so users can find and inquire about properties immediately. This initial release eschews agent portals, user accounts, and premium tooling to validate the core search experience first.

## What Changes

- Greenfield Next.js application (App Router, TypeScript, Tailwind) with mock data — no backend API in MVP scope
- Landing page with a location search bar and a "for sale"/"to rent" toggle
- Property search returning paginated property-card results
- Sidebar/filter controls for price range, bedrooms, property type, and sale/rent
- Property detail page with photo carousel, key facts, description, floorplan, and EPC rating
- Contact-agent enquiry form on the detail page (no login required — send only)
- Locale-aware routing with browser-language detection. URLs follow `/:locale/...`. Ships en-GB first; architected for more locales

## Capabilities

### New Capabilities

- `landing-page`: A single-page entry point with a prominent location search input and a sale/rent toggle, routing users into the search experience
- `property-search`: Location-based property search with paginated results rendered as property cards
- `search-filters`: Price range, bedroom count, property type, and sale/rent filters that refine search results
- `property-detail`: Full listing view including photo carousel, key facts (price, beds, baths, sq ft), text description, floorplan image, and EPC rating graphic
- `contact-agent`: Enquiry form on the property detail page capturing name, email, and message; submissions are persisted or echoed locally (no real email integration in MVP)
- `locale-routing`: Browser-language detection, locale-prefixed URLs, and locale-aware formatting (currency, dates). Initially ships en-GB

### Modified Capabilities

None — this is a greenfield change with no existing capabilities.

## Impact

- **New codebase**: Next.js App Router project with TypeScript and Tailwind CSS
- **Mock data layer**: In-memory or JSON-file mock data for properties, images, and agents
- **Dependencies**: Next.js, React, Tailwind CSS, and locale utility libraries (e.g., `next-intl` or equivalent)
- **No external API**: All data is self-contained; no Azure SQL, Blob Storage, or App Service required for MVP
