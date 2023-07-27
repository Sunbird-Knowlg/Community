---
description: >-
  This page lists the knowlg jobs' specific kafka topic, functionality
  configurations, sample event and dependencies (if any).
---

# Configuration

Configuration of all knowledge-platform-jobs during the time of deployment is referred from [sunbird-learning-platform](https://github.com/project-sunbird/sunbird-learning-platform/blob/release-4.8.0/kubernetes/helm\_charts/datapipeline\_jobs/values.j2) repository. However, configuration for local setup is referred from respective job folders in [knowledge-platform-jobs](https://github.com/project-sunbird/knowledge-platform-jobs) repository.

### :stars: dialcode-context-updater:&#x20;

**Kafka Topic:**

```
kafka {
      input.topic = "{{ env_name }}.dialcode.context.job.request"
      groupId = "{{ env_name }}-dialcode-group"
    }
```

**Job configuration variables:**

<table><thead><tr><th width="360">Variable</th><th>Purpose</th></tr></thead><tbody><tr><td>dialcode_context_updater.actions</td><td>Used to identify dial code context update action</td></tr><tr><td>dialcode_context_updater<em>.</em>search<em>_</em>mode</td><td>Used to set search mode for search API</td></tr><tr><td>dialcode_context_updater<em>.</em>context_map_path</td><td>Used to specify the path of context Mapping file. File used to specify the field mapping of context schema.jsonld to sunbird content/collection schema.json</td></tr><tr><td>dialcode_context_updater<em>.</em>identifier_search_fields</td><td>Used to specify the search fields when the content/collection details is fetched for primary category.</td></tr><tr><td>dialcode_context_updater<em>.</em>dial_code_context_read_api_path</td><td>Used to specify the api endpoint of the DIAL service read context API (/dialcode/v4/read)</td></tr><tr><td>dialcode_context_updater<em>.</em>dial_code_context_update_api_path</td><td>Used to specify the api endpoint of the DIAL service Update context API (/dialcode/v4/update)</td></tr><tr><td>service.search.basePath</td><td>Used to specify Search service base URL.</td></tr><tr><td>service.dial_service.basePath</td><td>Used to specify DIAL service base URL.</td></tr><tr><td>es_sync_wait_time</td><td>Used to specify wait time for collection nodes data to sync to ES after collection publish to reflect in search service results.</td></tr><tr><td></td><td></td></tr></tbody></table>

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
** Services:** \
&#x20; 1\. Search Service - composite search API

&#x20; 2\. DIAL service - DIAL context read and update API
{% endhint %}

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
_<mark style="color:blue;">**Dependency:**</mark>_&#x20;

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
_<mark style="color:blue;">**Dependency:**</mark>_&#x20;

**Services:** Content Service - system update API

**Jobs:** 'live-node-publisher'
{% endhint %}

###

