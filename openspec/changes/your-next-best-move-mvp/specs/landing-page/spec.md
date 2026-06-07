## ADDED Requirements

### Requirement: Location search with sale/rent toggle

The landing page SHALL present a prominent search bar with a location field and sale/rent toggle so visitors can start searching immediately.

#### Scenario: Visitor searches for properties to buy

- **GIVEN** a visitor lands on the homepage
- **WHEN** they type a location (e.g. "Manchester") and select "For Sale"
- **AND** they submit the search
- **THEN** they are taken to the property search results page for that location, filtered to sale listings

#### Scenario: Visitor searches for properties to rent

- **GIVEN** a visitor lands on the homepage
- **WHEN** they type a location and select "To Rent"
- **AND** they submit the search
- **THEN** they are taken to the property search results page for that location, filtered to rental listings

#### Scenario: Visitor submits search with an empty location

- **GIVEN** a visitor is on the homepage
- **WHEN** they submit the search without entering a location
- **THEN** they are shown a validation message asking them to enter a location
- **AND** they remain on the landing page
