# Register a Generator

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
