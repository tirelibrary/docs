## Get Model Sizes by Model Id

```csharp
    HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("https://api.tirelibrary.com/v1/")
    }

    client.DefaultRequestHeaders.Add("X-API-KEY", "YourApiKeyHere");

    // Hitting the endpoint.
    object response = Newtonsoft.Json.JsonConvert.DeserializeObject
        (await client.GetStringAsync("data/models/2/sizes"));

    // The number in the query represents the Id of 
    // the Tire Model in question.
```

```ruby
    require 'net/http'
    
    # The number in the query represents the Id of the Tire Model in question.
    uri = URI('https://api.tirelibrary.com/v1/data/models/2/sizes')

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
        "length": 32,
        "timeTaken": "0.008 seconds",
        "sizes": [
            {
                "id": 33973,
                "itemNumber": "00004",
                "gmCode": null,
                "universalItemNumber": null,
                "displayName": "185/75R14  TIGER PAW XTM",
                "loadRange": null,
                "traCode": null,
                "utqg": "640 A B",
                "sidewall": "WW",
                "sectionWidth": 185,
                "aspectRatio": 75,
                "rimSize": 14,
                "inchWidth": null,
                "diameter": null,
                "metricRimDiameter": null,
                "overallDiameter": null,
                "loadRating": "89",
                "speedRating": "S",
                "plyRating": null,
                "starRating": null,
                "loadCapacitySingle": "1290",
                "loadCapacityDual": null,
                "maxInflationPressure": "35",
                "weight": null,
                "approvedRimWidth": null,
                "measuringRimWidth": null,
                "overallWidth": null,
                "treadWidth": null,
                "treadDepth": 9.5,
                "loadedWidth": null,
                "staticLoadedRadius": null,
                "minimumDualSpacing": null,
                "revolutionsPerMile": null,
                "rollingCircumference": null,
                "originCountry": null,
                "warranty": null,
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

This endpoint allows you to get information on all tire sizes within the model with the specified id.

### HTTP Request

`GET
https://api.tirelibrary.com/v1/data/models/:id/sizes`

<aside class="notice">
Requires a Developer plan with Tire Library API.
</aside>

### Query Parameters

Parameter | Description
--------- | -----------
id | Tire Model Id to be used to find the model and the tire sizes within.

### Response Parameters

An array of Tire Size objects.

#### Tire Size Object Parameters

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