## ADDED Requirements

### Requirement: Filter search results by price range

Visitors SHALL be able to narrow results by specifying a minimum and maximum price.

#### Scenario: Visitor filters by price range

- **GIVEN** search results for "Manchester" show properties priced from £80,000 to £500,000
- **WHEN** the visitor sets a minimum price of £150,000 and a maximum price of £300,000
- **THEN** only properties priced between £150,000 and £300,000 are shown
- **AND** the URL reflects the price filter parameters

#### Scenario: Visitor sets only a minimum price

- **GIVEN** search results for "Leeds" show properties priced from £50,000 to £400,000
- **WHEN** the visitor sets a minimum price of £200,000
- **THEN** only properties priced £200,000 and above are shown

### Requirement: Filter search results by bedroom count

Visitors SHALL be able to narrow results by number of bedrooms.

#### Scenario: Visitor filters by bedroom count

- **GIVEN** search results contain properties with 1 to 5 bedrooms
- **WHEN** the visitor selects "3 bedrooms"
- **THEN** only properties with exactly 3 bedrooms are shown
- **AND** the URL reflects the bedroom filter parameter

### Requirement: Filter search results by property type

Visitors SHALL be able to narrow results by property type (house, flat, bungalow, etc.).

#### Scenario: Visitor filters by property type

- **GIVEN** search results contain houses, flats, and bungalows
- **WHEN** the visitor selects "Flat"
- **THEN** only flats are shown
- **AND** the URL reflects the property type filter parameter

#### Scenario: Visitor selects multiple property types

- **GIVEN** search results contain houses, flats, and bungalows
- **WHEN** the visitor selects "House" and "Bungalow"
- **THEN** only houses and bungalows are shown

### Requirement: Toggle between sale and rental listings

Visitors SHALL be able to switch between viewing properties for sale and properties to rent.

#### Scenario: Visitor switches from sale to rent

- **GIVEN** search results currently show properties for sale
- **WHEN** the visitor switches the toggle to "To Rent"
- **THEN** only rental properties are shown
- **AND** the URL reflects the listing type parameter

### Requirement: Filters combine and persist in URL

Multiple filters SHALL be combinable and MUST be reflected in the URL so results are shareable.

#### Scenario: Visitor applies multiple filters

- **GIVEN** search results for "Bristol" show 100 properties
- **WHEN** the visitor sets price £100,000-£250,000, selects 2 bedrooms, and selects "House"
- **THEN** only houses in Bristol with 2 bedrooms priced £100,000-£250,000 are shown
- **AND** the URL contains all active filter parameters

#### Scenario: Visitor clears all filters

- **GIVEN** multiple filters are active on search results
- **WHEN** the visitor clicks "Clear all filters"
- **THEN** all filters are removed
- **AND** the full unfiltered search results are shown
