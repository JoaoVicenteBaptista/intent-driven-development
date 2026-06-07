## ADDED Requirements

### Requirement: Enquiry form on the property detail page

A visitor SHALL be able to send an enquiry about a specific property using a form on the detail page.

#### Scenario: Visitor submits a valid enquiry

- **GIVEN** a visitor is viewing a property detail page
- **WHEN** they fill in their name, email, and a message
- **AND** they submit the form
- **THEN** a success message is shown confirming the enquiry was sent
- **AND** the form is cleared

#### Scenario: Visitor submits an enquiry with missing name

- **GIVEN** a visitor is viewing a property detail page
- **WHEN** they submit the form without entering a name
- **THEN** a validation message is shown asking for their name
- **AND** the enquiry is not submitted

#### Scenario: Visitor submits an enquiry with an invalid email

- **GIVEN** a visitor is viewing a property detail page
- **WHEN** they enter an invalid email address (e.g. "not-an-email")
- **AND** they submit the form
- **THEN** a validation message is shown asking for a valid email address
- **AND** the enquiry is not submitted

#### Scenario: Visitor submits an enquiry with an empty message

- **GIVEN** a visitor is viewing a property detail page
- **WHEN** they submit the form without entering a message
- **THEN** a validation message is shown asking for a message
- **AND** the enquiry is not submitted

### Requirement: Enquiry form is accessible without login

The contact form MUST be open to all visitors — no authentication SHALL be required.

#### Scenario: Visitor accesses the enquiry form without logging in

- **GIVEN** a visitor is not authenticated
- **WHEN** they navigate to any property detail page
- **THEN** the enquiry form is visible and functional
- **AND** no login prompt is shown

### Requirement: Enquiry references the property being viewed

The enquiry SHALL be associated with the property the visitor was viewing.

#### Scenario: Enquiry includes the property context

- **GIVEN** a visitor is viewing "123 Acacia Avenue"
- **WHEN** they submit an enquiry
- **THEN** the submission includes a reference to "123 Acacia Avenue" so the agent knows which property the enquiry is about
