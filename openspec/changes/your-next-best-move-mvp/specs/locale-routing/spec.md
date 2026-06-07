## ADDED Requirements

### Requirement: Browser language detection

The site SHALL detect a visitor's preferred language from their browser settings and redirect accordingly.

#### Scenario: Visitor with en-GB preference is redirected

- **GIVEN** a visitor's browser `Accept-Language` header is set to `en-GB`
- **WHEN** they navigate to the site root `/`
- **THEN** they are redirected to `/en-GB`

#### Scenario: Visitor with unsupported language falls back to en-GB

- **GIVEN** a visitor's browser `Accept-Language` header is set to `fr-FR`
- **AND** French is not yet a supported locale
- **WHEN** they navigate to the site root `/`
- **THEN** they are redirected to `/en-GB`

#### Scenario: Visitor navigates directly to a locale-prefixed URL

- **GIVEN** a visitor navigates directly to `/en-GB/search`
- **WHEN** the page loads
- **THEN** they are not redirected
- **AND** content is displayed in English (en-GB)

### Requirement: Locale-prefixed URLs

All application routes SHALL include a locale segment (`/:locale/...`).

#### Scenario: Search page URL includes locale

- **GIVEN** a visitor is browsing in the en-GB locale
- **WHEN** they navigate to the property search page
- **THEN** the URL follows the pattern `/en-GB/search`

#### Scenario: Property detail URL includes locale

- **GIVEN** a visitor is browsing in the en-GB locale
- **WHEN** they view property ID 123
- **THEN** the URL follows the pattern `/en-GB/property/123`

### Requirement: Locale-aware currency formatting

Prices SHALL be formatted according to the active locale.

#### Scenario: Price is formatted for en-GB

- **GIVEN** the active locale is en-GB
- **WHEN** a property price of 250000 is displayed
- **THEN** it is rendered as "£250,000"

#### Scenario: Currency formatting adapts to a different locale

- **GIVEN** the active locale is de-DE
- **WHEN** a property price of 250000 is displayed
- **THEN** it is rendered using German number formatting conventions

### Requirement: Locale-aware date formatting

Dates SHALL be formatted according to the active locale.

#### Scenario: Date is formatted for en-GB

- **GIVEN** the active locale is en-GB
- **WHEN** a date such as 15 March 2026 is displayed
- **THEN** it is rendered as "15/03/2026" or "15 March 2026" following en-GB conventions

### Requirement: Adding a new locale requires only translation files

The locale system SHALL be architected so a new locale can be added without code changes.

#### Scenario: New locale is added via translation file

- **GIVEN** the site currently supports only en-GB
- **WHEN** a developer adds a `messages/fr-FR.json` translation file
- **AND** registers `fr-FR` in the locale configuration
- **THEN** the site serves content in French at `/fr-FR/...` routes
- **AND** no component or routing code is modified
