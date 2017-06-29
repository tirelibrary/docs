## Get All Models

```csharp
    HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("https://api.tirelibrary.com/v1/")
    }

    client.DefaultRequestHeaders.Add("X-API-KEY", "YourApiKeyHere");

    // Hitting the endpoint.
    object response = Newtonsoft.Json.JsonConvert.DeserializeObject
        (await client.GetStringAsync("data/models"));
```

```ruby
    require 'net/http'
    
    uri = URI('https://api.tirelibrary.com/v1/data/models')

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
Requires a Professional Developer plan with Tire Library API.
</aside>

### Response Parameters

An array of Tire Model objects.

#### Tire Model Object Parameters

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The identifier for the given tire model within Tire Library.
name | string | The name of the given tire model.
description | string | The description of the tire model.
benefits | string | The benefits of the tire model, delimited by '*' (asterisk) characters.
features | string | The features of the tire model, delimited by '*' (asterisk) characters.
manufacturerUrl | string | The link to the manufacturer of the tire model.
videoUrl | string | The link of
imageUrl | string | The link to the image of the tire model.
rotationImageUrls | string | An array of 24 strings containing the image links for viewing the tire model from multiple angles.
classes | array of objects | An array of all subclasses pertaining to this tire model object. Parameters are outlined below.

#### Subclass Object Parameters

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The identifier for the given subclass within Tire Library.
name | string | The name of the given subclass.
description | string | The description of the subclass.
keywords | string | The keywords pertaining to the subclass, delimited by ',' (comma) characters.
