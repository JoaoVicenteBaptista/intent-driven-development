## ADDED Requirements

### Requirement: Location-based property search with pagination

A visitor SHALL be able to search for properties by location and receive paginated results displayed as property cards.

#### Scenario: Search returns matching properties

- **GIVEN** the mock data contains properties in "Brighton"
- **WHEN** a visitor searches for "Brighton"
- **THEN** they see a list of property cards for Brighton
- **AND** each card shows the property image, price, address, bedroom count, and sale/rent type

#### Scenario: Search returns no results

- **GIVEN** the mock data contains no properties in "Atlantis"
- **WHEN** a visitor searches for "Atlantis"
- **THEN** they see a message indicating no properties were found
- **AND** they are offered a link back to the homepage

#### Scenario: Results are paginated

- **GIVEN** there are 50 properties matching a search in "London"
- **AND** the page size is 12
- **WHEN** a visitor views the first page of results
- **THEN** they see 12 property cards
- **AND** they see pagination controls showing there are multiple pages

#### Scenario: Visitor navigates to the next page of results

- **GIVEN** a search for "London" returns 50 properties across 5 pages
- **AND** the visitor is on page 1
- **WHEN** they click "Next"
- **THEN** they see page 2 with the next 12 properties
- **AND** the URL includes `?page=2`
