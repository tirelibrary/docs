## Search Makes

```csharp
    HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("https://api.tirelibrary.com/v1/")
    }

    client.DefaultRequestHeaders.Add("X-API-KEY", "YourApiKeyHere");

    // Hitting the endpoint.
    object response = Newtonsoft.Json.JsonConvert.DeserializeObject
        (await client.GetStringAsync("search/makes?q=michelin"));
```

```ruby
    require 'net/http'
    
    uri = URI('https://api.tirelibrary.com/v1/search/makes')

    # Adding the search parameter to the URI.
    uri.query = URI.encode_www_form q: 'michelin'

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
        "totalResults": 1,
        "totalPages": 1,
        "timeTaken": "0.001 seconds",
        "results": [
            {
                "id": 3,
                "name": "MICHELIN",
                "dotRegUrl": "Http://link",
                "imageUrl": "https://linktoimagewillbehere"
            },
            ...
        ]
    }
```

This endpoint allows you to search for makes.

### HTTP Request

`GET
https://api.tirelibrary.com/v1/search/makes`

<aside class="notice">
Requires a Professional Developer plan with Tire Library API.
</aside>

### Query Parameters

Parameter | Type | Description
--------- | ---- | -----------
q | string | Used to search for specific results.

### Response Parameters

An array of Make objects:

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The identifier for the given make within Tire Library.
name | string | The name of the given make.
dotRegUrl | string | The link to the Department of Transport Registration for a given make.
imageUrl | string | The link to the image of a given make.