## Default Parameters

Most Tire Library API Endpoints will return some or all of the following parameters alongside the actual expected results:

Parameter | Type | Description
--------- | ---- | -----------
page | integer | The page number for the current request. If there are a lot of results, these are split into pages and you can use this parameter to get the correct results.
totalResults or length | integer | The amount of results returned by hitting the endpoint with the specified parameters.
totalPages | integer | The amount of pages available based on the amount of results returned.
timeTaken | string | The time taken to execute the specified action.