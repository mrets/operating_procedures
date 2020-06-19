# Get Transaction History

## Use Case

The Transaction History is tab in the M-RETS system is a reverse chronological log of all activities including issuances, issuance rollbacks, internal transfers, external transfers, exports, imports, and retirements. Filters are provided to drill into this data by a wide array of data attributes. A user of the M-RETS system would look at the Transaction History table for a variety of reasons that could include viewing recent issuances, checking on status of transfers, or reviewing retirements from the past year.

## Notes About the Entity

Events in the M-RETS system are represented on a basic level by User Transactions and Transaction Details. The User Transaction captures important information about the transaction such as the transaction type, date the transaction was started/completed, who started/completed the transaction, or, if the User Transaxction  was a retirement, it could contain important information about the claim made by the retirement.

A User Transaction could have one or many associated transaction details that represent the individual certificate quantities that were involved in the transaction. So say in the UI, a user were to select 3 rows and complete and Internal Transfer, that User Transaction would have three associated Transaction Details.

## The Basic Call

In the M-RETS System, the Transaction History table is a list of Transaction Details.

```
v1/public/transaction_details
```

## Filters

The most common filters that would be applied to Transaction Details would likely be the `status` filter. To replicate the table found in the M-RETS under the Active Certificate tab, you would apply the `complete` filter, or if you were trying to view transactions that had not been completed, the `pending` filter would be applied.

```
v1/public/transaction_details?filter[status]=complete
```

## Including Relationships

The relationships available with this call include:

* Certificate
* From Account's Organization
* To Account
* User Transaction

To receive the additional associated information that can be viewed in the Transaction History table found in the M-RETS, it would be helpful to include all of these optins.

```
v1/public/transaction_details?include=to_account,certificate,from_account.organization,user_transaction
```

## Sorting Results

And let's say we want to view these certificates in order by when they were created.

```
v1/public/transaction_details?sort=created_at
```

## Other Use Case Examples

Other things you may want to do with this endpoint could include:

View all of your pending Transactions:
```
v1/public/transaction_details?filter[transaction_type]=retirement
```

View all of your issued RECs from a specific vintage, say Jan-Dec of 2019.
```
v1/public/transaction_details?filter[transaction_type]=issuance&filter[vintage_start]=2019-01-01&filter[vintage_end]=2019-12-31
```

View all of your incoming transactions from a specific Organization id "00000000-0000-0000-0000-000000000001".

```
v1/public/transaction_details?filter[from_organization]=00000000-0000-0000-0000-000000000001
```

## Notes on Pagination / Limits / Permissions

The M-RETS API by default returns paginated results of 25 records. With a maximun of 100 records.

For external transactions, the API will not return the `to_account` field for another organization. This is information M-RETS does not expose.
