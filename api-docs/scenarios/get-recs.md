# Get REC Inventory

## Use Case

A common task for most of users of the M-RETS is viewing their Active REC inventory.

## Notes About the Entity

RECs in the M-RETS are represented on a basic level by the Certificate Quantity and (capital "C") Certificate objects. A Certificate is created upon issuance and contains information consistent with the whole batch of certificates, such as the vintage, generator, and fuel type. A Certificate is generally considered immutable after creation. A single Certificate Quantity associated with the Certificate is also created upon issuance. This represents all of the certificates that were created in that issuance and contains key information about the start and end serial numbers. During the lifetime of this Certificate Quantity it may be split during the transaction process an unlimited number of times.

For example, say we have a Certificate Quantity representing 100 certificates and 50 of them are transfered to another Organization. We would go from having one Certificate Quantity representing all 100 certificates owned by Organization A to two Certificate Quantities, one in Organization A and one in Organization B, each representing 50 certificates.

## The Basic Call

```
v1/public/certificate_quantities
```

## Filters

The most common filters that would be applied to certificate quantities would likely be the `status` filter. To replicate the table found in the M-RETS under the Active Certificate tab, you would apply the `active` filter.

```
v1/public/certificate_quantities?filter[status]=active
```

## Including Relationships

The relationships available with this call include:

* Account
* Certificate
* Transaction Detail

To receive the additional associated information that can be viewed in the Active Certificates table found in the M-RETS under the Active Certificate tab, it would be helpful to include the Account and the Certificate.

```
v1/public/certificate_quantities?include=account,certificate,transaction_detail
```

## Sorting Results

And let's say we want to view these certificates in order by when they were created.

```
v1/public/certificate_quantities?sort=created_at
```

## Other Use Case Examples

Other things you may want to do with this endpoint could include:

View all of your retired RECs:

```
v1/public/certificate_quantities?filter[status]=retired
```

View all of your active RECs from a specific vintage, say Jan-Dec of 2019.

```
v1/public/certificate_quantities?filter[status]=active&filter[vintage_start]=2019-01&filter[vintage_end]=2019-12
```

View all of your retired RECs retired for the MN RPS in 2018.

```
v1/public/certificate_quantities?filter[status]=retired&filter[retirement_type]=State/Provincial Portfolio Standard&filter[retired_to]=MN&filter[retirement_period_start]=2018-01-01&filter[retirement_period_end]=2018-12-31
```

View all of your Active RECs in a specific Account id "00000000-0000-0000-0000-000000000001".

```
v1/public/certificate_quantities?filter[status]=active&filter[account_id]=00000000-0000-0000-0000-000000000001
```

View all of your Active RECs with a specific Fuel Type id "00000000-0000-0000-0000-000000000001".

```
v1/public/certificate_quantities?filter[status]=active&filter[fuel_type]=00000000-0000-0000-0000-000000000001
```

View all of your Active RECs with a specific Eligibility with slug "hydro".

```
v1/public/certificate_quantities?filter[status]=active&filter[eligibility]=hydro
```

## Notes on Pagination / Limits / Permissions

The M-RETS API by default returns paginated results of 25 records. With a maximun of 1000 records.

## For Market Administrator Organization

Market Administrator Organizations do not own generators but have visibility on the participant organization's generators, given those generators issued recs that are for sell.
