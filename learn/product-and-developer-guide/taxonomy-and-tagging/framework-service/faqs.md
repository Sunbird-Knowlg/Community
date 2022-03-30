---
description: >-
  This page is used to address frequently asked questions about Framework
  service.
---

# FAQs

### **How to create a Framework?**

A Channel/Tenant can have one or more frameworks.

Prerequisite: “Master Categories” should be created while doing service deployment. Master Categories are the list of categories from which a new framework’s category should be mapped to.

A Framework can have its categories corresponding to all master categories or its subset. Framework Categories are linked to Master categories by using the 'code' value same as that of master categories.

Below are the steps to create a new framework:

1. [Create Framework](http://docs.sunbird.org/latest/apis/framework/#operation/FrameworkV1CreatePost)
2. [Create Framework categories](http://docs.sunbird.org/latest/apis/framework/#operation/FrameworkV1CategoryCreatePost)
3. [Create Terms for each category](http://docs.sunbird.org/latest/apis/framework/#operation/FrameworkV1TermCreatePost)
4. [Publish the Framework](http://docs.sunbird.org/latest/apis/framework/#operation/publishFramework)

Each term can be associated with another term from another category by using 'associationswith' attribute in [Term update API](http://docs.sunbird.org/latest/apis/framework/#operation/FrameworkV1TermUpdateClass2Patch)

`Example: { "request": { "term": { "associationswith": [ { "identifier": "associatetermidentifier1" //Term you want to add association with }, { "identifier": "associatetermidentifier2" //Term you want to add association with } ] } } }`

'Level1-term', 'Level2-term' and 'Level3-term' can be created as map-trees under the framework category. 'Level1-concept’ is created as a term directly associated with framework category'. However, 'Level2-term' and 'Level3-term' are created as terms using the Term create API with reference to Parent.

`Example: { "request": { "term": { "name": "Sample Term", "label": "Sample Term", "description": "Sample Term", "code": "sampleTerm" //needs to be unique within a framework "index": 20 //index of term display "parents": [ { "identifier": "parentIdentifier" //Term you want to add association to } ] } } }`

[**API to create ‘Framework Master Category’:**](http://docs.sunbird.org/3.6.0/developer-docs/server-installation/knowledge-platform/#create-master-framework-category)

`curl --location --request POST '{{host}}/action/framework/v3/category/master/create'`\
`--header 'Content-Type: application/json'`\
`--header 'Authorization: Bearer {{APIKey}}'`\
`--header 'x-authenticated-user-token: {{user_token}}'`\
`--data-raw '{ "request": { "category":{ "name":"Learning Outcome", "description":"Learning Outcome", "code":"learningOutcome" } } }'`

\`\`

{% embed url="http://docs.sunbird.org/2.10.0/developer-docs/how-to-guide/how_to_create_framework_in_sunbird" %}

{% embed url="http://docs.sunbird.org/2.10.0/developer-docs/how-to-guide/how_to_seeddata_in_framework" %}

### How to fetch list of all Frameworks in the sunbird instance?

Using [Frameworks List API](http://docs.sunbird.org/latest/apis/framework/#operation/FrameworkV1ListPost), we can fetch all the existing frameworks in the application
