# Participate in a Market

## Use Case

By joining a Market on the M-RETS platform, users can seamlessly participate in an external spot market. T
 

## Process

1. From the Participant’s perspective, the process will begin when they receive an invite from the Market Administrator. They can either accept or reject the invite.

2. If the Participant accepts, two dedicated accounts will be created in the Participant’s organizations:  a Market account and a designated purchased RECs account. To make Certificates eligible to be posted to a Market, a Participant will need to move the Certificates to the Market Account.

While in this account, the Certificates are visible to the Market Administrator and can be posted on the external market. To ensure Certificates are not transacted on while posted on an external market, in the M-RETS the Market Admin will apply the status of "encumbered". While Certificates are encumbered, they are not eligible for any other kind of transaction in the M-RETS. 

From here, the Certificates will either be sold and automatically transferred to the buyer’s Organization, or the Participant can coordinate with the Market Admin to have Certificates “unencumbered”. Once Certificates are “unencumbered”, the Participant is free to move the Certificates from the Market Account and they are eligible again for any kind of transaction.

## 1. Accept a Market Invite

An invite notification will be received via email and a notification will be visible on the dashboard view when a user logs into the M-RETS. 

To accept the invite via API:


    POST v1/public/

##### Example
```json
{

}
```
##### Response
    Status: 201 Created
```json
{
  
}
```
## Move Certificates to a Market Account

To move certificates into the Market account and make them eligible to be posted onto an external market, the Participant needs to simply complete an internal transaction.

### GET Accounts to identify Market Account

The Market Account will contain the name of the spot Market.

    GET v1/public/accounts

##### Example
```json
{
 
}
```
##### Response
    Status: 201 Created
```json
{

}
```

### Initiating an Internal Transfer

One or many Certificate are specified. To view what the possible options are, the full list of Certificates with Active Certificate Quantities can be retrieved with this call:

#### Example

    POST ....

##### Response
    Status: 200 OK
```json
{

}
```

### Enqueue Transaction

Once the draft transaction is completed it needs to be enqueued with this call:

    PUT /v1/public/user_transactions/<transaction uuid>/enqueue
##### Response
    Status: 200 OK