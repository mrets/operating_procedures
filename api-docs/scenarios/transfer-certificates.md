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

### Drafting a transaction

All transactions are initiated in the same way.

    POST v1/public/user_transactions

##### Example
```json
{
    "data": {
        "type": "user_transactions",
        "attributes": {
            "transaction_type": "internal transfer"
        }
    }
}
```
##### Response
    Status: 201 Created
```json
{
  "data": {
      "id": "<transaction uuid>",
      "type": "user_transactions",
      "links": {...},
      "attributes": {
        "transaction_type": "internal transfer",
        "status": "draft",
        "created_at": "2020-01-01T00:00:00Z",
        "updated_at": "2020-01-01T00:00:00Z",
        "retirement_type": null,
        "started_at": null,
        "ended_at": null,
        "compliance_period": null,
        "retired_to": null,
        "notes": null,
        "retired_quarter": null,
        "retirement_reason": null
      },
      "relationships": [...]
  }
}
```

### Specifying the Transaction Type

For an internal transfer, the transaction type should be `internal transfer`.

```json
  "transaction_type": "internal transfer"
```

### Creating Transaction Details

Transaction Details can be created into that draft User Transaction.

    POST v1/public/transaction_details

##### Example
```json
{
  "data": {
    "type": "transaction_details",
    "attributes": {
      "serial_number_start": 1,
      "serial_number_end": 100
    },
    "relationships": {
      "user_transaction": {
        "data": {
          "type": "user_transactions",
          "id": "<transaction uuid>"
        }
      },
      "from_account": {
        "data": {
          "type": "accounts",
          "id": "<from account uuid>"
        }
      },
      "to_account": {
        "data": {
          "type": "accounts",
          "id": "<to account uuid>"
        }
      },
      "certificate": {
        "data": {
          "type": "certificates",
          "id": "<certificate uuid>"
        }
      }
    }
  }
}
```
##### Response
    Status: 201 Created
```json
{
  "data": {
    "id": "...",
    "type": "transaction_details",
    "links": {...},
    "attributes": {
      "serial_number_start": 1,
      "serial_number_end": 100,
      "quantity": 100,
      "created_at": "2020-01-01T00:00:00Z",
      "updated_at": "2020-01-01T00:00:00Z"
    },
    "relationships": [...]
  }
}
```

### Selecting Certificates

One or many Certificate are specified. To view what the possible options are, the full list of Certificates with Active Certificate Quantities can be retrieved with this call:

    GET /v1/public/certificate_quantities?filter[status]=active&include=certificate

##### Response
    Status: 200 OK
```json
{
  "data": [
    {
        "id": "...",
        "type": "certificate_quantities",
        "links": {...},
        "attributes": {
            "quantity": 100,
            "serial_number_end": 100,
            "serial_number_start": 1,
            "serial_number_base": "...",
            "rrc_quantity": "...",
            "status": "active",
            "created_at": "2020-01-01T00:00:00Z",
            "updated_at": "2020-01-01T00:00:00Z"
        },
        "relationships": {
            "account": {...},
            "certificate": {
                "links": {...},
                "data": {
                    "type": "certificates",
                    "id": "<certificate uuid>"
                }
            },
            "transaction_detail": {...}
        }
    },
    {...}
  ]
}
```

Then select an Certificate and include it in a post call like this:

```json
"certificate": {
  "data": {
    "type": "certificates",
    "id": "<certificate uuid>"
  }
}
```

### Specifying the Receiving Party

The destination on an internal transfer should one or many Active Accounts within the same organization. To view what the possible options are, the full list of Open Active Accounts can be retrieved with this call:

    POST /v1/public/accounts?filter[account_type]=active&filter[status]=open

##### Response
    Status: 200 OK
