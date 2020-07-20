# Get Generation History

## Use Case

The Generation History table in the M-RETS is a log of all generation entries in reverse chronological order. This information is helpful in understanding the how much energy a generator produced and the resulting issuances that occured.

## Notes About the Entity



## The Basic Call

```
v1/public/
```

## Filters

The most common filters that would be applied to generation entries would likely be the `status` filter. To view only generation entries that had resulted in the issuance of certificates, you would apply the `issued` filter.

```
v1/public/
```

## Including Relationships

The relationships available with this call include:

* Generator

To receive the additional associated information that can be viewed in the Generation History table, includ the Generator relationship.

```
v1/public/
```

## Sorting Results

And let's say we want to view generation entries as they would appear in the Generation Entry log, in reverse order by when they were created.

```
v1/public/
```

## Other Use Case Examples

Other things you may want to do with this endpoint could include:

View all of generation entries from a specific generator:

```
v1/public/
```

View all of your generation entries from January - December of 2019:

```
v1/public/
```

View all of your generation entries from a specific fuel type:

```
v1/public/
```



## Notes on Pagination / Limits / Permissions

The M-RETS API by default returns paginated results of 25 records. With a maximun of 1000 records.