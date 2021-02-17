# Participate in a Market

## Use Case

By joining a Market on the M-RETS platform, users can seamlessly participate in an external spot market. These examples are from the Participant's perspective.

## Process

1. From the Participant’s perspective, the process will begin when they receive an invite from the Market Administrator. They can either accept or reject the invite.

2. If the Participant accepts, two dedicated accounts will be created in the Participant’s organizations:  a Market account and a designated purchased RECs account. To make Certificates eligible to be posted to a Market, a Participant will need to move the Certificates to the Market Account.

While in this account, the Certificates are visible to the Market Administrator and can be posted on the external market. To ensure Certificates are not transacted on while posted on an external market, in the M-RETS the Market Admin will apply the status of "encumbered". While Certificates are encumbered, they are not eligible for any other kind of transaction in the M-RETS.

From here, the Certificates will either be sold and automatically transferred to the buyer’s Organization, or the Participant can coordinate with the Market Admin to have Certificates “unencumbered”. Once Certificates are “unencumbered”, the Participant is free to move the Certificates from the Market Account and they are eligible again for any kind of transaction.

## 1. Accept or Reject a Market Admin Invite

A Participant (logged in from their M-RETS organization or using their Organization API keys) will be able to accept or reject a pending Market invite. 

## PUT Participant Invites

    `PUT..... `
    
### Response

Status: 200 OK
```json
{
  
}
```

### GET Accounts to identify Market Account

The Market Account will contain the name of the spot Market.

    GET /v1/public/accounts?filter[account_type]=market&filter[status]=open

##### Response
    Status: 200 OK
```json
{
  
}
```

Then use the Market Account ID while creating an intermal transaction. Include it in a post call like this:

```json
"to_account": {
  "data": {
    "type": "accounts",
    "id": "<account uuid>"
  }
}
```

### Initiating an Internal Transfer

One or many Certificate are specified. To view what the possible options are, the full list of Certificates with Active Certificate Quantities can be retrieved with this call:

#### Example

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


### Enqueue Transaction

Once the draft transaction is completed it needs to be enqueued with this call:

    PUT /v1/public/user_transactions/<transaction uuid>/enqueue
##### Response
    Status: 200 OK
