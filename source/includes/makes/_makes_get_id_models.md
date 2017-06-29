## Get Make Models by Make Id

```csharp
    HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("https://api.tirelibrary.com/v1/")
    }

    client.DefaultRequestHeaders.Add("X-API-KEY", "YourApiKeyHere");

    // Hitting the endpoint.
    object response = Newtonsoft.Json.JsonConvert.DeserializeObject
        (await client.GetStringAsync("data/makes/485/models"));

    // The number in the query represents the Id of 
    // the Tire Make in question.
```

```ruby
    require 'net/http'
    
    # The number in the query represents the Id of the Tire Make in question.
    uri = URI('https://api.tirelibrary.com/v1/data/makes/485/models')

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
        "totalPages": 1,
        "length": 22,
        "timeTaken": "0.018 seconds",
        "models": [
            {
                "id": 19275,
                "name": "ACCELERA",
                "description": "Affordable, Directional, All Season Passenger Vehicle Tire.",
                "features": "* Twin straight grooves\r\n* Center rib\r\n* Unique shoulder block design",
                "benefits": "* Maintain stability and enable rapid water evacuation to overcome aquaplaning risk\r\n* Provides directional stability and quick steering response\r\n* Provide optimum cornering stability",
                "manufacturerUrl": "http://linkwillbehere",
                "imageUrl": null,
                "rotationImageUrls": null,
                "videoUrl": null
            },
            ...
        ]
    }
```

This endpoint allows you to get information on models within the given tire make id.

### HTTP Request

`GET
https://api.tirelibrary.com/v1/data/makes/:id/models`

<aside class="notice">
Requires a Professional Developer plan with Tire Library API.
</aside>

### Query Parameters

Parameter | Description
--------- | -----------
id | Tire Make Id to be used to find the make and the models within.

### Response Parameters

An array of Tire Model objects.

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