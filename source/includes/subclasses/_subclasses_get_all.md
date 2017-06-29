## Get All Subclasses

```csharp
    HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("https://api.tirelibrary.com/v1/")
    }

    client.DefaultRequestHeaders.Add("X-API-KEY", "YourApiKeyHere");

    // Hitting the endpoint.
    object response = Newtonsoft.Json.JsonConvert.DeserializeObject
        (await client.GetStringAsync("data/subclasses"));
```

```ruby
    require 'net/http'
    
    uri = URI('https://api.tirelibrary.com/v1/data/subclasses')

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
        "length": 87,
        "timeTaken": "0.051 seconds",
        "subclasses": [
            {
                "id": 2,
                "name": "High Performance (HP)",
                "description": "Tires in which the Speed Ratings are predominately H-Rated and/or V-Rated and focused on Performance. The main benefits of these tires are higher speed capability, improved handling and maximum dry road grip. This can come at a cost ie. lower tread life and higher costs.",
                "keywords": "HP,High Performance,Touring",
                "classId": 1
            },
            ...
        ]
    }
```

This endpoint allows you to get all subceslass and their information.

### HTTP Request

`GET
https://api.tirelibrary.com/v1/data/subclasses`

<aside class="notice">
Requires a Professional Developer plan with Tire Library API.
</aside>

### Response Parameters

An array of subclass objects.

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The identifier for the given subclass within Tire Library.
name | string | The name of the given subclass.
description | string | The description of the subclass.
keywords | string | The keywords pertaining to the subclass, delimited by ',' (comma) characters.
classId | integer | The id of the class this subclass pertains to.