# Register a Generator

## Use Case

Registering a generator in the M-RETS is the first step towards issuing certificates. It is a multi-step process and, once all data has been submit, requries approval by the M-RETS System Administrator.

## Notes About the Entity

Generators are complex entities with many associated objects that must be created before M-RETS is able to approve the generator. Only `approved` generators can issue certificates.

Once a generator is `approved`, there is a subset of fields that if updated will automatically return the generator to a `pending` status and it will again need to be approved by the M-RETS System Administrator. 

## The Basic Call

To initialize a generator in `draft` status, the only required field is the generator `name`.

Upon being initialized, the system will asign a sequential `mrets_id` to the generator. 

```
v1/public/
```

## Creating Associated Objects

### Fuel Types
Generators are associated with a specific `fuel_type` through a `generator_fuel`. 

To get the list of possible `fuel_types`:

``` 
v1/public/
```

To add the generator_fuel `biomass` to a generator, the call would look like this: 

```
v1/public/
```

### Contacts
A generator has 3 associated contact objects including the Owner, Operator, and Mailing Address. To create these objects the call would look like this:

```
v1/public/
```

### Eligibilities
A generator can have one or many associated `eligibilities`. 

The full list of possible eligibilities can be retried with this call:

```
v1/public/
```

To add the `MN` and `ND` eligibilities to a generator: 

###
A generator has one reporting entity. This can either be `Self Reporting` or another active organization in the system.

To designate a generatoras self-reporting:

```
v1/public/
```

To designate another organization as the reporting entity:
```
v1/public/
```

## Generator State

As mentioned above, a generator only requires the `name` to be saved in `draft` status. Before a generator can be submit to be reviewed by the M-RETS System Admin, it must have include all required fields (see swagger file for further details on which fiels are requred). To submit a generator for review, change the status to `pending`.

```
v1/public/
```

After it has been successfully reviewed by the M-RETS System Admin, the generator will be updated with a status of `approved` as well as an `effective_date`.

_______________

```
POST v1/public/generators
```

With request body

```json
{
  "data":{
    "type": "generators",
    "attributes": {
      "name": "Test name",
      "facility_name": "Facility name"
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

Add a Generator Fuel to the newly created Generator

```
POST v1/public/generator_fuels
```

With request body, using the Generator's id from the previous request

```
{
  "data": {
    "type": "generator_fuels",
    "attributes": {
      "label": "Fuel Label"
    },
    "relationships": {
      "generator": {
        "data": {
          "type": "generators",
          "id": <generator id>
        }
      },
      "fuel_source": {
        "data": {
          "type": "fuel_sources",
          "id": <fuel source id>
        }
      }
    }
  }
}
```
