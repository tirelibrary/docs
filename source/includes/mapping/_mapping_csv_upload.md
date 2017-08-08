## Mapping via CSV Upload

```csharp
  Will be added soon.
```

```php
  Will be added soon.
```

```ruby
  Will be added soon.
```

> The result for this endpoint is a **CSV file** containing the Mapped Code Object Parameters as described in the information on the side.

This endpoint allows you to execute mapping via uploading a CSV file on a specific set of data with a given package.

### HTTP Request

`POST
https://api.tirelibrary.com/v1/mapping/execute.csv`

<aside class="notice">
Requires a Developer plan with Tire Library API and the Mapping Add-on.
</aside>

<aside class="warning">
Tokenization is currently undergoing performance improvements.
</aside>

### Request Body

A CSV file containing the Mapping Objects must be sent in order for data to be mapped. The CSV must only contain the following fields:

* **Unmapped Code**: The default version of the item numbers / product codes before being mapped; and
* **Make**: The make this specific code is linked to. 

With the exception of `packageId`, all other parts of the mapping process are now optional:

  * `packageId`: The id of the package to be used for mapping;
  * `executeRules`: Applies mapping rules to the set of mappingObjects received;
  * `executeVerification`: Matches valid codes to Tire Library's Data;
  * [Disabled] `executeTokenization`: Generates Specification Links for detailed information about objects;
  * `mappingMode`: The method to use to map the requested objects, a list of the available modes is outlined below; and
  * `fields`: The list of extra fields you would like to retrieve from Tire Library API.
  
The Request Body must contain a **files** key with a single file and it must be of type CSV according to the fields above.

The Request Body must be in the following format for the process to work:

```json
{
  "options": {
    "executeRules": "true",
    "executeVerification": "true",
    "executeTokenization": "false",
    "mappingMode": 1,
    "packageId": 1,
    "fields": [
      "gmcode", "aspectRatio"
    ]
  }
}
```

### Response Parameters

A comma-delimited file containing the Mapped Code Object Parameters separated into columns (alongside any extra fields requested).

#### Mapped Code Object Parameters

Parameter | Type | Description
--------- | ---- | -----------
unmappedCode | string | The original code sent to the API prior to the execution of rules.
make | string | The make to be used in the search for a specific tire for mapping.
flag | integer | The status of the code after the execution of rules and Tire Library verification. A thorough list of flags and their meaning has been provided below.
tireLibraryMakeId | integer | The id of the matching make of the mapped code in Tire Library. Null if no perfect match was found.
tireLibraryMake | string | The name of the make found to match the tire in question in Tire Library. Null if no perfect match was found.
tireLibraryId | integer | The id pertaining to the specified tire if the matching was successful. Empty if no match was found.
mappedCode | string | The final code after the execution of rules within the given package.
specUrl | string | The url pointing to the specifications page for the matched tire if found.

#### Modes

You can now select the mapping mode you would like to use:

Mode Code | Title | Description
---------- | ----- | -----------
1 | Default | Default mapping mode, uses UnmappedCode and Makes to determine matches.
2 | ItemNumberAndTireSize | Makes use of UnmappedCode and Tire Size (under the "Extra" field) to match items. This is not as accurate as the default method and takes a longer time to finalize. You must have the **Extra** column containing the Tire Size in your CSV.

#### Flags

Flag Code | Modes | Description
--------- | ----- | -----------
0 | All | Empty code, mapped code was empty.
1 | ItemNumberAndTireSize | Multiple item number matches were found but we could not ascertain the correct make.
2 | All | Invalid code, no perfect match was found.
3 | All | Valid Code, a perfect match was found.
4 | All | Valid Possible Duplicate Size, this means that a valid match was found but there was a duplicate in Tire Library and we were unable to specify the correct one.
5 | All | Valid Duplicate Entry In Csv, duplicate items were found in the csv, if a result was found, all will receive the same Tire Library details.
6 | ItemNumberAndTireSize | Partial Match, this means results were returned during the search but none matched the Item Number and Tire size combination.

#### Extra Fields

Field Code | Title
---------- | -----
gmcode | GM Code
upc | Universal Product Code
ean | EAN
asin | ASIN
loadrange | Load Range
tracode | TRA Code
utqg | UTQG
sidewall | Sidewall
sectionwidth | Section Width
aspectratio | Aspect Ratio
rimsize | Rim Size
inchwidth | Inch Width
diameter | Diameter
metricrimdiameter | Metric Rim Diameter
overalldiameter | Overall Diameter
loadrating | Load Rating
speedrating | Speed Rating
plyrating | Ply Rating
starrating | Star Rating
loadcapacitysingle | Load Capacity Single
loadcapacitydual | Load Capacity Dual
maxinflationpressure | Max Inflation Pressure
weight | Weight
approvedrimwidth | Approved Rim Width
measuringrimwidth | Measuring Rim Width
overallwidth | Overall Width
treaddepth | Tread Depth
minimumdualspacing | Minimum Dual Spacing
revolutionspermile | Revolutions Per Mile
rollingcircumference | Rolling Circumference
origincountry | Origin Country
warranty | Warranty
treadwidth | Tread Width
loadedwidth | Loaded Width
staticloadedradius | Static Loaded Radius