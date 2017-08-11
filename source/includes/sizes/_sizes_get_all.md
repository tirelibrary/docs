## Get All Sizes

```csharp
    HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("https://api.tirelibrary.com/v1/")
    }

    client.DefaultRequestHeaders.Add("X-API-KEY", "YourApiKeyHere");

    // Hitting the endpoint.
    object response = Newtonsoft.Json.JsonConvert.DeserializeObject
        (await client.GetStringAsync("data/sizes"));
```

```ruby
    require 'net/http'
    
    uri = URI('https://api.tirelibrary.com/v1/data/sizes')

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
        "totalPages": 563,
        "length": 300,
        "timeTaken": "0.166 seconds",
        "sizes": [
            {
                "id": 33973,
                "itemNumber": "00004",
                "gmCode": null,
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
                "maxInflationPressure": 35,
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
                "updatedAt": "2017-01-17T11:26:47.487",
                "model": {
                    "id": 2,
                    "name": "TIGER PAW XTM",
                    "description": "All-Season Passenger Car tire.",
                    "benefits": "* Good value and long tread life\r\n* Smooth ride",
                    "features": "* Raised White Letter\r\n* Built with Uniroyal's DuraShield construction",
                    "manufacturerUrl": null,
                    "videoUrl": null,
                    "imageUrl": "https://linktoimagewillbehere",
                    "rotationImageUrls": null,
                    "make": {
                        "id": 2,
                        "name": "UNIROYAL",
                        "imageUrl": "https://linktoimagewillbehere",
                        "dotRegUrl": "http://linkwillbehere"
                    }
                }
            },
            ...
        ]
    }
```

This endpoint allows you to get all tire sizes and their information.

### HTTP Request

`GET
https://api.tirelibrary.com/v1/data/sizes`

<aside class="notice">
Requires a Developer plan with Tire Library API.
</aside>

### Response Parameters

An array of Tire Size objects.

#### Tire Size Object Parameters

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The identifier for the given tire size within Tire Library.
itemNumber | string | The item number for the given tire size within Tire Library (can be used to search for sizes).
gmCode | string | A string containing the 
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
maxInflationPressure | integer | An integer containing the
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
model | object | The model object this tire size is linked to. Parameters are outlined below.

#### Tire Model Object Parameters

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
make | object | The make object this tire model is linked to. Parameters are outlined below.

#### Tire Make Object Parameters

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The identifier for the given make within Tire Library.
name | string | The name of the given make.
imageUrl | string | The link to the image of a given make.
dotRegUrl | string | The link to the Department of Transport Registration for a given make.