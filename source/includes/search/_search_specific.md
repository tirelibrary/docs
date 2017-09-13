## Get Specific Size

```csharp
    HttpClient client = new HttpClient
    {
        BaseAddress = new Uri("https://api.tirelibrary.com/v1/")
    }

    client.DefaultRequestHeaders.Add("X-API-KEY", "YourApiKeyHere");

    // Hitting the endpoint.
    object response = Newtonsoft.Json.JsonConvert.DeserializeObject
        (await client.GetStringAsync("search/specific?make=bridgestone&itemnumber=000009"));
```

```ruby
    require 'net/http'
    
    uri = URI('https://api.tirelibrary.com/v1/search/specific')

    # Adding the search parameter to the URI.
    uri.query = URI.encode_www_form(make: 'bridgestone',
                                    itemnumber: '000009')

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
        "tire": {
            "id": 33972,
            "itemNumber": "000009",
            "tireModelId": null,
            "gmCode": "89049447",
            "displayName": "245/50R18 TURANZA EL42 RFT",
            "loadRange": null,
            "traCode": null,
            "utqg": "140 A A",
            "sidewall": "BL",
            "sectionWidth": 245.0,
            "aspectRatio": 50.0,
            "rimresult": 18.0,
            "inchWidth": null,
            "diameter": null,
            "metricRimDiameter": null,
            "overallDiameter": 27.8,
            "loadRating": "100",
            "speedRating": "V",
            "plyRating": null,
            "starRating": null,
            "loadCapacitySingle": null,
            "loadCapacityDual": null,
            "maxInflationPressure": null,
            "weight": 36.0,
            "approvedRimWidth": null,
            "measuringRimWidth": null,
            "overallWidth": 10.0,
            "treadWidth": null,
            "treadDepth": 11.0,
            "loadedWidth": null,
            "staticLoadedRadius": null,
            "minimumDualSpacing": null,
            "revolutionsPerMile": 749.0,
            "rollingCircumference": null,
            "originCountry": null,
            "warranty": null,
            "originalEquipment": false,
            "originalEquipmentNotes": null,
            "dotTinCode": null,
            "treadConstruction": null,
            "numberOfLugs": null,
            "rimProtector": false,
            "upc": null,
            "ean": null,
            "asin": null,
            "model": {
                "id": 73,
                "name": "TURANZA EL42",
                "description": "All Season Passenger Car Touring tire for Use on Sporty Coupes, Luxury Sedans as well as CUVs and Family Minivans. Original Equipment (OE) tire on Select Vehicles.",
                "benefits": "* For reliable all season traction\r\n* Evacuate water out from tire footprint to reduce hydroplaning and enhance wet traction\r\n* Help stabilize the tread area and enhance treadwear, handling and durability\r\n* Provides a smooth ride",
                "features": "* All Season tread compound\r\n* Symmetrical tread design featuring siped rectangular tread blocks\r\n* Lateral and circumferential tread grooves\r\n* Reinforced twin steel belts\r\n* Polyester cord body ply\r\n* Buy & Try 30 Day Guarantee\r\n* Platinum Pact Limited Warranty",
                "manufacturerUrl": null,
                "videoUrl": null,
                "imageUrl": "https://imagelinkwillbehere",
                "rotationImageUrls": null,
                "make": {
                    "id": 1,
                    "name": "BRIDGESTONE",
                    "imageUrl": "https://imagelinkwillbehere",
                    "dotRegUrl": "http://www.bridgestonetire.com/customer-care/tire-registration"
                }
            }
        }
    }
```

This endpoint allows you to search for a specific size based on a Make and an Item Number.

### HTTP Request

`GET
https://api.tirelibrary.com/v1/search/specific`

<aside class="notice">
Requires a Developer plan with Tire Library API.
</aside>

### Query Parameters

Parameter | Type | Required | Default | Description
--------- | ---- | -------- | ------- | -----------
make | string | Yes | - | The make to be used in the search.
itemNumber | string | Yes | - | The item number to be used in the search.

### Response Parameters

Parameter | Type | Description
--------- | ---- | -----------
tire | [Tire Size](https://developer.tirelibrary.com/#tire-size) | The tire size object.