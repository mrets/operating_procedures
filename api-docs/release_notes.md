# Release Notes

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
