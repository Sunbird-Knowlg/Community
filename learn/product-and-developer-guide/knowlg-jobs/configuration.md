---
description: >-
  This page lists the knowlg jobs' specific kafka topic, functionality
  configurations, sample event and dependencies (if any).
---

# Configuration

Configuration of all knowledge-platform-jobs during the time of deployment is referred from [sunbird-learning-platform](https://github.com/project-sunbird/sunbird-learning-platform/blob/release-4.8.0/kubernetes/helm\_charts/datapipeline\_jobs/values.j2) repository. However, configuration for local setup is referred from respective job folders in [knowledge-platform-jobs](https://github.com/project-sunbird/knowledge-platform-jobs) repository.

### :stars: asset-enrichment: <a href="#asset-enrichment" id="asset-enrichment"></a>

**Kafka Topic:**

```
kafka {
      input.topic = {{ env_name }}.learning.job.request
      groupId = {{ env_name }}-asset-enrichment-group
    }
```

**Job configuration variables:**

| Variable                        | Purpose                                                                                                                                                                                                                       |
| ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| content.stream.enabled          | <p>Used to enable or disable video stream generation for the uploaded video asset.</p><p><em>Default value:</em> false</p>                                                                                                    |
| content.strem.mimeType          | <p>Used to identify streamable mimeTypes.</p><p><em>Default value:</em> ["video/mp4"]</p>                                                                                                                                     |
| content.youtube.applicationName | <p>Used as credential for youtube client creation in YouTubeUtil.scala file. <br><em>Default value:</em> "fetch-youtube-license"</p>                                                                                          |
| content.youtube.regexPattern    | <p>Used to extract youtube media Id by identifying youtube url pattern using regex.</p><p><em>Default value:</em> ["\?vi?=([^&#x26;]<em>)", "watch\?.v=([^&#x26;])", "(?:embed|vi?)/([^/?]</em>)", "^([A-Za-z0-9\-\_]*)"]</p> |
| content.upload.context.driven   | _Default value:_ true                                                                                                                                                                                                         |
| content.max.iteration.count     | <p>Used to indicate number of times the event is to be attempted for publishing till it is processed successfully. </p><p><em>Default value:</em> 2</p>                                                                       |
| thumbnail.max.sample            | _Default value:_ 5                                                                                                                                                                                                            |
| thumbnail.max.size.pixel        | D_efault value:_ 150                                                                                                                                                                                                          |
|                                 |                                                                                                                                                                                                                               |

**Sample kafka event:**

```
{
  "eid": "BE_JOB_REQUEST",
  "ets": 1648720639981,
  "mid": "LP.1648720639981.d6b1d8c8-7a4a-483a-b83a-b752bede648c",
  "actor": {
    "id": "Asset Enrichment Samza Job",
    "type": "System"
  },
  "context": {
    "pdata": {
      "ver": "1.0",
      "id": "org.sunbird.platform"
    },
    "channel": "01269878797503692810",
    "env": "staging"
  },
  "object": {
    "ver": "1648720639904",
    "id": "do_2135063194770636801334"
  },
  "edata": {
    "action": "assetenrichment",
    "iteration": 1,
    "mediaType": "image",
    "status": "Processing",
    "objectType": "Asset"
  }
}
```

{% hint style="info" %}
_<mark style="color:blue;">**Dependency:**</mark>_** Jobs:** 'video-stream-generator' .\
**External Software:** imagemagick
{% endhint %}



### ****:stars: **audit-event-generator:**

**Kafka Topic:**

```
kafka {
      input.topic = "{{ env_name }}.learning.graph.events"
      groupId = "{{ env_name }}-audit-event-generator-group"
      output.topic = "{{ env_name }}.telemetry.raw"
    }
```

**Job configuration variables:**

| Variable          | Purpose                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| schema.basepath\* | Used to access object schema files basepath that are hosted publicly using which object schema file path can be constructed. (Basepath Example: [https://sunbirddev.blob.core.windows.net/sunbird-dial-dev/schemas/local](https://sunbirddev.blob.core.windows.net/sunbird-dial-dev/schemas/local), Object schema file path example: [https://sunbirddev.blob.core.windows.net/sunbird-dial-dev/schemas/local/content/schema.json](https://sunbirddev.blob.core.windows.net/sunbird-dial-dev/schemas/local/content/schema.json)) |
| channel.default\* | Used to generate context information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

**Sample kafka event:**

```
{
  "ets": 1649228985316,
  "channel": "01269878797503692810",
  "transactionData": {
    "properties": {
      "childNodes": {
        "ov": [
          "do_213509990427254784111670",
          "do_21351048342788505611737",
          "do_21351048359284736011739"
        ],
        "nv": [
          "do_213509990427254784111670",
          "do_21351048342788505611737",
          "do_21351048359284736011739",
          "do_2134250082225192961958"
        ]
      },
      "lastUpdatedOn": {
        "ov": "2022-04-06T07:09:14.653+0000",
        "nv": "2022-04-06T07:09:45.288+0000"
      },
      "versionKey": {
        "ov": "1649228954653",
        "nv": "1649228985288"
      }
    }
  },
  "mid": "1f33cab7-a8ba-4245-87cb-a11ab648d9c8",
  "label": "Timer Course",
  "nodeType": "DATA_NODE",
  "userId": "ANONYMOUS",
  "createdOn": "2022-04-06T07:09:45.316+0000",
  "objectType": "Collection",
  "nodeUniqueId": "do_21351048259398041611736",
  "requestId": null,
  "operationType": "UPDATE",
  "nodeGraphId": 1149046,
  "graphId": "domain"
}
```

****

### :stars: audit-history-indexer:

**Kafka Topic:**

```
kafka {
      input.topic = "{{ env_name }}.learning.graph.events"
      groupId = "{{ env_name }}-audit-history-indexer-group"
    }
```

**Job configuration variables:**

| Variable | Purpose                                                                                                                 |
| -------- | ----------------------------------------------------------------------------------------------------------------------- |
| timezone | <p>Used to generate index name for the autit event to be indexed in ElasticSearch.<br><em>Default value:</em> "IST"</p> |
|          |                                                                                                                         |

**Sample kafka event:**

```
{
  "ets": 1649232292680,
  "channel": "01269878797503692810",
  "transactionData": {
    "properties": {
      "ownershipType": {
        "ov": null,
        "nv": [
          "createdBy"
        ]
      },
      "code": {
        "ov": null,
        "nv": "org.sunbird.cYmND2"
      },
      "credentials": {
        "ov": null,
        "nv": "{\"enabled\":\"Yes\"}"
      },
      "channel": {
        "ov": null,
        "nv": "01269878797503692810"
      },
      "description": {
        "ov": null,
        "nv": "Enter description for Course"
      },
      "organisation": {
        "ov": null,
        "nv": [
          "Tamil Nadu"
        ]
      },
      "language": {
        "ov": null,
        "nv": [
          "English"
        ]
      },
      "mimeType": {
        "ov": null,
        "nv": "application/vnd.ekstep.content-collection"
      },
      "idealScreenSize": {
        "ov": null,
        "nv": "normal"
      },
      "createdOn": {
        "ov": null,
        "nv": "2022-04-06T08:04:52.679+0000"
      },
      "primaryCategory": {
        "ov": null,
        "nv": "Course"
      },
      "contentDisposition": {
        "ov": null,
        "nv": "inline"
      },
      "lastUpdatedOn": {
        "ov": null,
        "nv": "2022-04-06T08:04:52.679+0000"
      },
      "contentEncoding": {
        "ov": null,
        "nv": "gzip"
      },
      "generateDIALCodes": {
        "ov": null,
        "nv": "No"
      },
      "dialcodeRequired": {
        "ov": null,
        "nv": "No"
      },
      "contentType": {
        "ov": null,
        "nv": "Course"
      },
      "trackable": {
        "ov": null,
        "nv": "{\"enabled\":\"Yes\",\"autoBatch\":\"No\"}"
      },
      "creator": {
        "ov": null,
        "nv": "Guest name changed"
      },
      "lastStatusChangedOn": {
        "ov": null,
        "nv": "2022-04-06T08:04:52.679+0000"
      },
      "audience": {
        "ov": null,
        "nv": [
          "Student"
        ]
      },
      "createdFor": {
        "ov": null,
        "nv": [
          "01269878797503692810"
        ]
      },
      "IL_SYS_NODE_TYPE": {
        "ov": null,
        "nv": "DATA_NODE"
      },
      "visibility": {
        "ov": null,
        "nv": "Default"
      },
      "os": {
        "ov": null,
        "nv": [
          "All"
        ]
      },
      "consumerId": {
        "ov": null,
        "nv": "cb069f8d-e4e1-46c5-831f-d4a83b323ada"
      },
      "targetFWIds": {
        "ov": null,
        "nv": [
          "tn_k-12_5"
        ]
      },
      "discussionForum": {
        "ov": null,
        "nv": "{\"enabled\":\"Yes\"}"
      },
      "mediaType": {
        "ov": null,
        "nv": "content"
      },
      "osId": {
        "ov": null,
        "nv": "org.ekstep.quiz.app"
      },
      "version": {
        "ov": null,
        "nv": 2
      },
      "versionKey": {
        "ov": null,
        "nv": "1649232292679"
      },
      "idealScreenDensity": {
        "ov": null,
        "nv": "hdpi"
      },
      "license": {
        "ov": null,
        "nv": "CC BY 4.0"
      },
      "createdBy": {
        "ov": null,
        "nv": "fca2925f-1eee-4654-9177-fece3fd6afc9"
      },
      "compatibilityLevel": {
        "ov": null,
        "nv": 1
      },
      "IL_FUNC_OBJECT_TYPE": {
        "ov": null,
        "nv": "Collection"
      },
      "userConsent": {
        "ov": null,
        "nv": "Yes"
      },
      "name": {
        "ov": null,
        "nv": "Untitled Course"
      },
      "IL_UNIQUE_ID": {
        "ov": null,
        "nv": "do_21351051094159360011743"
      },
      "status": {
        "ov": null,
        "nv": "Draft"
      },
      "resourceType": {
        "ov": null,
        "nv": "Course"
      }
    }
  },
  "mid": "eafe3ff1-c1bc-4a5c-85e6-c5b4c493cc69",
  "label": "Untitled Course",
  "nodeType": "DATA_NODE",
  "userId": "fca2925f-1eee-4654-9177-fece3fd6afc9",
  "createdOn": "2022-04-06T08:04:52.680+0000",
  "objectType": "Collection",
  "nodeUniqueId": "do_21351051094159360011743",
  "requestId": null,
  "operationType": "CREATE",
  "nodeGraphId": 1149047,
  "graphId": "domain"
}
```

****

### :stars: content-publish:&#x20;

**Kafka Topic:**

```
kafka {
      input.topic = {{ env_name }}.publish.job.request
      groupId = {{ env_name }}-content-publish-group
    }
```

**Job configuration variables:**

| Variable                              | Purpose                                                                                                                                                                                                                                                 |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| content.bundleLocation                | <p>Used to specify local/server folder location where artifacts are to be downloaded for ECAR bundling.<br><em>Default value:</em> "/data/contentBundle/"</p>                                                                                           |
| content.isECARExtractionEnabled       | <p>Used to specify if the ECAR extraction is to be enabled to object 'version' and 'latest' cloud location using its 'snapshot' version.<br><em>Default value:</em> true</p>                                                                            |
| content.retry\_asset\_download\_count | <p>Used to specify number of times download attempt for assets part of content/collection object is to be done till it is successfully downloaded.<br><em>Default value:</em> 1</p>                                                                     |
| content.tmp\_file\_location           | NOT USED                                                                                                                                                                                                                                                |
| content.objectType                    | <p>Used to specify list of valid objectTypes supported for publishing.<br><em>Default value:</em> ["Content", "ContentImage"]</p>                                                                                                                       |
| content.mimeType                      | <p>Used to specify list of valid mimeTypes supported for publishing.<br><em>Default value:</em> ["application/pdf"]</p>                                                                                                                                 |
| content.asset\_download\_duration     | <p>Used to specify time in seconds to wait for the asset download request to respond.<br><em>Default value:</em> "60 seconds"</p>                                                                                                                       |
| content.stream.enabled                | <p>Used to check if streaming is enabled for published objects. If it is enabled, content rendenring is done using 'streamingUrl' attribute else via 'artifactUrl'<br><em>Default value:</em> false</p>                                                 |
| content.stream.mimeType               | <p>Used to check if the mimeType of the object being published is of streamable type. If yes,  event for video-stream-generator job is generated.<br><em>Default value:</em> ["video/mp4"]</p>                                                          |
| content.artifact.size.for\_online     | <p>Used to set the maximum size of the object (in bytes) that can be played by downloading beyond which "contentDisposition" is set to "online-only". <br><em>Default value:</em> 209715200</p>                                                         |
| content.downloadFiles.spine           | <p>Used to specify list of attributes that store asset Urls which are to be downloaded from the mentioned Urls while packaging SPINE ECAR.  <br><em>Default value:</em> ["appIcon"]</p>                                                                 |
| content.downloadFiles.full            | <p>Used to specify list of attributes that store asset Urls which are to be downloaded from the mentioned Urls while packaging FULL ECAR.  <br><em>Default value:</em> ["appIcon", "grayScaleAppIcon", "artifactUrl", "itemSetPreviewUrl", "media"]</p> |
| content.nested.fields                 | <p>Used to specify the list of object properties that are of object types with nested attributes.<br><em>Default value:</em> ["badgeAssertions","targets","badgeAssociations"]</p>                                                                      |
| cloud\_storage.folder.content         | <p>Used to specify the cloud store container folder name for content file storage/extraction etc.<br><em>Default value:</em> "container"</p>                                                                                                            |
| cloud\_storage.folder.artifact        | <p>Used to specify the cloud store container folder name for artifact (media) files storage.<br><em>Default value:</em> "artifact"</p>                                                                                                                  |
| contentTypeToPrimaryCategory          | <p>Used to specify the mapping between contentType and primaryCategory attributes using which object metadata is populated with the missing attribute among two.<br><em>Default value:</em> []</p>                                                      |
| compositesearch.index.name            | <p>Used to specify the composite search index name where collection object nodes are synced with updated metadata.<br><em>Default value:</em> "compositesearch"</p>                                                                                     |
| search.document.type                  | <p>Used to specify the ElasticSearch document index type using which collection object nodes are synced with updated metadata.<br><em>Default value:</em> "cs"</p>                                                                                      |
| master.category.validation.enabled    | <p>Used to specify whether object getting published is to be enriched with framework metadata.<br><em>Default value:</em> "Yes"</p>                                                                                                                     |
| service.print.basePath                | NOT USED                                                                                                                                                                                                                                                |
| mimetype.allowed\_extensions.word     | <p>Used to specify the list of file extensions allowed for uploaded content object. <br><em>Default value:</em> ["doc", "docx", "ppt", "pptx", "key", "odp", "pps", "odt", "wpd", "wps", "wks"]</p>                                                     |
| enableDIALContextUpdate               | Used to sepcify if the DIAL code context update data is to be computed using the linked/de-linked Dial codes of the content/collection.                                                                                                                 |

**Sample kafka event:**

```
{
  "eid": "BE_JOB_REQUEST",
  "ets": 1619527882745,
  "mid": "LP.1619527882745.32dc378a-430f-49f6-83b5-bd73b767ad36",
  "actor": {
    "id": "content-publish",
    "type": "System"
  },
  "context": {
    "channel": "01309282781705830427",
    "pdata": {
      "id": "org.sunbird.platform",
      "ver": "1.0"
    },
    "env": "dev"
  },
  "object": {
    "id": "do_11329603741667328018",
    "ver": "1619153418829"
  },
  "edata": {
    "publish_type": "public",
    "metadata": {
      "identifier": "do_11329603741667328018",
      "mimeType": "application/pdf",
      "objectType": "Content",
      "lastPublishedBy": "",
      "pkgVersion": 1
    },
    "action": "publish",
    "iteration": 1
  }
}
```

{% hint style="info" %}
_<mark style="color:blue;">**Dependency:**</mark>_** **&#x20;

**Services:** Content Service - composite search API

**Jobs:** 'post-publish-processor', 'video-stream-generator' & 'mvc-indexer'&#x20;
{% endhint %}

****

### :stars: post-publish-processor:&#x20;

**Kafka Topic:**

```
kafka {
      input.topic = {{ env_name }}.content.postpublish.request
      groupId = {{ env_name }}-post-publish-processor-group
      
      publish.topic = {{ env_name }}.publish.job.request
      qrimage.topic = {{ env_name }}.qrimage.request
      dialcode.context.topic = {{ env_name }}.dialcode.context.job.request
    }
```

**Job configuration variables:**

No job functionality specific variables to list.

**Sample kafka event:**

```
{
  "eid": "BE_JOB_REQUEST",
  "ets": 1649170015935,
  "mid": "LP.1649170015935.2a7382ff-8bc9-4ff5-8620-2d467cf8990a",
  "actor": {
    "id": "Post Publish Processor",
    "type": "System"
  },
  "context": {
    "pdata": {
      "ver": "1.0",
      "id": "org.sunbird.platform"
    },
    "channel": "01272777697873100812",
    "env": "sunbirdstaging"
  },
  "object": {
    "ver": "1649169952265",
    "id": "do_21350999965318348811690"
  },
  "edata": {
    "action": "post-publish-process",
    "iteration": 1,
    "identifier": "do_21350999965318348811690",
    "channel": "01272777697873100812",
    "mimeType": "application/vnd.ekstep.content-collection",
    "contentType": "Course",
    "pkgVersion": 1,
    "status": "Live",
    "name": "CourseMTimmothy",
    "trackable": {
      "enabled": "Yes",
      "autoBatch": "No"
    }
  }
}
```

{% hint style="info" %}
_<mark style="color:blue;">**Dependency:**</mark>_** ** \
****1. **Kafka** **Jobs:** 'qrcode-image-generator', **Samza Jobs:** 'publish-pipeline' (For Shallow Copy Collections publishing)

2\. **Services:** Asset Search Service **(**[Search API](https://documenter.getpostman.com/view/25463377/2s8ZDa3MP7)), LMS Service ([Course Batch Create](https://lern.sunbird.org/learn/product-and-developer-guide/batch-service/api-documentation#api-documentation)), Learning Service to reserve DIAL codes for a collection.
{% endhint %}

****

### :stars: qrcode-image-generator:&#x20;

**Kafka Topic:**

```
kafka {
      input.topic = "{{ env_name }}.qrimage.request"
      groupId = "{{ env_name }}-qrcode-image-generator-group"
    }
```

**Job configuration variables:**

| Variable              | Purpose                                                                                                                   |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| lp.tmp.file.location  | <p>Used to specify machine directory where the qrcode images are to be packaged at.<br><em>Default value:</em> "/tmp"</p> |
| qr.image.imageFormat  | <p>Used to specify qrcode image file format (Example: png)<br><em>Default value:</em> "png"</p>                           |
| qr.image.bottomMargin | <p>Used to specify qrcode image bottom margin.<br><em>Default value:</em> 0</p>                                           |
| qr.image.margin       | <p>Used to specify qrcode image margin.<br><em>Default value:</em> 1</p>                                                  |
|                       |                                                                                                                           |

**Sample event:**

```
{
  "eid": "BE_QR_IMAGE_GENERATOR",
  "processId": "3b369c35-2b79-40ec-a3e0-3d0306fc0388",
  "objectId":"contentid/channel",
  "dialcodes": [
    {
      "data": "https://diksha.gov.in/dial/ABCDEF",
      "text": "ABCDEF",
      "id": "ABCDEF_1543568148",
      "location":"cloudPublicUrl"
    },
    {
      "data": "https://diksha.gov.in/dial/123456",
      "text": "123456",
      "id": "123456_1543568148"
    }
  ],
  "storage": {
    "container": "dial",
    "path": "channel/publisher/",
    "fileName": "do_112636984058314752121_Medium_Grade_Subject_timestamp"
  },
  "config": {
    "errorCorrectionLevel": "H",
    "pixelsPerBlock": 2,
    "qrCodeMargin": 3,
    "qrCodeMarginBottom": 1,
    "textFontName": "Verdana",
    "textFontSize": 11,
    "textCharacterSpacing": 0.1,
    "imageFormat": "png",
    "colourModel": "Grayscale",
    "imageBorderSize": 1,
    "imageMargin": 1
  }
}
```

_<mark style="color:blue;">****</mark>_

### :stars: search-indexer:&#x20;

**Kafka Topic:**

```
kafka {
      input.topic = "{{ env_name }}.learning.graph.events"
      groupId = "{{ env_name }}-search-indexer-group"
    }
```

**Job configuration variables:**

| Variable                        | Purpose                                                                                                                                                                                 |
| ------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| compositesearch.index.name      | <p>Used to specify index name of composite search in ElasticSearch.<br><em>Default value:</em> "compositesearch"</p>                                                                    |
| dialcode.index.name             | <p>Used to specify index name of DIAL code in ElasticSearch.<br><em>Default value:</em> "dialcode"</p>                                                                                  |
| dailcodemetrics.index.name      | <p>Used to specify index name of DIAL code metrics in ElasticSearch.<br><em>Default value:</em> "dialcodemetrics"</p>                                                                   |
| restrict.metadata.objectTypes   | NOT USED                                                                                                                                                                                |
| nested.fields                   | <p>Used to specify the list of object properties that are of object types with nested attributes which are necessary for indexing in ElasticSearch.<br><em>Default value:</em> [""]</p> |
| schema.definition\_cache.expiry | NOT USED                                                                                                                                                                                |
| restrict.objectTypes            | <p>Used to specify list of object Types for which transaction event output tags are to be restricted/skipped.<br><em>Default value:</em> [""]</p>                                       |
| ignored.fields                  | <p><em>Used to specify the list of object properties that are to be ingored while indexing an object document.</em><br><em>Default value:</em> ["responseDeclaration", "body"]</p>      |
|                                 |                                                                                                                                                                                         |

**Sample kafka** **event:**

```
{
  "ets": 1649229042072,
  "channel": "01269878797503692810",
  "transactionData": {
    "properties": {
      "childNodes": {
        "ov": [
          "do_213509990427254784111670",
          "do_21351048342788505611737",
          "do_2134250082225192961958",
          "do_21351048359284736011739",
          "do_21351048393799270411741",
          "do_21310354431597772814733"
        ],
        "nv": [
          "do_213509990427254784111670",
          "do_21351048342788505611737",
          "do_2134250082225192961958",
          "do_21351048359284736011739",
          "do_21310354431597772814733",
          "do_21351048393799270411741"
        ]
      },
      "lastUpdatedOn": {
        "ov": "2022-04-06T07:10:27.365+0000",
        "nv": "2022-04-06T07:10:42.041+0000"
      },
      "versionKey": {
        "ov": "1649229027365",
        "nv": "1649229042041"
      }
    }
  },
  "mid": "cb29eb1d-810f-4f26-a174-e37f9a681066",
  "label": "Timer Course",
  "nodeType": "DATA_NODE",
  "userId": "ANONYMOUS",
  "createdOn": "2022-04-06T07:10:42.072+0000",
  "objectType": "Collection",
  "nodeUniqueId": "do_21351048259398041611736",
  "requestId": null,
  "operationType": "UPDATE",
  "nodeGraphId": 1149046,
  "graphId": "domain"
}
```

###

### :stars: video-stream-generator:&#x20;

**Kafka Topic:**

```
kafka {
      input.topic = "{{ env_name }}.content.postpublish.request"
      groupId = "{{ env_name }}-video-stream-generator-group"
    }
```

**Job configuration variables:**

| Variable                 | Purpose                                                                                                                              |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| service.content.basePath | Used to configure Content Service API base path for accessing System Update API (/content/v4/system/update/ - not exposed publicly). |
|                          |                                                                                                                                      |

**Sample kafka event:**

```
{
  "eid": "BE_JOB_REQUEST",
  "ets": 1649174914686,
  "mid": "LP.1649174914686.02c7ac3d-f7b2-46be-9771-e91645ecd632",
  "actor": {
    "id": "Post Publish Processor",
    "type": "System"
  },
  "context": {
    "pdata": {
      "ver": "1.0",
      "id": "org.sunbird.platform"
    },
    "channel": "01272777697873100812",
    "env": "sunbirdstaging"
  },
  "object": {
    "ver": "1649169311270",
    "id": "do_21350999440018636811684"
  },
  "edata": {
    "action": "post-publish-process",
    "iteration": 1,
    "identifier": "do_21350999440018636811684",
    "channel": "01272777697873100812",
    "mimeType": "application/vnd.ekstep.content-collection",
    "contentType": "Course",
    "pkgVersion": 1,
    "status": "Live",
    "name": "CourseMElenor",
    "trackable": {
      "enabled": "Yes",
      "autoBatch": "No"
    }
  }
}
```

{% hint style="info" %}
_<mark style="color:blue;">**Dependency:**</mark>_** Services:** Content Service - system update API
{% endhint %}

****

### :stars: dialcode-context-updater:&#x20;

**Kafka Topic:**

```
kafka {
      input.topic = "{{ env_name }}.dialcode.context.job.request"
      groupId = "{{ env_name }}-dialcode-group"
    }
```

**Job configuration variables:**

| Variable                                                            | Purpose                                                                                                                                                     |
| ------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| dialcode\_context\_updater.actions                                  | Used to identify dial code context update action                                                                                                            |
| dialcode\_context\_updater_._search_\__mode                         | Used to set search mode for search API                                                                                                                      |
| dialcode\_context\_updater_._context\_map\_path                     | Used to specify the path of context Mapping file. File used to specify the field mapping of context schema.jsonld to sunbird content/collection schema.json |
| dialcode\_context\_updater_._identifier\_search\_fields             | Used to specify the search fields when the content/collection details is fetched for primary category.                                                      |
| dialcode\_context\_updater_._dial\_code\_context\_read\_api\_path   | Used to specify the api endpoint of the DIAL service read context API (/dialcode/v4/read)                                                                   |
| dialcode\_context\_updater_._dial\_code\_context\_update\_api\_path | Used to specify the api endpoint of the DIAL service Update context API (/dialcode/v4/update)                                                               |
| service.search.basePath                                             | Used to specify Search service base URL.                                                                                                                    |
| service.dial\_service.basePath                                      | Used to specify DIAL service base URL.                                                                                                                      |
| es\_sync\_wait\_time                                                | Used to specify wait time for collection nodes data to sync to ES after collection publish to reflect in search service results.                            |
|                                                                     |                                                                                                                                                             |

**Sample kafka event:**

```
{
  "eid": "BE_JOB_REQUEST",
  "ets": 1655804893687,
  "mid": "LP.1655804893687.e8e921df-f479-49a9-af5a-df8bbc4de70a",
  "actor": {
    "id": "DIAL code context update Job",
    "type": "System"
  },
  "context": {
    "pdata": {
      "ver": "1.0",
      "id": "org.ekstep.platform"
    },
    "channel": "01309282781705830427",
    "env": "dev"
  },
  "object": {
    "ver": "1.0",
    "id": "G3L9S2"
  },
  "edata": {
    "action": "dialcode-context-update",
    "iteration": 1,
    "dialcode": "G3L9S2",
    "identifier": "do_113556563202981888177"
  },
  "identifier": "do_113556563202981888177"
}
```

{% hint style="info" %}
_<mark style="color:blue;">**Dependency:**</mark>_\
_<mark style="color:blue;">****</mark>_** Services:** \
&#x20; ****  1. Search Service - composite search API

&#x20; 2\. DIAL service - DIAL context read and update API
{% endhint %}

****

### :stars: cassandra-data-migration:&#x20;

**Kafka Topic:**

```
kafka {
      input.topic = "{{ env_name }}.cassandra.data.migration.request"
      groupId = "{{ env_name }}-cassandra-data-migration-group"
    }
```

**Job configuration variables:**

| Variable                                 | Purpose                                                                                                                         |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| migrate.keyspace                         | Used to specify the keyspace of the cassandra database in which data is to be migrated.                                         |
| migrate.table                            | Used to specify the table in the keyspace configured above; in which data is to be migrated.                                    |
| migrate.primary\_key\_column             | Used to specify the primay key column name of the table and the keyspace configured above; in which data is to be migrated.     |
| migrate.primary\_key\_column\_type       | Used to specify the primay key column datatype in the table and the keyspace configured above; in which data is to be migrated. |
| migrate.column\_to\_migrate              | Used to specify the name of the column to be migrated from the table and the keyspace configured above.                         |
| migrate.column\_to\_migrate\_type        | Used to specify the datatype of the column to be migrated from the table and the keyspace configured above.                     |
| migrate.key\_value\_strings\_to\_migrate | Used to specify the list of strings to be migrated in the column data.                                                          |



**Sample kafka event:**

```
{
  "eid": "BE_JOB_REQUEST",
  "ets": 1619527882745,
  "mid": "LP.1619527882745.32dc378a-430f-49f6-83b5-bd73b767ad36",
  "actor": {
    "id": "cassandra-data-migration",
    "type": "System"
  },
  "context": {
    "channel": "ORG_001",
    "pdata": {
      "id": "org.sunbird.platform",
      "ver": "1.0"
    },
    "env": "dev"
  },
  "edata": {
    "column": "url",
    "table": "dialcode_images",
    "keyspace": "dialcodes",
    "action": "migrate-cassandra",
    "iteration": 1
  }
}
```



### :stars: csp-migrator:&#x20;

**Kafka Topic:**

```
kafka {
      input.topic = "{{ env_name }}.csp.migration.job.request"
      groupId = "{{ env_name }}-csp-migrator-group"
      failed.topic = "{{ csp_migrator_failed_topic_name }}"
      live_video_stream.topic = "{{ video_stream_topic_name }}"
      live_content_node_republish.topic = "{{ content_republish_topic_name }}"
      live_question_node_republish.topic = "{{ question_republish_topic_name }}"
    }
```

**Job configuration variables:**

| Variable                         | Purpose                                                                           |
| -------------------------------- | --------------------------------------------------------------------------------- |
| key\_value\_strings\_to\_migrate | Used to specify the list of strings to be migrated in the fields' data.           |
| neo4j\_fields\_to\_migrate       | Used to specify the neo4j fields which are to be migrated based on the objectType |
| cassandra\_fields\_to\_migrate   | Used to specify the columns of assessmentItem which are to be migrated.           |
| hierarchy.keyspace               | Used to specify the keyspace containing collection hierarchy data table           |
| hierarchy.table                  | Used to specify collection hierarchy data table                                   |
| content.keyspace                 | Used to specify the keyspace containing content data table                        |
| content.content\_table           | Used to specify content data table                                                |
| content.assessment\_table        | Used to specify assessment data table                                             |
| questionset.hierarchy.keyspace   | Used to specify the keyspace containing question set hierarchy table.             |
| questionset.hierarchy.table      | Used to specify the question set hierarchy table                                  |
| migrationVersion                 | Used to specify the migration version                                             |
|                                  |                                                                                   |
|                                  |                                                                                   |
|                                  |                                                                                   |



**Sample kafka event:**

```
{
  "eid": "BE_JOB_REQUEST",
  "ets": 1619527882745,
  "mid": "LP.1619527882745.32dc378a-430f-49f6-83b5-bd73b767ad36",
  "actor": {
    "id": "csp-migration",
    "type": "System"
  },
  "context": {
    "channel": "01309282781705830427",
    "pdata": {
      "id": "org.sunbird.platform",
      "ver": "1.0"
    },
    "env": "dev"
  },
  "object": {
    "id": "do_2136329211884830721183.img",
    "ver": "1619153418829"
  },
  "edata": {
    "metadata": {
      "mimeType": "application/vnd.ekstep.pdf",
      "objectType": "ContentImage",
      "status": "Live"
    },
    "action": "csp-migration",
    "iteration": 1
  }
}
```

{% hint style="info" %}
_<mark style="color:blue;">**Dependency:**</mark>_**  Sync tool (Jenkins Job - to trigger events for each content to be migrated).**
{% endhint %}



### :stars: live-node-publisher:&#x20;

**Kafka Topic:**

```
kafka {
      input.topic = {{ env_name }}.republish.job.request
      groupId = {{ env_name }}-content-republish-group
      live_video_stream.topic = "{{ env_name }}.live.video.stream.request"
      error.topic = "{{ env_name }}.learning.events.failed"
      skipped.topic = "{{ env_name }}.learning.events.skipped"
    }
```

**Job configuration variables:**

| Variable                              | Purpose                                                                                                                                                                                                                                                 |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| content.bundleLocation                | <p>Used to specify local/server folder location where artifacts are to be downloaded for ECAR bundling.<br><em>Default value:</em> "/data/contentBundle/"</p>                                                                                           |
| content.isECARExtractionEnabled       | <p>Used to specify if the ECAR extraction is to be enabled to object 'version' and 'latest' cloud location using its 'snapshot' version.<br><em>Default value:</em> true</p>                                                                            |
| content.retry\_asset\_download\_count | <p>Used to specify number of times download attempt for assets part of content/collection object is to be done till it is successfully downloaded.<br><em>Default value:</em> 1</p>                                                                     |
| content.tmp\_file\_location           | NOT USED                                                                                                                                                                                                                                                |
| content.objectType                    | <p>Used to specify list of valid objectTypes supported for publishing.<br><em>Default value:</em> ["Content", "ContentImage"]</p>                                                                                                                       |
| content.mimeType                      | <p>Used to specify list of valid mimeTypes supported for publishing.<br><em>Default value:</em> ["application/pdf"]</p>                                                                                                                                 |
| content.asset\_download\_duration     | <p>Used to specify time in seconds to wait for the asset download request to respond.<br><em>Default value:</em> "60 seconds"</p>                                                                                                                       |
| content.stream.enabled                | <p>Used to check if streaming is enabled for published objects. If it is enabled, content rendenring is done using 'streamingUrl' attribute else via 'artifactUrl'<br><em>Default value:</em> false</p>                                                 |
| content.stream.mimeType               | <p>Used to check if the mimeType of the object being published is of streamable type. If yes,  event for video-stream-generator job is generated.<br><em>Default value:</em> ["video/mp4"]</p>                                                          |
| content.artifact.size.for\_online     | <p>Used to set the maximum size of the object (in bytes) that can be played by downloading beyond which "contentDisposition" is set to "online-only". <br><em>Default value:</em> 209715200</p>                                                         |
| content.downloadFiles.spine           | <p>Used to specify list of attributes that store asset Urls which are to be downloaded from the mentioned Urls while packaging SPINE ECAR.  <br><em>Default value:</em> ["appIcon"]</p>                                                                 |
| content.downloadFiles.full            | <p>Used to specify list of attributes that store asset Urls which are to be downloaded from the mentioned Urls while packaging FULL ECAR.  <br><em>Default value:</em> ["appIcon", "grayScaleAppIcon", "artifactUrl", "itemSetPreviewUrl", "media"]</p> |
| content.nested.fields                 | <p>Used to specify the list of object properties that are of object types with nested attributes.<br><em>Default value:</em> ["badgeAssertions","targets","badgeAssociations"]</p>                                                                      |
| cloud\_storage.folder.content         | <p>Used to specify the cloud store container folder name for content file storage/extraction etc.<br><em>Default value:</em> "container"</p>                                                                                                            |
| cloud\_storage.folder.artifact        | <p>Used to specify the cloud store container folder name for artifact (media) files storage.<br><em>Default value:</em> "artifact"</p>                                                                                                                  |
| contentTypeToPrimaryCategory          | <p>Used to specify the mapping between contentType and primaryCategory attributes using which object metadata is populated with the missing attribute among two.<br><em>Default value:</em> []</p>                                                      |
| compositesearch.index.name            | <p>Used to specify the composite search index name where collection object nodes are synced with updated metadata.<br><em>Default value:</em> "compositesearch"</p>                                                                                     |
| search.document.type                  | <p>Used to specify the ElasticSearch document index type using which collection object nodes are synced with updated metadata.<br><em>Default value:</em> "cs"</p>                                                                                      |
| master.category.validation.enabled    | <p>Used to specify whether object getting published is to be enriched with framework metadata.<br><em>Default value:</em> "Yes"</p>                                                                                                                     |
| service.print.basePath                | NOT USED                                                                                                                                                                                                                                                |
| mimetype.allowed\_extensions.word     | <p>Used to specify the list of file extensions allowed for uploaded content object. <br><em>Default value:</em> ["doc", "docx", "ppt", "pptx", "key", "odp", "pps", "odt", "wpd", "wps", "wks"]</p>                                                     |

**Sample kafka event:**

```
{
  "eid": "BE_JOB_REQUEST",
  "ets": 1619527882745,
  "mid": "LP.1619527882745.32dc378a-430f-49f6-83b5-bd73b767ad36",
  "actor": {
    "id": "content-publish",
    "type": "System"
  },
  "context": {
    "channel": "ORG_001",
    "pdata": {
      "id": "org.sunbird.platform",
      "ver": "1.0"
    },
    "env": "dev"
  },
  "object": {
    "id": "do_11363368845198131217",
    "ver": "1619153418829"
  },
  "edata": {
    "publish_type": "public",
    "metadata": {
      "identifier": "do_11363368845198131217",
      "mimeType": "application/vnd.ekstep.ecml-archive",
      "objectType": "Content",
      "lastPublishedBy": "",
      "pkgVersion": 4
    },
    "action": "republish",
    "iteration": 1
  }
}
```

{% hint style="info" %}
_<mark style="color:blue;">**Dependency:**</mark>_** **&#x20;

**Services:** Search Service - composite search API

**Jobs:** 'csp-migrator'
{% endhint %}



### :stars: live-video-stream-generator:&#x20;

**Kafka Topic:**

```
kafka {
      input.topic = "{{ env_name }}.live.video.stream.request"
      groupId = "{{ env_name }}-live-video-stream-generator-group"
    }
```

**Job configuration variables:**

| Variable                 | Purpose                                                                                                                              |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| service.content.basePath | Used to configure Content Service API base path for accessing System Update API (/content/v4/system/update/ - not exposed publicly). |
|                          |                                                                                                                                      |

**Sample kafka event:**

```
{
  "eid": "BE_JOB_REQUEST",
  "ets": 1649174914686,
  "mid": "LP.1649174914686.02c7ac3d-f7b2-46be-9771-e91645ecd632",
  "actor": {
    "id": "Post Publish Processor",
    "type": "System"
  },
  "context": {
    "pdata": {
      "ver": "1.0",
      "id": "org.sunbird.platform"
    },
    "channel": "01272777697873100812",
    "env": "sunbirdstaging"
  },
  "object": {
    "ver": "1649169311270",
    "id": "do_21350999440018636811684"
  },
  "edata": {
    "action": "post-publish-process",
    "iteration": 1,
    "identifier": "do_21350999440018636811684",
    "channel": "01272777697873100812",
    "mimeType": "application/vnd.ekstep.content-collection",
    "contentType": "Course",
    "pkgVersion": 1,
    "status": "Live",
    "name": "CourseMElenor",
    "trackable": {
      "enabled": "Yes",
      "autoBatch": "No"
    }
  }
}
```

{% hint style="info" %}
_<mark style="color:blue;">**Dependency:**</mark>_** **&#x20;

**Services:** Content Service - system update API

**Jobs:** 'live-node-publisher'
{% endhint %}

###

