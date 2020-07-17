# Submit Generation

## Use Case

Any registered generator is eligible to issue certificates. Generation is usually submit monthly for large generators and can be submit annually for generators under 150kW.

M-RETS issues 1 Renewable Energy Cerificate for each MWh submit. 

## Notes About the Entity

Submittal of generation occures through the creation of a generation entry. The system runs a series of validation generation entries and automatically issues certifiates if all validations pass successfully.

## The Basic Call

To create a generation entry:

```
v1/public/
```

Here is an example with multiple multiple `fuel_types`:

```

```

# Validations

Some of the validations in place include:

* Generation more than 62 days old must be approved by the System Admin
* There can't be any temporal gaps in the submittal of generation.
* Generation can't exceed the theoretical limits of a generator based on the nameplate capacity and capapcity factor.

Here is an example response if a generation entry is created after the 62 day window.

```

```