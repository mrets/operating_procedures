# Authentication

Bearer Authentication is the authentication method for authenticating with the M-RETS API.

## How To Use

Here's an example of how the curl request should look with your API token entered:

```
curl --location --request GET 'https://app.mrets.org/v1/public/accounts' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'X-Api-Key: <token>'
```
