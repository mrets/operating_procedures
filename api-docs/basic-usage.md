# Basic Usage

## Authentication

Bearer Authentication is the authentication method for authenticating with the M-RETS API.

### How To Use

Here's an example of how the curl request should look with your API token entered:

```
curl --location --request GET 'https://app.mrets.org/v1/public/accounts' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'X-Api-Key: <token>'
```
 
## Pagination

Instead of returning the full result set when the user asks for it, we can break it into smaller pages of data. That way the server never needs to serialize every resource in the system at once.

You can use `page[number]` and `page[size]` in the query string to control which page you are viewing. The maximum current page size is 1000.

**For example**

```
https://m-rets-sandbox.herokuapp.com/v1/public/generators?page[number]=2&page[size]=30
```

This will allow you to iterate over the next links to fetch the full results set without putting extreme pressure on your server.


The reponse will contain a `links` section, which has URIs for the first, next, and last page of your request.

```
"links": {
       "first": "https://m-rets-sandbox.herokuapp.com/v1/public/generators?page[number]=1&page[size]=30",
       "next": "https://m-rets-sandbox.herokuapp.com/v1/public/generators?page[number]=2&page[size]=30",
       "last": "https://m-rets-sandbox.herokuapp.com/v1/public/generators?page[number]=6&page[size]=30"
}
```   
## Filtering

The MRETS API supports sorting primary resources by [multiple sort criteria](https://jsonapi.org/format/#fetching-sorting).

We can use filters to query an end point by the value of an attribute.

For example

```
https://m-rets-sandbox.herokuapp.com/v1/public/generators?filters[status]=draft
```

Please see the specific endpoint in our documentation to see which filters are available.

## Sorting

Sorting is available on most of our collection endpoints.

By default, all attributes are sortable and the order is ascending.

For example

https://m-rets-sandbox.herokuapp.com/v1/public/generators?sort=state_province

Multiple attributes filtering is also allowed, a comma-separated list sould be provided.

https://m-rets-sandbox.herokuapp.com/v1/public/accounts?sort=status,name

To use descending order you need to put - in front of the corresponding attribute.

https://m-rets-sandbox.herokuapp.com/v1/public/accounts?sort=status,-name

## Date and Timestamp Format

We use the standard [ISO 8601](https://www.w3.org/TR/NOTE-datetime) format for all of our date and timestamps.

### Complete date
YYYY-MM-DD (eg 1997-07-16)  
### Complete date plus hours and minutes
YYYY-MM-DDThh:mmTZD (eg 1997-07-16T19:20+01:00)

### Timezone Designator
Our defines two ways of handling time zone offsets:

1.     Times are expressed in UTC (Coordinated Universal Time), with a special UTC designator ("Z").
1.     Times are expressed in local time, together with a time zone offset in hours and minutes. A time zone offset of "+hh:mm" indicates that the date/time uses a local time zone which is "hh" hours and "mm" minutes ahead of UTC. A time zone offset of "-hh:mm" indicates that the date/time uses a local time zone which is "hh" hours and "mm" minutes behind UTC. 

#### Example

1994-11-05T08:15:30-05:00 corresponds to November 5, 1994, 8:15:30 am, US Eastern Standard Time.  
1994-11-05T13:15:30Z corresponds to the same instant.

## Rate Limits

Each API token can be used up to 10 times over 5 seconds. The API rate limit is the same for all endpoints.

## Response Codes

The standard M-RETS API returns HTTP status codes in addition to JSON-based error codes and messages.

### HTTP Status Codes

The M-RETS API attempts to return appropriate HTTP status codes for every request.

| Code | Text                  | Description                                                                                                                                                                                                                                                                                                |
| ---- | --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 200  | OK                    | Success!                                                                                                                                                                                                                                                                                                   |
| 304  | Not Modified          | There was no new data to return.                                                                                                                                                                                                                                                                           |
| 400  | Bad Request           | The request was invalid or cannot be otherwise served. An accompanying error message will explain further.                                                                                                                                                                                                 |
| 401  | Unauthorized          | Missing or incorrect authentication credentials. This may also returned in other undefined circumstances.                                                                                                                                                                                                  |
| 403  | Forbidden             | The request is understood, but it has been refused or access is not allowed. |
| 404  | Not Found             | The URI requested is invalid or the resource requested, such as an account, does not exist.                                                                                                                                                                                                                |
| 422  | Unprocessable Entity  | Returned when the data is unable to be processed (for example, if a to POST account is not valid, or the JSON body of a request is badly-formed). |
| 429  | Too Many Requests| Returned when a request cannot be served due to the API token's rate limit having been exhausted. See Rate Limiting. |
| 500  | Internal Server Error | Something is broken. This is usually a temporary error, for example in a high load situation or if an endpoint is temporarily having issues. Contact the M-RETS Administrator to get information about the issue, or try again later.                                                                      |
| 503  | Service Unavailable   | M-RETS servers are up, but overloaded with requests or being upgraded. Try again later.                                                                                                                                                                                                                                 |
| 504  | Gateway timeout       | M-RETS servers are up, but the request couldn’t be serviced due to some failure within the internal stack. Try again later.                                                                                                                                                                         |

### Error Messages

M-RETS API error messages are returned in JSON format. For example, an error might look like this:

```
{
  "errors": [
    {
      "title": "Record not found",
      "detail": "The record identified by 00000000-0000-0000-0000-000000000001 could not be found.",
      "code": "404",
      "status": "404"
    }
  ]
}
```



