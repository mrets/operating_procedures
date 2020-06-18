# Get REC Inventory

## Use Case

A common task for most of users of the M-RETS is viewing their Active REC inventory. 

## Notes About the Entity

RECs in the M-RETS system are represented on a basic level by the Certificate Quantity and (capital "C") Certificate objects. A Certificate is created upon issuance and contains information consistent with the whole batch of certificates, such as the vintage, generator, and fuel type. A Certificate is generally considered immutable after creation. A single Certificate Quantity associated with the Certificate is also created upon issuance. This represents all of the certificates that were created in that issuance and contains key information about the start and end serial numbers. During the lifetime of this Certificate Quantity it may be split during the transaction process an unlimited number of times. 

For example, say we have a Certificate Quantity representing 100 certificates and 50 of them are transfered to another Organization. We would go from having one Certificate Quantity representing all 100 certificates owned by Organization A to two Certificate Quantities, one in Organization A and one in Organization B, each representing 50 certificates. 

## The Basic Call

[example]


## Filters

The most common filters that would be applied to certificate quantities would likely be the `status` filter. To replicate the table found in the M-RETS under the Active Certificate tab, you would apply the `active` filter.

[example]

## Including Relationships

The relationships available with this call include:

* Account
* Certificate
* Organization
* Transaction Detail

To receive the additional associated information that can be viewed in the Active Certificates table found in the M-RETS under the Active Certificate tab, it would be helpful to include the Account and the Certificate.

[example]

## Sorting Results

And let's say we want to view these certificates in order by when they were created.

[example]


## Other Use Case Examples

Other things you may want to do with this endpoint could include:

View all of your retired RECs:

[example]

View all of your active RECs from a specific vintage, say Jan-Dec of 2019.

[example]

View all of your retired RECs retired for the MN RPS in 2018.  

[example]

View all of your Active RECs in a specific Account named "Test Account".

[example]


## Notes on Pagination / Limits / Permissions

The M-RETS API by default returns paginated results of [x] records.

 
