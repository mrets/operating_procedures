# Transfer Certificates

## Use Case

There are three main types of certificate transfers:
* An internal transfer to another account within the same organization
* An external transfer to another organization. User denoting a sale or change in ownership.
* An internal transfer to multiple accounts within the same organization. This type of transfer can be done by specifying how a quantity should be split based on percent. 

## Notes About the Entity

Transfers in the M-RETS system are represented on a basic level by User Transactions and Transaction Details. The User Transaction captures important information about the transfer such as the transaction type, date the transaction was started/completed, and who started/completed the transaction.

A transfer User Transaction could have one or many associated transaction details that represent the individual certificate quantities that were involved in the transaction. So say in the UI, a user were to select 3 rows and complete an Internal Transfer, that User Transaction would have three associated Transaction Details.

Internal transfers only involve one step. A user initiates a transfer and it will immediately be completed requiring no additional steps.

An external transfer has two steps. The transfer is initated, then it must be accepted by the receiving organization. Other actions that could occure during an external transfer include a "withdraw", meaning the sending organization interrupt the transaction before it is completed and the certificates would return to their original account. The receiving organization could also choose to "reject" the transfer, meaning that they choose not to accept the transfer and the certificates would again return to the sender's organization and be deposited into their origin account.


## Initiating an Internal Transfer

### Selecting Certificates

All transactions are initiated in the same way. One or many Certificate Quantities are specified.

[example]


### Specifying the Transaction Type

For an internal transfer, the transaction type should be `internal-transaction`.

[show example]

For an internal transfer to multiple accounts, the transaction type should be `.....`. 

[show example]

### Specifying the Receiving Party

The destination on an internal transfer should one or many Active Accounts within the same organization. To view what the possible options are, the full list of Active Accounts can be retrieved with this call:

[example]

Then select an Active Account and include it in a post call like this:

[single account example]

For multiple accounts it would look like this:

[multi account example]

## Initiating an External Transfer

### Selecting Certificates

All transactions are initiated in the same way. One or many Certificate Quantities are specified.

[example]


### Specifying the Transaction Type

For an external transfer, the transaction type should be `extneral-transaction`.

[show example]

### Specifying the Receiving Party

The destination for an external transfer should be another Active Organization within the M-RETS System. To view what the possible options are, the full list of Active Organizations can be retrieved with this call:

[example]

The full call to initiate the transaction would look like this:

[example]

The success response would look like this:

[example]

The M-RETS platform also sends out email notifications to the both sending organization and destination organization. 

Email notification settings can be viewed and updated in the M-RETS user interface by clicking on the Org in the upper right corner, then navigating to the User table.


## Completing an External Transfer

To view any pending transfers that need action, the call would look like this:

[example]

Once identifying a transaction that requires action, below are the possible ways an external transfer can be completed.

### Accepting an External Transfer

[example]

### Withdrawing an External Transfer

[example]

### Rejecting an External Transfer

[example]


## Notes on Response Codes and Call Limits

[Anything we should add?]

 