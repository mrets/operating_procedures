# Administer a Market

## Use Case

There is one type of certificate transfers:
* A market transfer from one organization to another. User denoting a sale or change in ownership.

## Notes About the Entity

Transfers in the M-RETS system are represented on a basic level by User Transactions and Transaction Details. The User Transaction captures important information about the transfer such as the transaction type, date the transaction was started/completed, and who started/completed the transaction.

A transfer User Transaction could have one or many associated transaction details that represent the individual certificate quantities that were involved in the transaction. So say in the UI, a user were to select 3 rows and complete an Market Transfer, that User Transaction would have three associated Transaction Details.

Market transfers only involve one step. A user initiates a transfer and it will immediately be completed requiring no additional steps.

The market transfer will deposited the certificates on the receiving organization's Purchased account.

## Adding Market Participants

### Drafting a transaction

All transactions are initiated in the same way.

    POST v1/public/user_transactions

##### Example
```json
{
  "data": {
    "type": "user_transactions",
    "attributes": {
      "transaction_type": "market transfer"
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
      "transaction_type": "market transfer",
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

For an market transfer, the transaction type should be `market transfer`.

```json
  "transaction_type": "market transfer"
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

### Selecting Certificates

One or many Certificate are specified. To view what the possible options are, the full list of Certificates with Active Certificate Quantities can be retrieved with this call:

    GET /v1/public/certificate_quantities?filter[status]=active&include=certificate

The available certificates come from the "For Sale" accounts of a participant organization.

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

The destination on an market transfer should one within the participant Organizations of the market. To view what the possible options are, the full list of participant Organizations can be retrieved with this call:

    POST /v1/public/organizations?filter[participates_in_market]=<market program uuid>

Find your Market's program uuid with this call:

    GET /v1/public/programs?filter[is_market]=true

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

The M-RETS platform also sends out email notifications to the both sending organization and receiving organization.

Email notification settings can be viewed and updated in the M-RETS user interface by clicking on the Org in the upper right corner, then navigating to the User table.

### Enqueue Transaction

Once the draft transaction is completed it needs to be enqueued with this call:

    PUT /v1/public/user_transactions/<transaction uuid>/enqueue
##### Response
    Status: 200 OK
