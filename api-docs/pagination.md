# Pagination

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
