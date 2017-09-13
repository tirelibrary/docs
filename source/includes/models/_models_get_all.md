## Get All Models

```csharp
    HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("https://api.tirelibrary.com/v1/")
    }

    client.DefaultRequestHeaders.Add("X-API-KEY", "YourApiKeyHere");

    // Hitting the endpoint.
    object response = Newtonsoft.Json.JsonConvert.DeserializeObject
        (await client.GetStringAsync("data/models?page=2"));
```

```ruby
    require 'net/http'
    
    uri = URI('https://api.tirelibrary.com/v1/data/models')

    # Adding the page parameter to the URI.
    uri.query = URI.encode_www_form(page: '2')

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
        "totalPages": 42,
        "length": 300,
        "timeTaken": "0.046 seconds",
        "models": [
            {
                "id": 2,
                "name": "TIGER PAW XTM",
                "description": "All-Season Passenger Car tire.",
                "features": "* Raised White Letter\r\n* Built with Uniroyal's DuraShield construction",
                "benefits": "* Good value and long tread life\r\n* Smooth ride",
                "manufacturerUrl": null,
                "imageUrl": "https://linktotheimagewillbehere",
                "rotationImageUrls": null,
                "videoUrl": null,
                "make": {
                    "id": 2,
                    "name": "UNIROYAL",
                    "imageUrl": "https://linktoimagewillbehere",
                    "dotRegUrl": "https://www.tireregistration.com/us_en_uniroyal.html"
                },
                "classes": [
                    {
                        "subclass": {
                            "id": 4,
                            "name": "All-Season (A/S)",
                            "description": "All-Season tires are designed to provide a relatively quiet ride with good tread life and fuel economy. They offer versatile performance and are designed to perform in a variety of road conditions, including wet roads and light snow. All-Season tires won't provide the same amount of extreme grip and sharp handling of a Summer tire and is not designed to handle extreme Winter conditions.",
                            "keywords": "A/S,AS,All-Season,Four Season"
                        }
                    },
                    ...
                ]
            },
            ...
        ]
    }
```

This endpoint allows you to get all models and their information.

### HTTP Request

`GET
https://api.tirelibrary.com/v1/data/models`

<aside class="notice">
Requires a Developer plan with Tire Library API.
</aside>

### Query Parameters

Parameter | Type | Required | Default | Description
--------- | ---- | -------- | ------- | -----------
page | int | No | 1 | The page number to be retrieved. Currently returns 30 items per page.

### Response Parameters

A Tire Model object.

Parameter | Type | Description
--------- | ---- | -----------
models | [Tire Model](https://developer.tirelibrary.com/#tire-model) Array | An array of Tire Model objects (includes associated Tire Makes).