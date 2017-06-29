## Mapping via JSON

```csharp
  Will be added soon.
```

```php
  Will be added soon.
```

```ruby
  Will be added soon.
```

> The following sample represents the JSON response for this endpoint:

```json
  {
    "executeRules": true,
    "executeVerification": true,
    "executeTokenization": false,
    "timers": {
      "Process Title": 0
    },
    "mappedCodes": [
      {
        "unmappedCode": "2050",
        "make": "ceat",
        "flag": 3,
        "tireLibraryMakeId": 554,
        "tireLibraryMake": "CEAT",
        "tireLibraryId": 234718,
        "mappedCode": "2050",
        "specUrl": "https://LinkToSpecificationsOfThisTire"
      },
      ...
    ]
  }
```

This endpoint allows you to execute mapping via JSON on a specific set of Mapping Objects with a given package.

### HTTP Request

`POST
https://api.tirelibrary.com/v1/mapping/results/package/:packageId`

<aside class="notice">
Requires a Tire Mapping plan with Tire Library API.
</aside>

<aside class="warning">
Tokenization is currently undergoing performance improvements.
</aside>

### Query Parameters

Parameter | Description
--------- | -----------
packageId | The integer used to identify the rules package required to be used against the set of mapping objects.

### Request Body

Mapping Objects must be sent in order for data to be mapped. All parts of the process are now optional:

  * `executeRules`: Applies mapping rules to the set of mappingObjects received;
  * `executeVerification`: Matches valid codes to Tire Library's Data; and
  * `executeTokenization`: Generates Specification Links for detailed information about objects.

The Request Body must be in the following format for the process to work:

> The following request body sample must be followed for the correct behavior in the endpoint:

```json
{
  "executeRules": "true",
  "executeVerification": "true",
  "executeTokenization": "false",
  "entryData": [
    {
      "unmappedCode": "Your unmapped code prior to the execution of rules",
      "make": "Your make, must match data in Tire Library",
      "mappedCode": ""
    },
    ...
  ]
}
```

### Response Parameters

A list of Mapped Code objects with the parameters listed below as well as:

  * Timers containing the speed each process and inner process took in our servers;
  * ExecuteRules stating if the mapping rules for the provided package / user were applied;
  * ExecuteVerification stating if the matching process between mappedCodes and Tire Library data ran; and
  * ExecuteTokenization stating if the generation of Tire Library Specification tokens for quick links containing detailed information about each tire occurred.

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

#### Flags

Flag Code | Description
--------- | -----------
0 | Empty code, mapped code was empty.
2 | Invalid code, no perfect match was found.
3 | Valid Code, a perfect match was found.