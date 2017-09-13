## Search General

```csharp
    HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("https://api.tirelibrary.com/v1/")
    }

    client.DefaultRequestHeaders.Add("X-API-KEY", "YourApiKeyHere");

    // Hitting the endpoint.
    object response = Newtonsoft.Json.JsonConvert.DeserializeObject
        (await client.GetStringAsync("search?q=2056016&filters=speedrating:h&page=1&pagesize=30"));
    
    // See the parameters section for the accepted search parameters for this endpoint.
```

```ruby
    require 'net/http'
    
    uri = URI('https://api.tirelibrary.com/v1/search')

    # Adding the search parameter to the URI.
    uri.query = URI.encode_www_form(q: '2056016', 
                                    filters: 'speedrating:h', 
                                    page: 1, 
                                    pagesize: 30)

    request = Net::HTTP::Get.new uri

    # Adding the API Key.
    request['X-API-KEY'] = 'your_api_key_here'

    # Hitting the endpoint.
    response = Net::HTTP.start uri.hostname, uri.port, use_ssl: true do |http|
        http.request request
    end

    # See the parameters section for the accepted search parameters for this endpoint.
```

> The following sample represents the JSON response for this endpoint:

```json
    {
        "page": 1,
        "totalResults": 1169,
        "totalPages": 39,
        "timeTaken": "0.001 seconds",
        "results": [
            {
                "id": 178385,
                "itemNumber": "AG300P1609",
                "displayName": "205/60R16 XL GRIP300",
                "imageUrl": "https://linktoimagewillbehere",
                "model": "GRIP300",
                "make": "AUTOGRIP",
                "makeImageUrl": "https://linktoimagewillbehere"
            },
            ...
        ]
    }
```

This endpoint allows you to search for tires.

### HTTP Request

`GET
https://api.tirelibrary.com/v1/search`

<aside class="notice">
Requires a Developer plan with Tire Library API.
</aside>

### Query Parameters

Parameter | Type | Required | Default | Description
--------- | ---- | -------- | ------- | -----------
q | string | Yes | - | Used to search for specific results. A list of properties that can be searched for are listed below.
filters | string | No | - | Comma-delimited string of fields to filter the query. Sample: `speedrating:h,rimsize:16`.
page | int | No | 1 | The page to be retrieved from the search results.
pageSize | int | No | 30 | The amount of items to be retrieved on the page. Max value is 1000.

### Search Properties

You can search for tires based on:
- Size; and
- Make.

### Response Parameters

An array of Tire Size objects:

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The identifier for the given tire size within Tire Library.
itemNumber | string | The item number for the given tire size within Tire Library (can be used to search for sizes).
displayName | string | The display name for the specified tire size.
imageUrl | string | The link to the image of the tire size.
model | string | The name of the model this tire size is linked to.
make | string | The name of the make this tire size is linked to.
makeImageUrl | string | The link to the image of the make for this tire size.