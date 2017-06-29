## Get Other Tire Sizes in Model by Tire Size Id

```csharp
    HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("https://api.tirelibrary.com/v1/")
    }

    client.DefaultRequestHeaders.Add("X-API-KEY", "YourApiKeyHere");

    // Hitting the endpoint.
    object response = Newtonsoft.Json.JsonConvert.DeserializeObject
        (await client.GetStringAsync("data/sizes/33973/otherSizes"));

    // The number in the query represents the Id of 
    // the Tire Size in question.
```

```ruby
    require 'net/http'
    
    # The number in the query represents the Id of the Tire Size in question.
    uri = URI('https://api.tirelibrary.com/v1/data/sizes/33973/otherSizes')

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
        "length": 31,
        "timeTaken": "0.01 seconds",
        "sizes": [
            {
                "id": 34280,
                "itemNumber": "04380",
                "gmCode": null,
                "universalItemNumber": null,
                "displayName": "235/75R15  TIGER PAW XTM",
                "loadRange": "SL        ",
                "traCode": null,
                "utqg": "400 A C",
                "sidewall": "WW",
                "sectionWidth": 235,
                "aspectRatio": 75,
                "rimSize": 15,
                "inchWidth": null,
                "diameter": null,
                "metricRimDiameter": null,
                "overallDiameter": 29.65,
                "loadRating": "105",
                "speedRating": "S",
                "plyRating": null,
                "starRating": null,
                "loadCapacitySingle": "2028",
                "loadCapacityDual": null,
                "maxInflationPressure": "35",
                "weight": null,
                "approvedRimWidth": "6.0 - 8.0           ",
                "measuringRimWidth": "6.5                 ",
                "overallWidth": 9.3,
                "treadWidth": null,
                "treadDepth": 12,
                "loadedWidth": null,
                "staticLoadedRadius": null,
                "minimumDualSpacing": null,
                "revolutionsPerMile": null,
                "rollingCircumference": null,
                "originCountry": null,
                "warranty": "60000",
                "upc": null,
                "ean": null,
                "asin": null,
                "createdAt": "2017-01-17T11:26:47.487",
                "updatedAt": "2017-01-17T11:26:47.487"
            },
            ...
        ]
    }
```

This endpoint allows you to get information on all other sizes within the model of the specified tire size id.

### HTTP Request

`GET
https://api.tirelibrary.com/v1/data/sizes/:id/otherSizes`

<aside class="notice">
Requires a Developer plan with Tire Library API.
</aside>

### Query Parameters

Parameter | Description
--------- | -----------
id | Tire Size Id to be used to find the model and the other sizes within.

### Response Parameters

An array of Tire Size objects.

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The identifier for the given tire size within Tire Library.
itemNumber | string | The item number for the given tire size within Tire Library (can be used to search for sizes).
gmCode | string | A string containing the 
universalItemNumber | string | A string containing the
displayName | string | The display name for the specified tire size.
loadRange | string | A string containing the load carrying capability of a specified tire size.
traCode | string | A string containing the 
utqg | string | A string containing the
sidewall | string | A string containing the 
sectionWidth | double | A double containing the 
aspectRatio | double | A double containing the 
rimSize | double | A double containing the
inchWidth | double | A double containing the
diameter | double | A double containing the
metricRimDiameter | double | A double containing the
overallDiameter | double | A double containing the
loadRating | string | A string containing the relative load carrying capabilities of the tire size.
speedRating | string | A string containing the designed speed capability of the tire size.
plyRating | string | A string containing the amount of load the tire can safely carry at a specified inflation pressure.
starRating | string | A string containing the
loadCapacitySingle | string | A string containing the
loadCapacityDual | string | A string containing the
maxInflationPressure | string | A string containing the
weight | double | A double containing the
approvedRimWidth | string | A string containing the
measuringRimWidth | string | A string containing the
overallWidth | double | A double containing the
treadWidth | string | A string containing the 
treadDepth | double | A double containing the
loadedWidth | string | A string containing the
staticLoadedRadius | string | A string containing the
minimumDualSpacing | double | A double containing the
revolutionsPerMile | double | A double containing the
rollingCircumference | double | A double containing the
originCountry | string | A string containing the
warranty | string | A string containing the
upc | string | A string containing the universal product code for the tire size.
ean | string | A string containing the
asin | string | A string containing the
createdAt | string (datetime) | A string containing the date this object was created at.
updatedAt | string (datetime) | A string containing the last date this object was updated at.