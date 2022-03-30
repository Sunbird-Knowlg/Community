---
description: This page addresses frequently asked questions about Composite Search API.
---

# FAQs

### Samples of how to use filter operators in composite search API?

**Sample 1** - Find all node types that contain specific search term (content, words, assets)

{ "request": { "query":"elephant", "limit":10 } }

**Sample 2** - Find only TextBook

{ "request": {"filters":{"primaryCategory":"Digital Textbook"}, "limit":10 } }

**Sample 3** - Find "Explanation Content" less than 1MB

{ "request": {"filters":{"primaryCategory":"Explanation Content", "size": {"<=" : "1000000"\}}, "limit":10 } }

**Sample 4** - Find resources whose 'name' starts with "A" (e.g. for alphabetic navigation)

{ "request": { "filters": { "primaryCategory":"Explanation Content", "name": { "startsWith": "A" } } } }

**Sample 5** - Find resources without 'appIcon'

{ "request": { "filters": { "primaryCategory":"Explanation Content" }, "not\_exists":\["appIcon"] } }

**Sample 6** - Find resources with 'appIcon'

{ "request": { "filters": { "primaryCategory":"Explanation Content"}, "exists":\["appIcon"] } }

**Sample 7** - Find resources and aggregate results by 'language' and 'subject'

{ "request": { "filters": { "primaryCategory":"Explanation Content"}, "facets":\["language","subject"] } }

**Sample 8** - Find resources and sort results by name ascending and size desc

{ "request": { "filters": { "primaryCategory":"Explanation Content"}, "sort\_by":{"name":"asc", "size":"desc"} } }

**Sample 9** - Get first 10 results

{ "request": { "filters": { "primaryCategory":"Explanation Content"}, "sort\_by":{"name":"asc", "size":"desc"}, "offset": 0, "limit": 10 } }

**Sample 10** - Get 4th page of results. Results from 30 - 40 index.

{ "request": { "filters": { "primaryCategory":"Explanation Content"}, "sort\_by":{"name":"asc", "size":"desc"}, "offset": 30, "limit": 10 } }

**Sample 11** - Get the fields specified.

{ "request": { "filters": { "primaryCategory":"Explanation Content"}, "exists":\["appIcon"], "fields":\["name","description","identifier","mimeType","createdOn"] } }

**Sample 12** - Search for content with soft constraints

{ "request": { "filters": { "objectType": \["Content"], "primaryCategory": \["Explanation Content"], "gradeLevel" : \["Grade 1"], "ageGroup" : \["5-6"], "status": \["Live"] }, "mode" : \["soft"], "softConstraints": {"ageGroup" : 2, "gradeLevel" : 3 } } }

**Sample 13** - Find "Explanation Content" created between a time range

{ "request": { "filters": { "primaryCategory":"Explanation Content", "createdOn": {">=":"2020-07-28T01:27:16.559+0000", "<":"2021-10-28T01:27:16.559+0000"} }, "sort\_by":{"name":"asc"}, "offset": 0, "limit": 10 } }

**Sample 14** - Find published Textbooks to which a content is linked to

{ "request": { "filters": { "primaryCategory":"Digital Textbook", "leafNodes": {"contains": "do\_Id\_\_\_content"} }, "sort\_by":{"name":"asc"} } }

### What are the different modes that can be passed in search request?

There are 2 modes in search. 'soft' and 'collection' mode. By default, mode is 'soft' in a search request if the same is not specified. When the mode is specified as 'collection', then the search result will contain 'collections' block which will have the metadata of collections of the collection units that is part of the search result

Example:

