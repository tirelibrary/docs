## Get Subclass Models by Subclass Id

```csharp
    HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("https://api.tirelibrary.com/v1/")
    }

    client.DefaultRequestHeaders.Add("X-API-KEY", "YourApiKeyHere");

    // Hitting the endpoint.
    object response = Newtonsoft.Json.JsonConvert.DeserializeObject
        (await client.GetStringAsync("data/subclasses/2/models"));

    // The number in the query represents the Id of 
    // the Subclass in question.
```

```ruby
    require 'net/http'
    
    # The number in the query represents the Id of the Subclass in question.
    uri = URI('https://api.tirelibrary.com/v1/data/subclasses/2/models')

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
        "length": 3,
        "timeTaken": "0.057 seconds",
        "subclass": {
            "id": 1,
            "name": "Passenger",
            "description": "For a very general search of ALL passenger type tires including Car, Light Truck, SUV etc.",
            "keywords": "Passenger",
            "classId": 16,
            "models": [
              {
                "id": 3,
                "name": "RALLYE COSMETIC",
                "description": "Passenger Car tire.",
                "benefits": null,
                "features": null,
                "manufacturerUrl": null,
                "imageUrl": null,
                "videoUrl": null,
                "rotationImageUrls": null,
                "tireMake": {
                    "id": 2,
                    "name": "UNIROYAL",
                    "imageUrl": "https://media.tirelibrary.com/images/4b048010469d4ee69b38893fe19e9cb0",
                    "dotRegUrl": "https://www.tireregistration.com/us_en_uniroyal.html"
                }
              },
              ...
            ]
        } 
    }
```

This endpoint allows you to get information on the models within a specific subclass via the id of the subclass.

### HTTP Request

`GET
https://api.tirelibrary.com/v1/data/subclasses/:id/models`

<aside class="notice">
Requires a Professional Developer plan with Tire Library API.
</aside>

### Query Parameters

Parameter | Description
--------- | -----------
id | Subclass Id to be used in the search for the specific subclass.

### Response Parameters

A subclass object.

#### Subclass Object Parameters

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The identifier for the given subclass within Tire Library.
name | string | The name of the given subclass.
description | string | The description of the subclass.
keywords | string | The keywords pertaining to the subclass, delimited by ',' (comma) characters.
classId | integer | The id of the class this subclass pertains to.
models | array of objects | An array of all tire models pertaining to this subclass object. Parameters are outlined below.

#### Model Object Parameters

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
tireMake | object | The tire make object linked to the tire model. Parameters are outlined below.

#### Tire Make Object Parameters

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The identifier for the given make within Tire Library.
name | string | The name of the given make.
imageUrl | string | The link to the image of a given make.
dotRegUrl | string | The link to the Department of Transport Registration for a given make.