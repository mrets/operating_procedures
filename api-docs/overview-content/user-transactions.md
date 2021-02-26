# User Transactions and Transaction Details

All transactions in the M-RETS are represented by User Transactions and associated Transaction Details. For every transaction that occures, a User Transaction instance is created with general information about the transaction type and recipients if relevant. The User Transaction is also where the status of a transaction is stored. A User Transaction has one or many associated Transaction Details that correspond to each of the Certificate Quantities included in the transaction. For example, if from the UI a user selects three rows of RECs (Certificate Quantities) from the Active Certificates table, and initiates a transaction, the resulting User Transaction would also have three Transaction Details.

## Transaction Types

The M-RETS API supports 3 different types of transactions:
 
* Transferring certificates to another organization (external transaction)
* Transferring certificates to another active account or multiple active accounts (internal transaction)
* Transferring certificates to another tracking system (export)

## Transaction Statuses

After a user initiates a transfer (“Transferor”), the transferred certificates enter a ‘Pending’ state. This effectively “freezes” the certificates and the system will prevent the Transferor from making additional transfers of certificates in Pending status.
 

