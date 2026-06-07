## ADDED Requirements

### Requirement: Photo gallery with carousel navigation

The detail page SHALL display property photos in a browsable carousel.

#### Scenario: Visitor views the first photo

- **GIVEN** a property listing has multiple photos
- **WHEN** a visitor opens the property detail page
- **THEN** the first photo is displayed prominently
- **AND** dot indicators show how many photos are available

#### Scenario: Visitor navigates to the next photo

- **GIVEN** the visitor is viewing photo 1 of 5
- **WHEN** they click the next arrow or swipe
- **THEN** photo 2 is displayed
- **AND** the active dot indicator updates

#### Scenario: Visitor selects a specific photo via dot indicator

- **GIVEN** the visitor is viewing a property with 5 photos
- **WHEN** they click on the third dot indicator
- **THEN** photo 3 is displayed

#### Scenario: Property has only one photo

- **GIVEN** a property listing has a single photo
- **WHEN** a visitor opens the property detail page
- **THEN** the photo is displayed without navigation arrows or dot indicators

### Requirement: Key facts display

The detail page SHALL show essential property facts prominently.

#### Scenario: Visitor views key property facts

- **GIVEN** a property listing has price £250,000, 3 bedrooms, 2 bathrooms, and 1,200 sq ft
- **WHEN** a visitor opens the property detail page
- **THEN** the price, bedroom count, bathroom count, and square footage are displayed in a key facts section

#### Scenario: Property has no square footage data

- **GIVEN** a property listing has no square footage recorded
- **WHEN** a visitor opens the property detail page
- **THEN** the key facts section omits square footage without showing a blank or error

### Requirement: Property description

The detail page SHALL display the full text description of the property.

#### Scenario: Visitor reads the property description

- **GIVEN** a property has a written description
- **WHEN** a visitor opens the property detail page
- **THEN** the full description is displayed in a readable format

### Requirement: Floorplan image

The detail page SHALL display a floorplan image for the property when available.

#### Scenario: Visitor views the floorplan

- **GIVEN** a property listing includes a floorplan image
- **WHEN** a visitor opens the property detail page
- **THEN** the floorplan is displayed with a label indicating it is the floorplan

#### Scenario: Property has no floorplan

- **GIVEN** a property listing does not include a floorplan image
- **WHEN** a visitor opens the property detail page
- **THEN** the floorplan section is omitted without showing a broken image

### Requirement: EPC rating display

The detail page SHALL show the property's Energy Performance Certificate rating as a visual graphic when available.

#### Scenario: Visitor views the EPC rating

- **GIVEN** a property has an EPC rating of "B"
- **WHEN** a visitor opens the property detail page
- **THEN** an EPC rating graphic is displayed showing the "B" rating on the A-G scale

#### Scenario: Property has no EPC rating

- **GIVEN** a property listing has no EPC rating recorded
- **WHEN** a visitor opens the property detail page
- **THEN** the EPC section is omitted without showing an error
