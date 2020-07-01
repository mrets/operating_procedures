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

    POST /v1/public/user_transactions
##### Example
```json
{
  "data": {
    "type": "user_transactions",
    "attributes": {
      "transaction_type": "retirement",
      "retirement_type": "State/Provincial Portfolio Standards",
      "retirement_reason": null,
      "retired_to": "CA",
      "retired_quarter": "Q2",
      "compliance_period": true
    },
    "relationships": {
      "retirement_option": {
        "data": {
          "type": "retirement_options",
          "id": "<retirement option uuid>"
        }
      }
    }
  }
}
```

### Specifying the Transaction Type

For an retirement, the transaction type should be `retirement`.

```json
  "transaction_type": "retirement"
```

### Specifying the Retirement Account

The destination on an retirement should be a Retirement Account within the same organization. To view what the possible options are, the full list of Retirement Accounts can be retrieved with this call:

    POST /v1/public/accounts?filter[account_type]=retirement&filter[status]=open

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
        "name": "...",
        "status": "open",
        "account_type": "retirement",
        "created_at": "2020-01-01T00:00:00Z",
        "updated_at": "2020-01-01T00:00:00Z"
      },
      "relationships": [...]
    },
    ...
  ]
}
```

Then select a Retirement Account and include it in a post call like this:

```json
"to_account": {
  "data": {
    "type": "accounts",
    "id": "<account uuid>"
  }
}
```

### Specifying the Retirement Options

To view valid retirement options, this call can be used:

    GET /v1/public/retirement_options
##### Response
    Status: 200 OK
```json
{
  "data": [
    {
      "id": "<retirement option uuid>",
      "type": "retirement_options",
      "links": {...},
      "attributes": {
        "resource_type": "rec",
        "name": "State/Provincial Portfolio Standards",
        "reason": null,
        "retired_to": "all",
        "quarter": false,
        "description": null,
        "compliance_period": true,
        "main_reason": "compliance"
      }
    },
    {...}
  ]
}
```

Then select the required Retirement Option and include it in a post call like this:

```json
"retirement_option": {
  "data": {
    "type": "retirement_options",
    "id": "<retirement option uuid>"
  }
}
```

On the User Transaction object, the value of `retirement_type` should match the `name` from the selected `retirement_option`.
The `retirement_reason` values should match one of the values from the `reason` field on the selected `retirement_option` (if available)The `retired_to` from the user transaction requires a State/Province abbreviation from the specify country on the `retired_to` from the `retirement_option` (if the value is `all` then all Countries are allowed).

The M-RETS platform also sends out email notifications to the both sending organization and destination organization.

Email notification settings can be viewed and updated in the M-RETS user interface by clicking on the Org in the upper right corner, then navigating to the User table.
