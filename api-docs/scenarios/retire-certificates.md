# Retire Certificates

## Use Case

Certificates are retired when the owner wants to make some kid of environmental claim. M-RETS supports a variety of Retirement Types and Reasons.  

## Notes About the Entity

Retirements in the M-RETS system are represented on a basic level by User Transactions and Transaction Details. The User Transaction captures important information about the retirement such as the transaction type, date the transaction was started/completed, who started/completed the transaction, and important details related to the retirement.

A retirement User Transaction could have one or many associated transaction details that represent the individual certificate quantities that were involved in the retirement. So say in the UI, a user were to select 3 rows to be retired, that User Transaction would have three associated Transaction Details.

A Retirement Transaction only involve one step. A user initiates a retirement and it will immediately be completed requiring no additional steps.


## Initiating an Retirement

### Selecting Certificates

All transactions are initiated in the same way. One or many Certificate Quantities are specified.

[example]


### Specifying the Transaction Type

For an retirement, the transaction type should be `retirement`.

[show example]

### Specifying the Retirement Account

The destination on an retirement should be a Retirement Account within the same organization. To view what the possible options are, the full list of Retirement Accounts can be retrieved with this call:

[example]

Then select a Retirement Account and include it in a post call like this:

[example]

## Initiating an External Transfer

### Selecting Certificates

All transactions are initiated in the same way. One or many Certificate Quantities are specified.

[example]


### Specifying the Transaction Type

For an external transfer, the transaction type should be `extneral-transaction`.

[show example]

### Specifying the Retirement Account

The destination for an external transfer should be another Active Organization within the M-RETS System. To view what the possible options are, the full list of Active Organizations can be retrieved with this call:

[example]

### Specifying the Retirement Options

To view valid retirement options, this call can be used:

[example]

[Explain how users should use the retirement options to construct valid a valid retirement]

The full call to initiate the transaction would look like this:

[example]

The success response would look like this:

[example]

The M-RETS platform also sends out email notifications to the both sending organization and destination organization. 

Email notification settings can be viewed and updated in the M-RETS user interface by clicking on the Org in the upper right corner, then navigating to the User table.


## Notes on Response Codes and Call Limits

[Anything we should add?]