## Get Subclass by Id

```csharp
    HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("https://api.tirelibrary.com/v1/")
    }

    client.DefaultRequestHeaders.Add("X-API-KEY", "YourApiKeyHere");

    // Hitting the endpoint.
    object response = Newtonsoft.Json.JsonConvert.DeserializeObject
        (await client.GetStringAsync("data/subclasses/2"));

    // The number in the query represents the Id of 
    // the Subclass in question.
```

```ruby
    require 'net/http'
    
    # The number in the query represents the Id of the Subclass in question.
    uri = URI('https://api.tirelibrary.com/v1/data/subclasses/2')

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
        "timeTaken": "0.014 seconds",
        "subclass": {
            "id": 1,
            "name": "Passenger",
            "description": "For a very general search of ALL passenger type tires including Car, Light Truck, SUV etc.",
            "keywords": "Passenger",
            "classId": 16
        } 
    }
```

This endpoint allows you to retrieve the information of a specific subclass via their id.

### HTTP Request

`GET
https://api.tirelibrary.com/v1/data/subclasses/:id`

<aside class="notice">
Requires a Professional Developer plan with Tire Library API.
</aside>

### Query Parameters

Parameter | Description
--------- | -----------
id | Subclass Id to be used in the search for the specific subclass.

### Response Parameters

A subclass object.

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The identifier for the given subclass within Tire Library.
name | string | The name of the given subclass.
description | string | The description of the subclass.
keywords | string | The keywords pertaining to the subclass, delimited by ',' (comma) characters.
classId | integer | The id of the class this subclass pertains to.