# FAQ's

<details>

<summary>How to disable the "Add from Library" feature for a particular level/unit in the hierarchy? </summary>

There is a configuration to disable/enable the "Add from Library" feature at any level/unit in the hierarchy.\
Let's say you want to disable this feature for level1 and enable it for level2 then pass an empty  object value to level1 as below:\
`hierarchy.level1.children`

```
{
      "objectCategoryDefinition": {
        "objectMetadata": {
          "config": {
            "sourcingSettings": {
              "collection": {
                "maxDepth": 2,
                "objectType": "Collection",
                "primaryCategory": "Digital Textbook",
                "isRoot": true,
                "iconClass": "fa fa-book",
                "children": {},
                "hierarchy": {
                  "level1": {
                    "name": "Textbook Unit",
                    "type": "Unit",
                    "mimeType": "application/vnd.ekstep.content-collection",
                    "contentType": "TextBookUnit",
                    "primaryCategory": "Textbook Unit",
                    "iconClass": "fa fa-folder-o",
                    "children": {}
                  },
                  "level2": {
                    "name": "Section",
                    "type": "Unit",
                    "mimeType": "application/vnd.ekstep.content-collection",
                    "contentType": "TextBookUnit",
                    "primaryCategory": "Textbook Unit",
                    "iconClass": "fa fa-folder-o",
                    "children": {
                      Content: [
                        'Explanation Content',
                        'Learning Resource',
                        'eTextbook',
                        'Teacher Resource',
                        'Course Assessment'
                      ]
                    }
                  }
                }
              }
            }
          },
          "schema": {
            ....
          }
        },
        "forms": {
          ....
        }
      }
    }
}
```

</details>

<details>

<summary>How to use collection editor with frameworks (Angular, React, Vue, etc.)?</summary>

Currently, we are only supporting angular framework, not others frameworks likes react, Vue.\
For angular, Please refer to the [README](https://github.com/Sunbird-Ed/sunbird-collection-editor/tree/release-4.8.0#readme).md of the [git repository](faqs.md#git-repo)

</details>

<details>

<summary>How to enable an asset Drag&#x26;Drop?</summary>

The `Drag&Drop` features are enabled by default in the collection editor builds.

</details>

<details>

<summary>How to get an API key?</summary>

To be updated.....

</details>

<details>

<summary>How to configure a new metadata field and define its attributes in the collection editor?</summary>

The config for new fields has to be added in the object category definition. This can be done at the system level or at the individual channel level.

Suppose you want to add a name field in the metadata field, it can be added as:

```
"objectCategoryDefinition": {
    "identifier": "obj-cat:digital-textbook_collection_all",
    "objectMetadata": {
        "config": {
            ...
            ...
        },
        ...
        ...
    },
    ...
    "name": "Digital Textbook",
    "forms": {
        "create": {
            ...
            ...
            "properties": [
                {
                    "code": "name",
                    "dataType": "text",
                    "description": "Name of the collection",
                    "editable": true,
                    "inputType": "text",
                    "label": "Name",
                    "name": "Name",
                    "placeholder": "Enter name of the collection",
                    "renderingHints": {
                        "class": "sb-g-col-lg-1 required"
                    },
                    "required": true,
                    "visible": true,
                    "validations": [
                        {
                            "type": "maxLength",
                            "value": "120",
                            "message": "Input is Exceeded"
                        },
                        {
                            "type": "required",
                            "message": "Name is required"
                        }
                    ]
                }
            ]
        }
    }
}
```

</details>

<details>

<summary>How to configure Section Level configurations?</summary>

Attributes/collection behavior can be modified based on the unit level as well. It can be updated in the object category definition of the collection under the unit metadata form. Under unit metadata, the attributes or the behavior can be defined. Each field has a code and it can be updated with the collection configuration.\
Here's the sample configuration for the Digital textbook:

```
{
   "objectCategoryDefinition":{
      "identifier":"obj-cat:digital-textbook_collection_all",
      "objectMetadata":{
         "config":{
            ...
         },
         "schema":{
            ...
         }
      },
      "name":"Digital Textbook",
      "forms":{
         "unitMetadata":{
            "templateName":"",
            "required":[
               
            ],
            "properties":[
               {
                  "name":"First Section",
                  "fields":[
                     {
                        "code":"name",
                        "dataType":"text",
                        "description":"Name of the content",
                        "editable":true,
                        "inputType":"text",
                        "label":"Title",
                        "name":"Title",
                        "placeholder":"Title",
                        "renderingHints":{
                           "class":"sb-g-col-lg-1 required"
                        },
                        "required":true,
                        "visible":true,
                        "validations":[
                           {
                              "type":"maxLength",
                              "value":"120",
                              "message":"Input is Exceeded"
                           },
                           {
                              "type":"required",
                              "message":"Title is required"
                           }
                        ]
                     },
                     {
                        "code":"description",
                        "dataType":"text",
                        "description":"Description of the content",
                        "editable":true,
                        "inputType":"textarea",
                        "label":"Description",
                        "name":"Description",
                        "placeholder":"Description",
                        "renderingHints":{
                           "class":"sb-g-col-lg-1"
                        },
                        "required":false,
                        "visible":true,
                        "validations":[
                           {
                              "type":"maxLength",
                              "value":"256",
                              "message":"Input is Exceeded"
                           }
                        ]
                     },
                     {
                        "code":"keywords",
                        "visible":true,
                        "editable":true,
                        "dataType":"list",
                        "name":"Keywords",
                        "renderingHints":{
                           "class":"sb-g-col-lg-1"
                        },
                        "description":"Keywords for the content",
                        "inputType":"keywords",
                        "label":"Keywords",
                        "placeholder":"Input the keyword and PRESS enter",
                        "required":false,
                        "validations":[
                           
                        ]
                     },
                     {
                        "code":"topic",
                        "visible":true,
                        "depends":[
                           
                        ],
                        "editable":true,
                        "dataType":"list",
                        "renderingHints":{
                           
                        },
                        "name":"Topic",
                        "description":"Choose a Topics",
                        "index":11,
                        "inputType":"topicselector",
                        "label":"Topics",
                        "placeholder":"Choose Topics",
                        "required":false,
                        "validations":[
                           
                        ]
                     }
                  ]
               }
            ]
         }
      }
   }
}
```

</details>

<details>

<summary>How to filter specific contents in the "Add from Library" Page?</summary>



</details>
