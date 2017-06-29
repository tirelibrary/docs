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

> The result for this endpoint is a CSV file containing the Mapped Code Object Parameters as described in the information on the side.

This endpoint allows you to execute mapping via uploading a CSV file on a specific set of data with a given package.

### HTTP Request

`POST
https://api.tirelibrary.com/v1/mapping/results/package/:packageId/upload`

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

Mapping Objects must be sent in order for data to be mapped. All parts of the mapping process are now optional and the following extra headers must be sent to specify which ones to be used:

  * `ExecuteRules` -> `true` / `false`;
    * Applies mapping rules to the set of mappingObjects received.
  * `ExecuteVerification` -> `true` / `false`; and
    * Matches valid codes to Tire Library's Data.
  * `ExecuteTokenization` -> `true` / `false`.
    * Generates Specification Links for detailed information about objects.
  
The Request Body must contain a **"file"** key and this file must be of type CSV. It must contain the following data:

UnmappedCode | Make
------------ | ----
CodeA | MakeX
CodeB | MakeY
CodeC | MakeX
... | ...

### Response Parameters

A comma-delimited file containing the Mapped Code Object Parameters separated into columns.

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