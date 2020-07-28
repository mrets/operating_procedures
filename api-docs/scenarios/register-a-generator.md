# Register a Generator

## Use Case

Registering a generator in the M-RETS is the first step towards issuing certificates. It is a multi-step process and, once all data has been submit, requries approval by the M-RETS System Administrator.

## Notes About the Entity

Generators are complex entities with many associated objects that must be created before M-RETS is able to approve the generator. Only `approved` generators can issue certificates.

Once a generator is `approved`, there is a subset of fields that if updated will automatically return the generator to a `pending` status and it will again need to be approved by the M-RETS System Administrator. 

## The Basic Call

To initialize a generator in `draft` status, the only required field is the generator `facility_name`.

Upon being initialized, the system will asign a sequential `mrets_id` to the generator. 

```
POST v1/public/generators

{
	"data": {
		"type": "generators",
		"attributes": {
			"facility_name": "Test 1"
		}
	}
}
```

The response will be

```
{
  "data": {
    "id": <generator id>,
    "type": "generators",
    "links": ...,
    "attributes": {
      "name": "Test name",
      "state_province": null,
      "country": null,
      "facility_name": "Facility name",
      "generation_technology": null,
      "commenced_operation_date": null,
      "mrets_id": ...,
      "county": null,
      "additional_owners": null,
      "latitude": null,
      "longitude": null,
      "ownership_type": [],
      "meter_id": null,
      "aggregate_meter": null,
      "aggregating_unit_count": null,
      "primary_generator": null,
      "meter_manufacturer": null,
      "meter_type": null,
      "last_meter_certification": null,
      "nameplate_capacity": null,
      "max_annual_energy": null,
      "reporting_unit_id": null,
      "status": "draft",
      "capacity_factor": null,
      "is_wi_retail_elec_provider": null,
      "retail_elec_providers": null,
      "registration_rights_assign": null,
      "court_regulator_rights_assign": null,
      "uses_hydro_3_year_avg": null,
      "hydro_3_year_avg": null,
      "is_multi_fuel": false,
      "publish_contact": null,
      "wi_rrc_unit_id": null,
      "wi_rrc_program_registration_date": null,
      "control_area_operator": null,
      "biomass_net_generation": null,
      "eia_number": null,
      "approved_as_a_wi_displacement_facility": null,
      "repower_dates_and_added_capacities": [],
      "interconnected_utility": null,
      "created_at": ...,
      "updated_at": ...
    },
    "relationships": ...
  }
}
```

## Creating Associated Objects

### Fuel Sources
Generators are associated with a specific `fuel_source` through a `generator_fuel`. 

To get the list of possible `fuel_sources`:

``` 
GET v1/public/fuel_sources
```

To add the generator_fuel `biomass` to a generator, the call would look like this: 

```
POST v1/public/generator_fuels

{
	"data": {
	  "type": "generator_fuels",
	  "attributes": {
	    "label": "Test 1"
	  },
	  "relationships": {
	    "fuel_source": { "data": { "type": "fuel_sources", "id": "00000000-0000-0000-0000-000000000001"  } },
	    "generator": { "data": { "type": "generators", "id": "15500fff-8b41-478b-acaf-f4e9a3993b80" } }
	  }
	}
}
```

### Contacts
A generator has 3 associated contact objects including the Owner, Operator, and Mailing Address. To create these objects the call would look like this:

```
POST /v1/public/generators/:generator_id/owner
POST /v1/public/generators/:generator_id/operator
POST /v1/public/generators/:generator_id/mailing

Payload Sample:
{
  "data": {
    "type": "contacts",
    "attributes": {
      "name": "Name",
      "street_1": "Street 1",
      "street_2": "Street 2",
      "city": "test",
      "state_province": "MN",
      "postal_code": "12000",
      "country": "United States",
      "phone": "000-111-1234",
      "url": "example.url.domain.com",
      "fax": "000-111-1234",
      "email": "example.email@domain.com",
      "job_title": "Job Title"
    }
  }
}
```

### Eligibilities
A generator can have one or many associated `eligibilities`. 

The full list of possible eligibilities can be retrieved with this call:

```
v1/public/eligibilities
```

To add the `MN` and `ND` eligibilities to a generator:
 
 ```
POST /v1/public/generator_fuels/2dc6c99e-30fe-420e-ad3d-03a8b94c40eb/relationships/eligibilities

{
  "data": [{ "type": "eligibilities", id: {eligib_id} }]
}
```

###
A generator has one reporting entity. This can either be `Self Reporting` or another active organization in the system.

To designate a generators self-reporting:

```
GET /v1/public/generators/00080670-ce1c-4e2d-8a1b-0b97fd4d716f/relationships/reporting_entity

{
  "data": [{ "type": "organizations", id: {owner_org_id} }]
}
```

To designate another organization as the reporting entity:
```
PUT /v1/public/generators/00080670-ce1c-4e2d-8a1b-0b97fd4d716f/relationships/reporting_entity

{
  "data": [{ "type": "organizations", id: {org_id} }]
}
```

## Generator State

As mentioned above, a generator only requires the `name` to be saved in `draft` status. Before a generator can be submit to be reviewed by the M-RETS System Admin, it must have include all required fields (see swagger file for further details on which fiels are requred). To submit a generator for review, change the status to `pending`.

```
PUT v1/public/generators/{org_id}

{
  "data": {
	  "id": "{org_id}", 
	  "type": "generators", 
	  "attributes": {
	  	"status": "active"
	  }
  }
}
```

After it has been successfully reviewed by the M-RETS System Admin, the generator will be updated with a status of `approved` as well as an `effective_date`.


To check the generation history of a generator:

```
GET v1/public/generation_entries?filter[generator_id]={generator_id}
```

