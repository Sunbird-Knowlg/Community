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

1. [Create Framework](https://documenter.getpostman.com/view/25463377/2s8ZDa32ay#1114f15b-a5af-44bc-a390-004b35d25efd)
2. [Create Framework categories](https://documenter.getpostman.com/view/25463377/2s8ZDa32ay#7b07da54-506c-410e-a263-63d3b5522f38)
3. [Create Terms for each category](https://documenter.getpostman.com/view/25463377/2s8ZDa32ay#43c4fb52-a4d6-486c-beec-6c262571bf4a)
4. [Publish the Framework](https://documenter.getpostman.com/view/25463377/2s8ZDa32ay#eb30e906-51f6-4aa1-9161-0a58b0c2126e)

Each term can be associated with another term from **another category** by using _'associationswith'_ attribute in [Term update API](https://documenter.getpostman.com/view/25463377/2s8ZDa32ay#f16ade99-c9cd-4055-a251-5d8c996e3258)

`Example: { "request": { "term": {`` `**`"associationswith": [ { "identifier": "associatetermidentifier1"`**` ``//Term you want to add association with`` `**`}, { "identifier": "associatetermidentifier2"`**` ``//Term you want to add association with`` `**`} ]`**` ``} } }`

'Level1-term', 'Level2-term' and 'Level3-term' can be created as treemap under the framework category. 'Level1-term’ is created as a term directly associated with framework category. However, 'Level2-term' and 'Level3-term' are created as terms using the Term create API with reference to parent using _'parents'_ attribute in [Term create API](https://documenter.getpostman.com/view/25463377/2s8ZDa32ay#43c4fb52-a4d6-486c-beec-6c262571bf4a).

`Example: { "request": { "term": { "name": "Sample Term", "label": "Sample Term", "description": "Sample Term", "code": "sampleTerm" //needs to be unique within a framework "index": 20 //index of term display`` `**`"parents": [ { "identifier": "parentIdentifier"`**` ``//Term you want to add association to`` `**`} ]`**` ``} } }`

[**API to create ‘Framework Master Category’:**](https://documenter.getpostman.com/view/25463377/2s8ZDa32ay#2985d446-cd84-497a-b7dd-d965be66c6bf)

```
curl --location --request POST '{{host}}/action/framework/v3/category/master/create'
--header 'Content-Type: application/json'
--header 'Authorization: Bearer {{APIKey}}'
--header 'x-authenticated-user-token: {{user_token}}'
--data-raw '{"request":{"category":{"name":"Learning Outcome","description":"Learning Outcome","code":"learningOutcome","targetIdFieldName":"targetLearningOutcomeIds","searchLabelFieldName":"se_learningOutcomes","searchIdFieldName":"se_learningOutcomeIds","orgIdFieldName":"learningOutcomeIds"}}}'
```



{% embed url="http://docs.sunbird.org/2.10.0/developer-docs/how-to-guide/how_to_create_framework_in_sunbird" %}

{% embed url="http://docs.sunbird.org/2.10.0/developer-docs/how-to-guide/how_to_seeddata_in_framework" %}

### How to fetch list of all Frameworks in the sunbird instance?

Using [Frameworks List API](https://documenter.getpostman.com/view/25463377/2s8ZDa32ay#728e3b5e-18ab-4a14-8b54-b4ab9ed4eb90), we can fetch all the existing frameworks in the application
