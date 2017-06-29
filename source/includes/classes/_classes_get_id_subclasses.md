## Get Subclasses by Class Id

```csharp
    HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("https://api.tirelibrary.com/v1/")
    }

    client.DefaultRequestHeaders.Add("X-API-KEY", "YourApiKeyHere");

    // Hitting the endpoint.
    object response = Newtonsoft.Json.JsonConvert.DeserializeObject
        (await client.GetStringAsync("data/classes/16/subclasses"));

    // The number in the query represents the Id of 
    // the Class in question.
```

```ruby
    require 'net/http'
    
    # The number in the query represents the Id of the Class in question.
    uri = URI('https://api.tirelibrary.com/v1/data/classes/16/subclasses')

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
        "length": 17,
        "timeTaken": "0.016 seconds",
        "class": {
            "id": 16,
            "name": "Main Tire Classes",
            "subclasses": [
              {
                  "id": 1,
                  "name": "Passenger",
                  "description": "For a very general search of ALL passenger type tires including Car, Light Truck, SUV etc.",
                  "keywords": "Passenger"
              },
              ...
            ]
        }
    }
```

This endpoint allows you to get information on subclasses within a given class based on their id.

### HTTP Request

`GET
https://api.tirelibrary.com/v1/data/classes/:id/subclasses`

<aside class="notice">
Requires a Professional Developer plan with Tire Library API.
</aside>

### Query Parameters

Parameter | Description
--------- | -----------
id | Class Id to be used to find the subclasses within a given class.

### Response Parameters

A class object.

#### Class Object Parameters

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The identifier for the given class within Tire Library.
name | string | The name of the given class.
subclasses | array of objects | An array of all subclasses pertaining to this class object. Parameters are outlined below.

#### Subclass Object Parameters

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The identifier for the given subclass within Tire Library.
name | string | The name of the given subclass.
description | string | The description of the subclass.
keywords | string | The keywords pertaining to the subclass, delimited by ',' (comma) characters.