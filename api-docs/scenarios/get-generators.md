# Get Generators 

## Use Case

A common task for many users of the M-RETS is viewing generator information.

## Notes About the Entity

A generator is a complex entity including many relationships to other objects the system.

## The Basic Call

```
v1/public/
```

## Filters

Common filters that would be applied to generators could include the `fuel type`, `state_province`, or the `eligibility` filters. To replicate the table found in the M-RETS under the Projects tab, you would apply the `active` filter.

```
v1/public/
```

## Including Relationships

The relationships available with this call include:

* Generator Fuels
* Reporting Entity
* Owner (Contact)
* Operator (Contact)
* Mailing (Contact)
* Issue to Account

To receive the additional associated information that can be viewed in the Projects table found in the M-RETS under the Active Projects tab, it would be helpful to include the Generator Fuel and the Reporting Entity.

```
v1/public/
```

## Sorting Results

And let's say we want to view a list of Generators in order by nameplate capacity.

```
v1/public/
```

## Other Use Case Examples

Other things you may want to do with this endpoint could include:

View all of your draft generators:

```
v1/public/
```

View all of your wind generators:

```
v1/public/
```

View all of your self-reported generators:

```
v1/public/
```

View all of your generators with the MN eligibility:

```
v1/public/
```

View all of your generators located in Iowa:

```
v1/public/
```

## Notes on Pagination / Limits / Permissions

The M-RETS API by default returns paginated results of 25 records. With a maximun of 1000 records.

Depending on if your organization owns a generator or not, different information may be returned. If you are seeking to view the details of a generator that your organization does not own, the data returned will be limited to only the data in our system that is classified as public.