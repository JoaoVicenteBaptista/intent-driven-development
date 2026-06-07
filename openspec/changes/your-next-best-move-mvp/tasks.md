## 1. Project scaffold

- [x] 1.1 Create Next.js project with App Router and TypeScript (`create-next-app`)
- [x] 1.2 Install and configure Tailwind CSS with PostCSS
- [x] 1.3 Set up `tsconfig.json` with `strict: true` and path aliases (`@/` → `src/`)
- [x] 1.4 Create `src/` directory structure: `app/`, `components/`, `data/`, `lib/`, `messages/`
- [x] 1.5 Add shared root layout with `<html>`, `<body>`, and metadata

## 2. Mock data layer

- [x] 2.1 Define TypeScript types: `Property`, `Agent`, `PropertyType`, `ListingType`
- [x] 2.2 Create `src/data/properties.json` with 50+ seed properties across multiple locations
- [x] 2.3 Create `src/data/agents.json` with seed agents
- [x] 2.4 Build `src/lib/properties.ts` with data access functions: `searchProperties`, `getPropertyById`, `getPropertyTypes`
- [x] 2.5 Generate placeholder property images and floorplans in `public/images/properties/`

## 3. Locale routing and internationalization

- [x] 3.1 Install and configure `next-intl` middleware for `Accept-Language` detection
- [x] 3.2 Create `messages/en-GB.json` with all UI strings (search labels, filters, form labels, etc.)
- [x] 3.3 Wrap `src/app/[locale]/` in `NextIntlClientProvider`
- [x] 3.4 Create a language switcher component (static for now, en-GB only)
- [x] 3.5 Verify locale-prefixed URLs work: `/en-GB` redirect, `/en-GB/search`, `/en-GB/property/123`
- [x] 3.6 Add `generateStaticParams` to return supported locales

## 4. Landing page

- [x] 4.1 Create `src/app/[locale]/page.tsx` — the homepage
- [x] 4.2 Build `LocationSearch` component: text input for location, "For Sale" / "To Rent" toggle
- [x] 4.3 Validate empty location on submit — show inline error, do not navigate
- [x] 4.4 On valid submit, navigate to `/[locale]/search?location=...&listingType=sale|rent`

## 5. Property search

- [x] 5.1 Create `src/app/[locale]/search/page.tsx` — search results page with SSR
- [x] 5.2 Read `searchParams` (location, listingType, page) and call `searchProperties`
- [x] 5.3 Build `PropertyCard` component: image, price, address, bedrooms, listing type badge
- [x] 5.4 Render results as a responsive grid (1 col mobile, 2-3 cols desktop)
- [x] 5.5 Implement pagination: `?page=N` query param, "Previous" and "Next" controls
- [x] 5.6 Handle empty results: show message and link back to homepage

## 6. Search filters

- [x] 6.1 Build `FilterBar` component: price range (min/max inputs), bedrooms (select/dropdown), property type (checkboxes), listing type (toggle)
- [x] 6.2 Bind filter changes to URL query parameters — each change navigates to updated URL
- [x] 6.3 Read all filter params in search page SSR and pass to `searchProperties`
- [x] 6.4 Implement "Clear all filters" link that resets to base search URL
- [x] 6.5 Show active filter count/badges so the visitor knows which filters are applied

## 7. Property detail page

- [x] 7.1 Create `src/app/[locale]/property/[id]/page.tsx` — dynamic route with `generateStaticParams`
- [x] 7.2 Resolve property by `id` from mock data via `getPropertyById`
- [x] 7.3 Build `PhotoCarousel`: CSS scroll-snap, prev/next arrows, dot indicators
- [x] 7.4 Display key facts section: price, bedrooms, bathrooms, square footage (omit missing fields)
- [x] 7.5 Render property description as formatted text
- [x] 7.6 Display floorplan image (omit section if no floorplan data)
- [x] 7.7 Build EPC rating badge showing rating letter on an A-G scale (omit if missing)

## 8. Contact agent form

- [x] 8.1 Build `EnquiryForm` component: name, email, message fields
- [x] 8.2 Implement client-side validation: name required, valid email format, message required
- [x] 8.3 On valid submit: show success toast/message and clear form
- [x] 8.4 Include property reference (ID and address) in the submission payload
- [x] 8.5 Confirm no auth gate — form is visible and functional without login

## 9. Polish and shared UI

- [x] 9.1 Create shared header with site logo/title and locale switcher placeholder
- [x] 9.2 Create shared footer with copyright
- [x] 9.3 Add `next/image` for property card thumbnails (basic optimization for static imports)
- [x] 9.4 Add loading states (skeleton cards) for search and detail pages
- [x] 9.5 Verify all specs pass manually against the built application
- [x] 9.6 Run `openspec validate your-next-best-move-mvp --type change --strict`
