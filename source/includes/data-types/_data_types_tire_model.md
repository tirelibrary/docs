## Tire Model

Contains all data related to a specific Tire Model. Used throughout multiple
endpoints across Tire Library API.

### Parameters

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
make | [Tire Make](https://developer.tirelibrary.com/#tire-make) | The make object this tire model is linked to.
classes | array of objects | An array of all subclasses pertaining to this tire model object.