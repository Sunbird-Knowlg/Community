---
description: HTML player is used to render the HTML type contents
---

# HTML-h5p Player - v1

**Configuration**

Based on the following configuration HTML content can be rendered.

```
{
    "context": {},
    "config": {
        "mimetypes": [ // Content mimetypes for new cotent lucnhers
            "application/vnd.ekstep.html-archive",
            "application/vnd.ekstep.h5p-archive"
        ],
        "contentLaunchers": [ // content laucher plugins for specific content mimetypes
            { // Plugin used for ECML content to launch, It is default plugin
                "mimeType": ["application/vnd.ekstep.html-archive", "application/vnd.ekstep.h5p-archive"]
                "id": 'org.sunbird.htmlrenderer',
                "ver": 1.0,
                "type": 'plugin'
            }
        ]
    },
    "metadata":{
        "artifactUrl": "https://sunbirdstagingpublic.blob.core.windows.net/sunbird-content-staging/content/do_21339805065209446416747/artifact/zip-95kb_1635504230861_1635504790958.zip",
        "identifier": "do_21339805065209446416747",
        "mimeType": "application/vnd.ekstep.html-archive", // this could be html of h5p
        "streamingUrl": "https://sunbirdstagingpublic.blob.core.windows.net/sunbird-content-staging/content/html/do_21339805065209446416747-latest"
    },
    "data": undefined // content body json object (from API response take -> response.result.content.body)
}
```

Please refer to the [config section of README.md ](https://github.com/project-sunbird/sunbird-collection-editor#how-to-configure)file of the below [git repository](https://github.com/project-sunbird/sunbird-collection-editor)

![](../../../../../.gitbook/assets/htmlcontent.png)

**Interact with player**

Interact with player by using the html interface library.

Add the following to your HTML Content:

The file\_path is the relative path (eg. assets/js) to these files within the html content.

```
<!-- HTML Interface  JS library -->
<script src="[relative_path]/htmlinterface.js"></script>

//you can log telemetry interact event as shown below
org.ekstep.contentrenderer.interface.telemetryService.interact(data) 
//or 
RI.telemetryService.interact(data)
```

Please refer this [developer documents](http://docs.sunbird.org/latest/developer-docs/telemetry/htmlinterfacelibrary/) for more information.
