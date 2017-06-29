## Errors

Tire Library follows the conventions for HTTP response codes:
- 2xx indicate success;
- 4xx indicate errors; and
- 5xx indicate server errors with Tire Library API itself.


Error Code | Meaning
---------- | -------
400 | **Bad Request** - Your request is invalid, please check the content you are sending.
401 | **Unauthorized** - Your API key could not be validated. Check it to ensure you have the correct one and that your subscription is also active.
403 | **Forbidden** - The endpoint you are trying to reach is not available to your subscription.
404 | **Not Found** - The endpoint does not exist.
422 | **Unprocessable Entity** - The parameters sent do not match the required ones. Check your request to ensure it has everything the endpoint in questio needs.
500 | **Internal Server Error** - Something went wrong with our servers, let us know if the problem persists.
