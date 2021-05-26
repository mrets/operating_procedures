# Release Notes

## May 13, 2020: v1.2.0

Release of part one of our write endpoints. The second and final batch of write endpoints is scheduled or release in June. We excited to have our full API available for use by subscribers.

Note all endpoints are available in our sandbox environment. When an endpoint is deemed ready for a stable release, the endpoint will be made available in production. 

Stable endpoints in this release:

### Entities and Endpoints

#### Accounts
* POST /v1/public/accounts
* PUT /v1/public/accounts/{id}

#### Contacts
* POST /v1/public/contacts
* PUT /v1/public/contacts/{id}

#### Eligibility Bonds
* POST /v1/public/eligibility_bonds 
* DELETE /v1/public/eligibility_bonds/{id} 

#### Generators
* POST /v1/public/generatiors
* PUT /v1/public/generatiors/{id}
* POST /v1/public/generatiors/{id}/document

#### Generator Fuels
* POST /v1/public/generatior_fuels/{id}
* PUT /v1/public/generatior_fuels/{id}
* DELETE /v1/public/generatior_fuels/{id}

#### Organizations
* GET /v1/public/organizations
* GET /v1/public/organizations/{id}

#### Programs
* GET /v1/public/programs
* GET /v1/public/programs/{id}

#### Program Participant Invites
* POST /v1/public/program_participant_invites
* POST /v1/public/program_participant_invites/{id}/cancel


## March 25, 2020: v1.1.0

Release of part 2 of our read endpoints. This release completes the availability of all of our 'GET' endpoints.

Note all endpoints are available in our sandbox environment. When an endpoint is deemed ready for a stable release, the endpoint will be made available in production. 

Stable endpoints in this intial release:

### Entities and Endpoints

#### Public Reports
* GET /v1/public/reports/generators
* GET /v1/public/reports/organizations

#### Certificates
* GET /v1/public/certificates/reports/{time_unit}

#### Eligibilities
* GET /v1/public/eligibilities
* GET /v1/public/eligibilities/{id}

#### Eligibility Bonds
* GET /v1/public/eligibility_bonds

#### Fuel Sources
* GET /v1/public/fuel_types
* GET /v1/public/fuel_types/{id}

#### Fuel Types
* GET /v1/public/fuel_types
* GET /v1/public/fuel_types/{id}

#### Generators
* GET /v1/public/generators
* GET /v1/public/generatiors/{id}

#### Generator Fuels
* GET /v1/public/generatior_fuels/{id}

#### Organizations
* GET /v1/public/organizations
* GET /v1/public/organizations/{id}

#### Programs
* GET /v1/public/programs
* GET /v1/public/programs/{id}

#### Program Participant Invites
* GET /v1/public/program_participant_invites
* GET /v1/public/program_participant_invites/{id}

#### Transaction Details
* GET /v1/public/transactions_details
* GET /v1/public/transactions_details/{id}

#### User Transactions
* GET /v1/public/user_transactions
* GET /v1/public/user_transactions/{id}																										

## February 26, 2020: v1.0.0

Initial release of stable API endpoints! 

Note all endpoints are available in our sandbox environment. When an endpoint is deemed ready for a stable release, the endpoint will be made available in production. 

Stable endpoints in this intial release:

### Entities and Endpoints

#### Public Reports
* GET /v1/public/reports/certificates/by_fuel_type
* GET /v1/public/reports/certificates/by_fuel_source
* GET /v1/public/reports/certificates/by_eligibility
* GET /v1/public/reports/certificates/by_ownership_type
* GET /v1/public/reports/certificates/by_capacity

#### Accounts
* GET /v1/public/accounts
* GET /v1/public/accounts/{id}

#### Certificates
* GET /v1/public/certificates
* GET /v1/public/certificates/{id}

#### Certificate Quantity
* GET /v1/public/certificates_quantities
* GET /v1/public/certificates_quantities/{id}

#### Contacts
* GET /v1/public/contacts
* GET /v1/public/contacts/{id}

#### Generation Entry
* GET /v1/public/generation_entries
* GET /v1/public/generation_entries/{id}

#### Generation Entry Line
* GET /v1/public/generation_entry_lines
* GET /v1/public/generation_entry_lines/{id}

#### Generation Entry Uploads
* GET /v1/public/generation_upload_reports
* GET /v1/public/generation_upload_reports/{id}

#### Resource Types
* GET /v1/public/resource_types
* GET /v1/public/resource_types/{id}

#### Retirement Options
* GET /v1/public/retirement_options
* GET /v1/public/retirement_options/{id}

#### Users
* GET /v1/public/users
* GET /v1/public/users/{id}
