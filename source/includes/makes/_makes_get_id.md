## Get Make by Id

```csharp
    HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("https://api.tirelibrary.com/v1/")
    }

    client.DefaultRequestHeaders.Add("X-API-KEY", "YourApiKeyHere");

    // Hitting the endpoint.
    object response = Newtonsoft.Json.JsonConvert.DeserializeObject
        (await client.GetStringAsync("data/makes/485"));

    // The number in the query represents the Id of 
    // the Tire Make in question.
```

```ruby
    require 'net/http'
    
    # The number in the query represents the Id of the Tire Make in question.
    uri = URI('https://api.tirelibrary.com/v1/data/makes/485')

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
        "timeTaken": "0.012 seconds",
        "make": {
            "id": 485,
            "name": "ACCELERA",
            "imageUrl": "https://linktoimagewillbehere",
            "dotRegUrl": "http://linkwillbehere"
        } 
    }
```

This endpoint allows you to get information on a specific make via their id.

### HTTP Request

`GET
https://api.tirelibrary.com/v1/data/makes/:id`

<aside class="notice">
Requires a Professional Developer plan with Tire Library API.
</aside>

### Query Parameters

Parameter | Description
--------- | -----------
id | Make Id to be used in the search for the specific tire make.

### Response Parameters

A Tire Make object.

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The identifier for the given make within Tire Library.
name | string | The name of the given make.
imageUrl | string | The link to the image of a given make.
dotRegUrl | string | The link to the Department of Transport Registration for a given make.