```json
{
  "data": [
    {
      "id": "<account uuid>",
      "type": "accounts",
      "links": {...},
      "attributes": {
          "name": "Bangor",
          "status": "open",
          "account_type": "active",
          "created_at": "2020-01-01T00:00:00Z",
          "updated_at": "2020-01-01T00:00:00Z"
      },
      "relationships": [...]
    },
    ...
  ]
}
```

Then select an Active Account and include it in a post call like this:

```json
"to_account": {
  "data": {
    "type": "accounts",
    "id": "<account uuid>"
  }
}
```

## Initiating an External Transfer

All transactions are initiated in the same way. See [Drafting a transaction](#drafting-a-transaction)

### Specifying the Transaction Type

For an external transfer, the transaction type should be `external transfer`.

```json
  "transaction_type": "external transfer"
```

### Creating Transaction Details

Transaction Details can be created into that draft User Transaction.

    POST v1/public/transaction_details

##### Example
```json
{
  "data": {
    "type": "transaction_details",
    "attributes": {
      "serial_number_start": 1,
      "serial_number_end": 100
    },
    "relationships": {
      "user_transaction": {
        "data": {
          "type": "user_transactions",
          "id": "<transaction uuid>"
        }
      },
      "from_account": {
        "data": {
          "type": "accounts",
          "id": "<from account uuid>"
        }
      },
      "to_organization": {
        "data": {
          "type": "organizations",
          "id": "<to organization uuid>"
        }
      },
      "certificate": {
        "data": {
          "type": "certificates",
          "id": "<certificate uuid>"
        }
      }
    }
  }
}
```
##### Response
    Status: 201 Created
```json
{
  "data": {
    "id": "...",
    "type": "transaction_details",
    "links": {...},
    "attributes": {
      "serial_number_start": 1,
      "serial_number_end": 100,
      "quantity": 100,
      "created_at": "2020-01-01T00:00:00Z",
      "updated_at": "2020-01-01T00:00:00Z"
    },
    "relationships": [...]
  }
}
```

### Specifying the Receiving Party

The destination for an external transfer should be another Active Organization within the M-RETS System. To view what the possible options are, the full list of Organizations can be retrieved with this call:

    GET /v1/public/organizations
##### Response
    Status: 200 OK
```json
{
  "data": [
    {
      "id": "<organization uuid>",
      "type": "organizations",
      "links": {...},
      "attributes": {
        "name": "...",
        "resource_type": "rec",
        "account_type": "...",
        "organization_type": "...",
        "organization_subtype": "...",
        "created_at": "2020-01-01T00:00:00Z",
        "updated_at": "2020-01-01T00:00:00Z"
      },
      "relationships": [...]
    },
    {...}
  ]
}
```

Then select an Organization and include it in a post call like this:

```json
"to_organization": {
  "data": {
    "type": "organizations",
    "id": "<organization uuid>"
  }
}
```

The M-RETS platform also sends out email notifications to the both sending organization and destination organization.

Email notification settings can be viewed and updated in the M-RETS user interface by clicking on the Org in the upper right corner, then navigating to the User table.

### Enqueue Transaction

Once the draft transaction is completed it needs to be enqueued with this call:

    PUT /v1/public/user_transactions/<transaction uuid>/enqueue
##### Response
    Status: 200 OK

## Completing an External Transfer

To view any pending transfers that need action, the call would look like this:

    GET /v1/public/user_transactions?filter[status]=pending
##### Response
    Status: 200 OK

Once identifying a transaction that requires action, below are the possible ways an external transfer can be completed.

##### Response
    Status: 200 OK

### Accepting an External Transfer

    PUT /v1/public/user_transactions/<transaction uuid>/accept
##### Response
    Status: 200 OK

### Withdrawing an External Transfer

    PUT /v1/public/user_transactions/<transaction uuid>/withdraw
##### Response
    Status: 200 OK

### Rejecting an External Transfer

    PUT /v1/public/user_transactions/<transaction uuid>/reject
##### Response
    Status: 200 OK
