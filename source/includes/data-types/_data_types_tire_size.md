## Tire Size

Contains all data related to a specific Tire Size. Used throughout multiple
endpoints across Tire Library API.

### Parameters

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The identifier for the given tire size within Tire Library.
itemNumber | string | The item number for the given tire size within Tire Library (can be used to search for sizes).
tireModelId | integer | The identifier for the Tire Model this Tire Size is part of.
gmCode | string | A string containing the 
displayName | string | The display name for the specified tire size.
loadRange | string | The load carrying capability of a specified tire size.
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
loadRating | string | The relative load carrying capabilities of the tire size.
speedRating | string | The designed speed capability of the tire size.
plyRating | string | The amount of load the tire can safely carry at a specified inflation pressure.
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
originalEquipment | boolean | Outlines if this tire size is an original equipment (produced alongside a specific vehicle) or not.
originalEquipmentNotes | string | Any notes required for the original equipment.
treadConstruction | string | A string containing the
numberOfLugs | int | An integer containing the
rimProtector | boolean | Outlines if this tire contains a rim protector or not.
upc | string | A string containing the universal product code for the tire size.
ean | string | A string containing the
asin | string | A string containing the
model | [Tire Model](https://developer.tirelibrary.com/#tire-model) | The model object this tire size is linked to.