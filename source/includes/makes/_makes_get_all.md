## Get All Makes

```csharp
    HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("https://api.tirelibrary.com/v1/")
    }

    client.DefaultRequestHeaders.Add("X-API-KEY", "YourApiKeyHere");

    // Hitting the endpoint.
    object response = Newtonsoft.Json.JsonConvert.DeserializeObject
        (await client.GetStringAsync("data/makes"));
```

```ruby
    require 'net/http'
    
    uri = URI('https://api.tirelibrary.com/v1/data/makes')

    # Adding the all parameter to the URI.
    uri.query = URI.encode_www_form all: true

    request = Net::HTTP::Get.new uri

    # Adding the API Key.
    request['X-API-KEY'] = 'your_api_key_here'

    # Hitting the endpoint.
    response = Net::HTTP.start uri.hostname, uri.port, use_ssl: true do |http|
        http.request request
    end
```

> The following sample represents the JSON response for this endpoint:

```json
    {
        "page": 1,
        "totalPages": 2,
        "length": 300,
        "timeTaken": "0.009 seconds",
        "makes": [
            {
                "id": 485,
                "name": "ACCELERA",
                "imageUrl": "https://linktoimagewillbehere",
                "dotRegUrl": "http://linkwillbehere"
            },
            ...
        ]
    }
```

This endpoint allows you to get all makes and their information.

### HTTP Request

`GET
https://api.tirelibrary.com/v1/data/makes`

<aside class="notice">
Requires a Professional Developer plan with Tire Library API.
</aside>

### Query Parameters

Parameter | Value | Description
--------- | ----- | -----------
all | true | Requests all makes in one go as opposed to multiple pages.

### Response Parameters

An array of Tire Make objects.

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The identifier for the given make within Tire Library.
name | string | The name of the given make.
imageUrl | string | The link to the image of a given make.
dotRegUrl | string | The link to the Department of Transport Registration for a given make.