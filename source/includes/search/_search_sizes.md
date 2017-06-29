## Search Sizes (Specific)

```csharp
    HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("https://api.tirelibrary.com/v1/")
    }

    client.DefaultRequestHeaders.Add("X-API-KEY", "YourApiKeyHere");

    // Hitting the endpoint.
    object response = Newtonsoft.Json.JsonConvert.DeserializeObject
        (await client.GetStringAsync("search/sizes?q=a"));
```

```ruby
    require 'net/http'
    
    uri = URI('https://api.tirelibrary.com/v1/search/sizes')

    # Adding the search parameter to the URI.
    uri.query = URI.encode_www_form q: 'a'

    request = Net::HTTP::Get.new uri

    # Adding the API Key.
    request['X-API-KEY'] = 'your_api_key_here'

    # Hitting the endpoint.
    response = Net::HTTP.start uri.hostname, uri.port, use_ssl: true do |http|
        http.request request
    end

    # See the parameters section for the accepted search parameters for this endpoint.
```

> The following sample represents the JSON response for this endpoint:

```json
    {
        "page": 1,
        "totalResults": 117482,
        "totalPages": 1175,
        "timeTaken": "0.016 seconds",
        "results": [
            {
                "id": 233509,
                "itemNumber": "372323",
                "displayName": "31X10.50R15LT C A/T",
                "model": "A/T",
                "make": "SIERRA",
                "imageUrl": "https://linktoimagewillbehere",
                "makeImageUrl": "https://linktoimagewillbehere",
                "loadRating": "109",
                "speedRating": "s",
                "plyRating": "6"
            },
            ...
        ]
    }
```

This endpoint allows you to search for sizes.

### HTTP Request

`GET
https://api.tirelibrary.com/v1/search/sizes`

<aside class="notice">
Requires a Developer plan with Tire Library API.
</aside>

### Query Parameters

Parameter | Description
--------- | -----------
q | Used to search for specific results.

### Response Parameters

An array of Tire Size objects:

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The identifier for the given tire size within Tire Library.
itemNumber | string | The item number for the given tire size within Tire Library (can be used to search for sizes).
displayName | string | The display name for the specified tire size.
model | string | The name of the model this tire size is linked to.
imageUrl | string | The link to the image of the tire size.
makeImageUrl | string | The link to the image of the make for this tire size.
loadRating | string | A string containing the relative load carrying capabilities of the tire size.
speedRating | string | A string containing the designed speed capability of the tire size.
plyRating | string | A string containing the amount of load the tire can safely carry at a specified inflation pressure.