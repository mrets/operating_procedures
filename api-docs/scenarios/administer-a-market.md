# Administer a Market

## Use Case

The Market Administrator functionality was desinged to support third parties who would like to provide a spot market service to users on the M-RETS.

To read more about the Market Admin feature, see our help article [here](link). To Register as Market Admin, please see our help article [here](link) and contact the System Admin.

Market Administrators have several endpoints designed to meet their needs:
* Invite Participants
* Get all active Participants
* GET RECs
* Encumber/Unencumber a Certificate Quantity
* Create a Market Transaction

There is one type of certificate transfers:
* A market transfer from one organization to another. User denoting a sale or change in ownership.

## Process
The Market Administrator establishes a new “Market”. The Market Administrator must have their Participant Terms of Use approved by M-RETS and available for Participants to review at any time. See Operating Procedures for further details on the sign-up process, permissions, and other policies related to this account type in the M-RETS.

1. The Market Administrator has the ability to invite an unlimited number of participants to this Market. The list of Participants would be visible to the Market Administrator and they would have the ability to add or remove Participants at any time.

2. Upon accepting an invite to a Market, a special active Market Account would be automatically created for the Participant as well as a designated account where purchased RECs will be deposited. Participants can transfer Certificates to the designated Market Account. While in this special account, they by default have the status of “unencumbered”, but have the option of being toggled to “encumbered” While in this account, the certificates are visible to the Market Administrator and become available to be posted to the external market platform.

While posted on the external market, it is the Market Administrator’s responsibility to ensure Certificates have been set to “encumbered”. This ensures that they can’t be transacted on in the M-RETS system. Before a Market Participant can remove certificates from the Market Account they must be set to unencumbered. Only the Market Admin can return Certificates to and “unencumbered” status.

3. When a sale is completed in the external market, the Market Administrator has the ability to conduct a “Market Transaction” in the M-RETS. This includes creating a seamless transaction that sends Certificates from the Seller to the Market Admin, then from Market Admin to the buyer. Structuring the Market Transaction in this way gives the Market Administrator the ability to expose or not the identities of the buyer and seller in any transaction.

Purchased RECs would be deposited into the designated Active RECs account of the purchasing party. The status of these RECs would be returned to “active” and they would no longer be available for sale.


## 1. Invite Market Participants

This part of the process needs to be completed from the UI.

### Get all active Participants

	GET /v1/public/organizations?filter[participates_in_market]=<market program uuid>

##### Response
```json
{
    "data": [
        {
            "id": "<organization uuid>",
            "type": "organizations",
            "links": {...},
            "attributes": {
                "name": "...",
                "account_type": "...",
                "organization_type": "...",
                "organization_subtype": "...",
                "is_wi_service_provider": "..."
            }
        },
        ...
    ],
    "links": {...}
}
```


## 2. Encumber/Unencumber a Certificate Quantity

### Get All RECs

The general `GET RECs` call for a Market Admin will return all RECs in the M-RETS that are in any of the Market's Participants' Market Accounts.

	GET v1/public/certificate_quantities

##### Response
```json
{
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
        "certificate": {...},
        "transaction_detail": {...}
      }
    },
    {...}
  ]
}
```

### GET RECs from a Participant's dedicated Market Account

To return only the Certificates from a specific Participant's dedicated Market Account:

	GET v1/public/certificate_quantities?include=certificate&filter[organization]=<participant organization uuid>

##### Response
```json
{
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

### Encumber/Unencumber a Certificate Quantity

This part of the process needs to be completed from the UI.

## 3. Create a Market Transaction

### Notes About the Entity

Transfers in the M-RETS system are represented on a basic level by User Transactions and Transaction Details. The User Transaction captures important information about the transfer such as the transaction type, date the transaction was started/completed, and who started/completed the transaction.

A transfer User Transaction could have one or many associated transaction details that represent the individual certificate quantities that were involved in the transaction. So say in the UI, a user were to select 3 rows and complete an Market Transfer, that User Transaction would have three associated Transaction Details.

Market transfers only involve one step. A user initiates a transfer and it will immediately be completed requiring no additional steps.

The market transfer will deposited the certificates on the receiving organization's Purchased account.

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
