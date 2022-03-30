---
description: >-
  This page answers frequently asked questions about Object Category and Object
  Category Definition.
---

# FAQs

### How to create an object category definition?

In order to [create object category definition](http://docs.sunbird.org/latest/apis/objectcategory/#operation/Create%20Object%20Category%20Definition), master category of the primary category should be created first.

### Can I change datatype of a property using object category definition?

No, datatype of a property cannot be changed. Only, property value range list and default value of a property can be updated using the [object category definition API](http://docs.sunbird.org/latest/apis/objectcategory/#operation/Update%20Object%20Category%20Definition).

### Is it mandatory to mention all properties of object schema during object category definition creation?

No, only necessary properties to be overriden can be mentioned.

### Can I add new properties to object schema using object category definition instead of schema.json?

Yes, new properties can be added to object category definition.

### How to fetch list of primaryCategories defined/configured in the System?

List of configured primary categories can be fetched using '[Composite Search API](http://docs.sunbird.org/latest/apis/searchapi/#operation/Composite%20Search)'.\
`{ "request": { "filters": { "status": [], "objectType":["ObjectCategoryDefintion","ObjectCategory"] }, "limit": 100, "sortby": "Desc" } }`
