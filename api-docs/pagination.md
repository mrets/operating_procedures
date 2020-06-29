# Pagination

Instead of returning the full result set when the user asks for it, we can break it into smaller pages of data. That way the server never needs to serialize every resource in the system at once.

You will now see a `links` key with links to get the remaining resources in your set.

This will allow you to iterate over the next links to fetch the full results set without putting extreme pressure on your server.
