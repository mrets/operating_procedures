The MRETS API supports sorting primary resources by [multiple sort criteria](https://jsonapi.org/format/#fetching-sorting).

We can use filters to query an end point by the value of an attribute.

For example

```
https://m-rets-sandbox.herokuapp.com/v1/public/generators?filters[status]=draft
```

Please see the specific endpoint in our documentation to see which filters are available.
