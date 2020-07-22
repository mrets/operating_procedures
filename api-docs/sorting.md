Sorting is available on most of our collection endpoints. 

By default, all attributes are sortable and the order is ascending.

For example
```
https://m-rets-sandbox.herokuapp.com/v1/public/generators?sort=state_province
```

Multiple attributes filtering is also allowed, a comma-separated list sould be provided.
```
https://m-rets-sandbox.herokuapp.com/v1/public/accounts?sort=status,name
```

To use descending order you need to put `-` in front of the corresponding attribute.
```
https://m-rets-sandbox.herokuapp.com/v1/public/accounts?sort=status,-name
```
