# Changelog

## 30/08/2017

### Changes

* The following endpoints have been updated and now can receive extra parameters for better search filtering:
  * [Search Sizes (General)](https://developer.tirelibrary.com/#search-sizes-general-):
    * Now receives `filters` which can consist of any field to improve search results; and
    * Also accepts `page` and `pageSize` to define the amount of results to be returned on a per-search basis.
  * [Search Sizes (Sizes Only)](https://developer.tirelibrary.com/#search-sizes-sizes-only-):
    * Now receives `sectionWidth`, `aspectRatio` and `rimSize` to better search tires by size specifically;
    * Also accepts `page` and `pageSize` to define the amount of results to be returned on a per-search basis; and
    * Can take in the `all` parameter (defaulted to `false`) to retrieve all fields for the results as opposed to just the usual set.

## 09/08/2017

### Breaking Changes

* The `Max Inflation Pressure` field for Tire Sizes is now an integer as opposed to a string. The following endpoints make use of this object:
  * Get All Sizes;
  * Get Size by Id;
  * Get other Tire Sizes in Model by Tire Size Id; and
  * Get Model Sizes by Model Id.

## 07/08/2017

### Changes

* The Get All Makes endpoint (`data/makes`) now takes in an optional `all` parameter, this will retrieve all makes in one go as opposed to multiple pages / requests. Sample: `data/makes?all=true`.
* The mapping endpoint `Mapping via CSV` with url `https://api.tirelibrary.com/v1/mapping/results/package/:packageId/upload` has been deprecated and will be removed on the 31st of October;
* A new version of `Mapping via CSV` has been added at the url `https://api.tirelibrary.com/v1/mapping/execute.csv`. This endpoint now accepts an `Options` object (via JSON) containing all the settings required for Mapping and a `Files` header containing the CSV file with the required fields. You are also able to retrieve extra fields from Tire Library API and to map your items using different modes.

## 15/07/2017

### Breaking Changes

* The mapping endpoint `Mapping via JSON` with url `https://api.tirelibrary.com/v1/mapping/results/package/:packageId` has been deprecated and will be removed on the 31st of October;
* A new version of `Mapping via JSON` has been added at the url `https://api.tirelibrary.com/v1/mapping/execute.json`. This endpoint now accepts an `Options` object containing all the settings required for Mapping, you are also able to retrieve extra fields from Tire Library API and to map your items using different modes; and
* The mapping process is now in Beta! Tokenization is still undergoing improvements and will be added in the coming weeks.

## Archived
### 28/06/2017

### Changes

* The `templates/datasheets/:id` endpoint is now stable and has been re-added to the documentation.

### 12/06/2017

### Breaking Changes

* The following endpoints have been temporarily removed and will be made available once they reach a stable version:
  * `data/models/:id/rebates`;
  * `data/rebates`;
  * `data/rebates/:id`; and
  * `templates/datasheets/:id`.

### Changes

* The following endpoints had their `responses` updated:
  * `data/sizes`;
  * `data/sizes/:id`;
  * `data/sizes/:id/otherSizes`;
  * `data/models/:id/sizes`;
  * `data/classes`;
  * `data/classes/:id/subclasses`;
  * `data/subclasses`; and
  * `data/subclasses/:id/model`.
* The updates include:
  * Addition of `upc`, `asin`, `ean`, `treadWidth`, `loadedRadius` and `staticLoadedRadius` fields for Tire Sizes;
  * Renaming `classGroups` to `classes` and their respective singular forms within the classes and subclasses endpoints; and
  * The urls for subclass-related endpoints have been updated to have actual data being retrieved.

### 12/05/2017

### New Features

* The three steps of the mapping process via JSON and CSV are now optional and can be toggled off and on as required. Tokenization is undergoing performance improvements.
  * The JSON endpoint receives these options as part of the request; and
  * The CSV endpoint receives these options as part of the headers.

### Breaking Changes

* The following endpoints have been **renamed**:
  * Mapping via JSON: `/mapping/results/:userId/package/:packageId` -> `/mapping/results/package/:packageId`
  * Mapping via CSV: `/mapping/results/:userId/package/:packageId/upload` -> `/mapping/results/package/:packageId/upload`

* The following endpoint **requests** / **responses** have been changed:
  * `/mapping/results/package/:packageId` Mapping via JSON.

* The following properties have been **removed** in some endpoints:
  * `/mapping/results/package/:packageId` Mapping via JSON endpoint:
    * No longer retrieves `productCode` and `possibleMakes`.
  * `/mapping/results/package/:packageId/upload` Mapping via CSV endpoint:
    * No longer retrieves `productCode` and `possibleMakes`.

### 02/05/2017

### New Features

* The following endpoints have been **added**:
  * `mapping/results/:userId/package/:packageId`;
    * Allows the execution of rules and verification of tires via the Mapping API based on a specific user and package. Objects must be sent via a JSON request.
  * `mapping/results/:userId/package/:packageId/upload`;
    * Allows the execution of rules and verification of tires via the Mapping API based on a specific user and package. Objects must be sent via a CSV file.

### 27/04/2017

### Breaking Changes

* The following endpoints have been **renamed**:
  * `/data/classgroup` -> `/data/classes`
    * `/data/classgroup/:id` -> `/data/classes/:id`
    * `/data/classgroup/:id/subclass` -> `/data/classes/:id/subclasses`
  * `/data/subclass` -> `/data/subclasses`
    * `/data/subclass/:id` -> `/data/subclasses/:id`
    * `/data/subclass/:id/models` -> `/data/subclasses/:id/models`

* The following properties have been **removed / renamed** in some endpoints:
  * `/data/subclasses/:id/models` endpoint:
    * No longer retrieves `tireModelId`; and
    * `tireModels` property has been renamed to `models`.
  * `/data/models/:id` endpoint:
    * No longer retrieves `classGroupId`, `tireModelClasses` and `classGroup`.
  * All endpoints with `subClass` as a property in the response:
    * `subClass` has been renamed to `subclass`.


### 21/04/2017

### New Features

* Added Ruby samples to all endpoints except `Rebates`, tested on Ruby 2.3 and 2.4.
