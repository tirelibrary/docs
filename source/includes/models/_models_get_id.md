## Get Model by Id

```csharp
    HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("https://api.tirelibrary.com/v1/")
    }

    client.DefaultRequestHeaders.Add("X-API-KEY", "YourApiKeyHere");

    // Hitting the endpoint.
    object response = Newtonsoft.Json.JsonConvert.DeserializeObject
        (await client.GetStringAsync("data/models/2"));

    // The number in the query represents the Id of 
    // the Tire Model in question.
```

```ruby
    require 'net/http'
    
    # The number in the query represents the Id of the Tire Model in question.
    uri = URI('https://api.tirelibrary.com/v1/data/models/2')

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
        "timeTaken": "0.003 seconds",
        "model": {
            "id": 2,
            "name": "TIGER PAW XTM",
            "description": "All-Season Passenger Car tire.",
            "features": "* Raised White Letter\r\n* Built with Uniroyal's DuraShield construction",
            "benefits": "* Good value and long tread life\r\n* Smooth ride",
            "manufacturerUrl": null,
            "imageUrl": "https://linktoimagewillbehere",
            "rotationImageUrls": null,
            "videoUrl": null,
            "make": {
                "id": 2,
                "name": "UNIROYAL",
                "imageUrl": "https://linktoimagewillbehere",
                "dotRegUrl": "http://linkwillbehere"
            },
            "classes": [
                {
                    "id": 4,
                    "name": "All-Season (A/S)",
                    "description": "All-Season tires are designed to provide a relatively quiet ride with good tread life and fuel economy. They offer versatile performance and are designed to perform in a variety of road conditions, including wet roads and light snow. All-Season tires won't provide the same amount of extreme grip and sharp handling of a Summer tire and is not designed to handle extreme Winter conditions.",
                    "keywords": "A/S,AS,All-Season,Four Season"
                },
                ...
            ]
        }
    }
```

This endpoint allows you to get information on a specific tire model via their id.

### HTTP Request

`GET
https://api.tirelibrary.com/v1/data/models/:id`

<aside class="notice">
Requires a Professional Developer plan with Tire Library API.
</aside>

### Query Parameters

Parameter | Description
--------- | -----------
id | The tire Model Id to be used in the search for the specific tire model.

### Response Parameters

A Tire Model object.

Parameter | Type | Description
--------- | ---- | -----------
model | [Tire Model](https://developer.tirelibrary.com/#tire-model) | The tire model object.

#### Subclass Object Parameters

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The identifier for the given subclass within Tire Library.
name | string | The name of the given subclass.
description | string | The description of the subclass.
keywords | string | The keywords pertaining to the subclass, delimited by ',' (comma) characters.