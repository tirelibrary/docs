## Search Models

```csharp
    HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("https://api.tirelibrary.com/v1/")
    }

    client.DefaultRequestHeaders.Add("X-API-KEY", "YourApiKeyHere");

    // Hitting the endpoint.
    object response = Newtonsoft.Json.JsonConvert.DeserializeObject
        (await client.GetStringAsync("search/models?q=a"));
```

```ruby
    require 'net/http'
    
    uri = URI('https://api.tirelibrary.com/v1/search/models')

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
        "totalResults": 3485,
        "totalPages": 35,
        "timeTaken": "0.001 seconds",
        "results": [
            {
                "id": 5255,
                "name": "UA-603",
                "description": "Model description",
                "features": "Model features",
                "benefits": "Model benefits",
                "imageUrl": "https://linktoimagewillbehere"
            },
            ...
        ]
    }
```

This endpoint allows you to search for models.

### HTTP Request

`GET
https://api.tirelibrary.com/v1/search/models`

<aside class="notice">
Requires a Developer plan with Tire Library API.
</aside>

### Query Parameters

Parameter | Description
--------- | -----------
q | Used to search for specific results.

### Response Parameters

An array of Tire Model objects:

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The identifier for the given tire model within Tire Library.
name | string | The name of the specified tire model.
description | string | The description of the specified tire model.
features | string | The features of the specified tire model, delimited by '*' (asterisk) characters.
benefits | string | The benefits of the specified tire model, delimited by '*' (asterisk) characters.
imageUrl | string | The link to the image of this tire model.