# Participate in a Market

## Use Case

By joining a Market on the M-RETS platform, users can seamlessly participate in an external spot market.


## Process

1. From the Participant’s perspective, the process will begin when they receive an invite from the Market Administrator. They can either accept or reject the invite.

2. If the Participant accepts, two dedicated accounts will be created in the Participant’s organizations:  a Market account and a designated purchased RECs account. To make Certificates eligible to be posted to a Market, a Participant will need to move the Certificates to the Market Account.

While in this account, the Certificates are visible to the Market Administrator and can be posted on the external market. To ensure Certificates are not transacted on while posted on an external market, in the M-RETS the Market Admin will apply the status of "encumbered". While Certificates are encumbered, they are not eligible for any other kind of transaction in the M-RETS.

From here, the Certificates will either be sold and automatically transferred to the buyer’s Organization, or the Participant can coordinate with the Market Admin to have Certificates “unencumbered”. Once Certificates are “unencumbered”, the Participant is free to move the Certificates from the Market Account and they are eligible again for any kind of transaction.

## Retrieving all Market Invites

To view all available invites, the full list of ProgramParticipantInvites can be retrieved with this call:

    GET /v1/public/program_participant_invites?filter[program_type]=market

##### Response
    Status: 200 OK
```json
{
  "data": [
    {
      "id": "<program_participant_invites uuid>",
      "type": "program_participant_invites",
      "links": {...},
      "attributes": {
          "created_at": "2020-12-11T16:06:03Z",
          "answer": "accepted",
          "answered_at": "2020-12-11T16:08:32Z"
      },
      "relationships": [...]
    },
    ...
  ]
}
```

## Accept/Reject a Market Invite

To accept a market invite:

    POST /v1/public/program_participant_invites/<program_participant_invites uuid>/accept

##### Response
    Status: 200 OK
```json
{
  "data": [
    {
      "id": "<program_participant_invites uuid>",
      "type": "program_participant_invites",
      "links": {...},
      "attributes": {
          "created_at": "2020-12-11T16:06:03Z",
          "answer": "accepted",
          "answered_at": "2020-12-11T16:08:32Z"
      },
      "relationships": [...]
    },
    ...
  ]
}
```

To reject a market invite:

    POST /v1/public/program_participant_invites/<program_participant_invites uuid>/reject

##### Response
    Status: 200 OK
```json
{
  "data": [
    {
      "id": "<program_participant_invites uuid>",
      "type": "program_participant_invites",
      "links": {...},
      "attributes": {
          "created_at": "2020-12-11T16:06:03Z",
          "answer": "rejected",
          "answered_at": "2020-12-11T16:08:32Z"
      },
      "relationships": [...]
    },
    ...
  ]
}
```

## After accepting a Market Invite

## Move Certificates to a Market Account

To move certificates into the Market account and make them eligible to be posted onto an external market, the Participant needs to simply complete an internal transaction.

### GET Accounts to identify Market Account

The Market Account will contain the name of the spot Market.

    GET /v1/public/accounts?filter[account_type]=market&filter[status]=open

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

Then select an Market Account and include it in a post call like this:

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


### Leaving a Market

To leave a Market first make sure there are no recs on the To Sell account:

    POST /v1/public/programs/<market program uuid>/leave
##### Response
    Status: 200 OK