```
curl --location --request POST 'https://dev.sunbirded.org//api/content/v1/search' \
--header 'Content-Type: application/json' \
--data-raw '{
    "request": {
        "filters": {
            "status":["Live"],
            "visibility": ["Default","Parent"],
            "dialcodes":["BBU2JE"]
        },
        "mode": "Collection"
    }
}'


Response:
"result": {
        "collections": [
            {
                "identifier": "do_31277376449209958415961",
                "subject": [
                    "Mathematics"
                ],
                "childNodes": [
                    "do_31277376466550784015998"
                ],
                "mimeType": "application/vnd.ekstep.content-collection",
                "medium": [
                    "English"
                ],
                "objectType": "Collection",
                "gradeLevel": [
                    "Class 9"
                ],
                "appIcon": "https://ntpproductionall.blob.core.windows.net/ntp-content-production/content/do_31277376449209958415961/artifact/9-maths_1527603481839.thumb.jpg",
                "size": 2660278,
                "name": "B566_STD_9_MATHS_EM_FULL",
                "contentType": "TextBook",
                "board": "State (Tamil Nadu)",
                "resourceType": "Book"
            }
        ],
        "count": 1,
        "content": [
            {
                "parent": "do_31277376466550784016000",
                "code": "do_31277376466550784015998",
                "purpose": "HS",
                "channel": "01235953109336064029450",
                "downloadUrl": "https://ntpproductionall.blob.core.windows.net/ntp-content-production/ecar_files/do_31277376449209958415961/b566_std_9_maths_em_full_1602760532721_do_31277376449209958415961_7.0_spine.ecar",
                "description": "B566U2P63HS",
                "mimeType": "application/vnd.ekstep.content-collection",
                "variants": {
                    "online": {
                        "ecarUrl": "https://ntpproductionall.blob.core.windows.net/ntp-content-production/ecar_files/do_31277376449209958415961/b566_std_9_maths_em_full_1602760535048_do_31277376449209958415961_7.0_online.ecar",
                        "size": 178355
                    },
                    "spine": {
                        "ecarUrl": "https://ntpproductionall.blob.core.windows.net/ntp-content-production/ecar_files/do_31277376449209958415961/b566_std_9_maths_em_full_1602760532721_do_31277376449209958415961_7.0_spine.ecar",
                        "size": 2660278
                    }
                },
                "leafNodes": [
                    "do_31283041754486374417786",
                    "do_31283041255128268819778"
                ],
                "createdOn": "2019-05-31T10:10:44.520+0000",
                "objectType": "Content",
                "primaryCategory": "Textbook Unit",
                "children": [
                    "do_31283041255128268819778",
                    "do_31283041754486374417786"
                ],
                "lastUpdatedOn": "2020-10-15T11:15:24.872+0000",
                "contentType": "TextBookUnit",
                "dialcodeRequired": "Yes",
                "identifier": "do_31277376466550784015998",
                "lastStatusChangedOn": "2019-05-31T10:10:44.520+0000",
                "audience": [
                    "Student"
                ],
                "visibility": "Parent",
                "index": 5,
                "languageCode": [],
                "graph_id": "domain",
                "nodeType": "DATA_NODE",
                "pkgVersion": 7,
                "versionKey": "1559297444520",
                "framework": "tn_k-12_5",
                "dialcodes": [
                    "BBU2JE"
                ],
                "depth": 2,
                "lastPublishedOn": "2020-10-15T11:15:30.038+0000",
                "compatibilityLevel": 1,
                "leafNodesCount": 2,
                "name": "2.6.2 Laws of Radicals",
                "status": "Live",
                "node_id": 0
            }
        ],
        "collectionsCount": 1
    }
```

In the above example 'Response',

"collections" block gives the information of the **TextBook** that contains the 'TextBookUnit' to which DIAL Code is tagged to. "identifier" - id of the TextBook, "name" - name of the TextBook, "board" - board value to which TextBook is tagged to. similarly, "medium", "gradeLevel" (Class) and "subject" values.

"content" block gives the information of the **TextBook Unit** DIAL Code is tagged to. "identifier" - id of the TextBook Unit, "name" - name of the TextBook Unit, "topic" - topics/concepts to which Unit is tagged with.

### What is 'softConstraints' in search request?

'softConstraints' is used to fetch results from ElasticSearch by boosting the relevance of a document based on a particular value of a field.
