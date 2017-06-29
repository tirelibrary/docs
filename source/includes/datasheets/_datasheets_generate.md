## Generate Datasheet

```csharp
    HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("https://api.tirelibrary.com/v1/")
    };

    client.DefaultRequestHeaders.Add("X-API-KEY", "YourApiKeyHere");
    
    // Hitting the endpoint.
    // This returns a File as opposed to JSON.
    return await client.GetStreamAsync("templates/datasheets/41248");

    // The number in the query represents the Id of 
    // the datasheet in question.
```

```ruby
    require 'net/http'
    
    # The number in the query represents the Id of the Datasheet in question.
    uri = URI('https://api.tirelibrary.com/v1/templates/datasheets/41248')

    request = Net::HTTP::Get.new uri

    # Adding the API Key.
    request['X-API-KEY'] = 'your_api_key_here'

    # Hitting the endpoint.
    response = Net::HTTP.start uri.hostname, uri.port, use_ssl: true do |http|
        http.request request
    end
```

> This endpoint returns a PDF file containing the specified datasheet.

### HTTP Request

`GET
https://api.tirelibrary.com/v1/templates/datasheets/:id`

<aside class="notice">
Requires a Datasheets plan with Tire Library API.
</aside>

### Query Parameters

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The identifier for the specified datasheet to be retrieved.