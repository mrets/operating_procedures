# Get Generation History

## Use Case

The Generation History table in the M-RETS is a log of all generation entries in reverse chronological order. This information is helpful in understanding the how much energy a generator produced and the resulting issuances that occured.

## Notes About the Entity

Generation Entries and Generation Entry Lines are used to model generation data in the M-RETS.  In the M-RETS UI, The Generation Entry Log is a list of Generation Entry Lines. Each time M-RETS receives generation data for a generator, the date and quantity of MWhs is posted to the Generation Log.

The Generation Entry could have multiple Generation Entry Lines if, for example, a CSV upload was used to submit the data and it contained multiple lines of generation corresponding to different Generators.

## The Basic Call

```
GET v1/public/generation_entries
```

## Filters

The most common filters that would be applied to generation entries would likely be the `status` filter. To view only generation entries that had resulted in the issuance of certificates, you would apply the `issued` filter.

```
GET v1/public/generation_entries?filter[status]=issued
```

## Including Relationships

The relationships available with this call include:

* Generator

To receive the additional associated information that can be viewed in the Generation History table, include the Generator relationship.

```
GET v1/public/generation_entries?include=generator
```

## Sorting Results

And let's say we want to view generation entries as they would appear in the Generation Entry log, in reverse order by when they were created.

```
GET v1/public/generation_entries?sort=-created_at
```

## Other Use Case Examples

Other things you may want to do with this endpoint could include:

View all of generation entries from a specific generator:

```
GET v1/public/generation_entries?filter[generator_id]={generator_id}
```

View all of your generation entries from January - December of 2019:

```
GET v1/public/generation_entries?filter[generation_period_start_start]=2019-01-01&filter[generation_period_start_end]=2019-12-01
```

View all of your generation entries from a specific fuel type:

```
GET v1/public/generation_entries?filter[fuel_type]={fuel_type_id}
```



## Notes on Pagination / Limits / Permissions

The M-RETS API by default returns paginated results of 25 records. With a maximun of 1000 records.
