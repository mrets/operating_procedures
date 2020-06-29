# Response Codes

Example of response code docs: [https://developer.twitter.com/en/docs/basics/response-codes](https://developer.twitter.com/en/docs/basics/response-codes)

The standard Twitter API returns HTTP status codes in addition to JSON-based error codes and messages.

## HTTP Status Codes

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

## Error Messages

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

