| Name                          | Data Field                        | Description                                                                                                                                   |
|-------------------------------|-----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
|Transaction Type|transaction_type|'issuance': <br> 'withdraw': <br> 'issuance_rollback': <br> 'internal_transfer': <br> 'external_transfer': <br> 'conversion': <br> 'retirement': <br> 'export': <br> 'unretirement': <br> 'import': <br> 'transfer': <br> 'market_transfer':|
|Started At|started_at| The timestamp created when a transaction was initiated|
|Ended At|ended_at|The timestamp created when a transaction was completed.|
|Status|status|'complete': <br>'pending': <br>'rejected': <br>'withdrawn': <br>'expired': <br>'failed': <br>'enqueued': <br>'draft': <br>|
|Notes|notes|Any special comments included on the transaction to clarify purpose or any special steps taken by the administrator.|
|Action|action||
|Retired To|retired_to|State or province for which a retirement occured.|
|Compliance Period|compliance_period|The year for which a certificate was retired.|
|Retirement Type|retirement_type|The primary classification of a retirement.|
|Retirement Reason|retirement_reason|The sub classification of a retirement.|
|Is Multi Account Destiantion?|is\_multi\_account\_destination|Flag for a transaction to multiple internal accounts|
|User|relationship: user|The user that initializes a transaction.|
|Ended By User| relationship: ended\_by\_user       | The user that completes a transaction.|
|Transaction Details| relationship: transaction_details | The associated quantities included in the transaction. Includes the specific start and end serial numbers for specifc certificate quantities. |
|Retirement Options| relationship: retirement_options  | The associated retirement information. Only relevant for retirement transactions.|
