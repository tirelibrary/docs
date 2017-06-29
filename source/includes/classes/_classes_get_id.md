## Get Class by Id

```csharp
    HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("https://api.tirelibrary.com/v1/")
    }

    client.DefaultRequestHeaders.Add("X-API-KEY", "YourApiKeyHere");

    // Hitting the endpoint.
    object response = Newtonsoft.Json.JsonConvert.DeserializeObject
        (await client.GetStringAsync("data/classes/16"));

    // The number in the query represents the Id of 
    // the Class in question.
```

```ruby
    require 'net/http'
    
    # The number in the query represents the Id of the Class in question.
    uri = URI('https://api.tirelibrary.com/v1/data/classes/16')

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
        "timeTaken": "0.008 seconds",
        "classGroup": {
            "id": 16,
            "name": "Main Tire Classes"
        } 
    }
```

This endpoint allows you to get information on a specific class via their id.

### HTTP Request

`GET
https://api.tirelibrary.com/v1/data/classes/:id`

<aside class="notice">
Requires a Professional Developer plan with Tire Library API.
</aside>

### Query Parameters

Parameter | Description
--------- | -----------
id | Class Id to be used in the search for the specific class.

### Response Parameters

A class object.

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The identifier for the given class within Tire Library.
name | string | The name of the given class.