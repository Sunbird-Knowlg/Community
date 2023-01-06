---
description: >-
  This document details about migration of data from cloud absolute paths stored
  in the database with relative paths OR with new CSP absolute paths.
---

# Data Migration

This document details about the migration of data with respect to

* Replace existing absolute paths in database with relative paths.
*   Migration of data while changing the CSP provider

    Example: Moving from Azure to AWS service provider.

#### Below are the data that currently(upto release-5.2.0) store cloud specific absolute URLs that are to be migrated to relative paths OR with new CSP provider absolute URLs:

* neo4J fields based on objectType:

```
"asset": ["artifactUrl", "thumbnail", "downloadUrl"],
"content": ["appIcon", "artifactUrl", "posterImage", "previewUrl", "thumbnail", "assetsMap", "certTemplate", "itemSetPreviewUrl", "grayScaleAppIcon", "sourceURL", "variants", "downloadUrl","streamingUrl"],
"contentimage": ["appIcon", "artifactUrl", "posterImage", "previewUrl", "thumbnail", "assetsMap", "certTemplate", "itemSetPreviewUrl", "grayScaleAppIcon", "sourceURL", "variants", "downloadUrl","streamingUrl"],
"collection": ["appIcon", "artifactUrl", "posterImage", "previewUrl", "thumbnail", "toc_url", "grayScaleAppIcon", "variants", "downloadUrl"],
"collectionimage": ["appIcon", "artifactUrl", "posterImage", "previewUrl", "thumbnail", "toc_url", "grayScaleAppIcon", "variants", "downloadUrl"],
"plugins": ["artifactUrl"],
"itemset": ["previewUrl", "downloadUrl"],
"assessmentitem": ["data", "question", "solutions", "editorState", "media"],
"question": ["appIcon","artifactUrl", "posterImage", "previewUrl","downloadUrl", "variants","pdfUrl"],
"questionimage": ["appIcon","artifactUrl", "posterImage", "previewUrl","downloadUrl", "variants","pdfUrl"],
"questionset": ["appIcon","artifactUrl", "posterImage", "previewUrl","downloadUrl", "variants","pdfUrl"],
"questionsetimage": ["appIcon","artifactUrl", "posterImage", "previewUrl","downloadUrl", "variants","pdfUrl"]
```

{% hint style="info" %}
Note: Above data is available as configuration(neo4j\_fields\_to\_migrate) in 'csp-migrator' job.&#x20;
{% endhint %}

* Cassandra data that will be migrated

| Keyspace              | Table                  | Column                                                     |
| --------------------- | ---------------------- | ---------------------------------------------------------- |
| hierarchy\_keystore   | content\_hierarchy     | hierarchy                                                  |
| content\_keystore     | content\_data          | body                                                       |
| content\_keystore     | question\_data         | body,  editorState, answer, solutions, instructions, media |
| questionset\_keystore | questionset\_hierarchy | hierarchy                                                  |
| dialcodes             | dialcode\_images       | url                                                        |
| dialcodes             | dialcode\_batch        | url                                                        |

* ECAR (needs live nodes republishing)
* streamingUrl (needs regeneration based on new Media service provider)

Reference diagram to know how the migration of existing data with CNAME(storing relative path DB)&#x20;

{% embed url="https://app.diagrams.net/#G1HzUob6a9_TrVWhcoo1nWoKPVN0PKzpmQ" %}
migration flow diagram (migration-job flow & migration-process workflow)
{% endembed %}

#### Flink Jobs used for migration:

* [csp-migrator](https://knowlg.sunbird.org/learn/product-and-developer-guide/knowlg-jobs/configuration#csp-migrator): For migration of data in eno4j and cassandra tables.
* [live-node-publisher](https://knowlg.sunbird.org/learn/product-and-developer-guide/knowlg-jobs/configuration#live-node-publisher): For republishing of live nodes (Content and Collection).
* [live-video-stream-generator](https://knowlg.sunbird.org/learn/product-and-developer-guide/knowlg-jobs/configuration#live-video-stream-generator): For regeneration of streamUrl using new Media service.
* [cassandra-data-migration](https://knowlg.sunbird.org/learn/product-and-developer-guide/knowlg-jobs/configuration#cassandra-data-migration): For migration of data in any cassandra table, column wise.

{% hint style="info" %}
Note:&#x20;

* Jenkins Job '<mark style="color:green;">**Neo4jElasticSearchSyncTool**</mark>' is used to insert the events into 'csp-migrator' job input topic. 'csp-migrator' job will further insert topics into 'live-node-publisher' job and 'live-video-stream-generator' jobs based on conditions. Jenkins job command: **migratecspdata**
* '**cassandra-data-migration'** job is to be used for migration of '_dialcode\_images'_ and '_dialcode\_batch'_ cassandra tables in '_dialcodes_**'** keyspace.
* <mark style="color:orange;">**Run the migration flink jobs in a separate kafka setup with increased processing ability and storage for storing all kakfa events and logs.**</mark>
* <mark style="color:orange;">**Increase the infra for neo4j. Also, increase the neo4j max heap size in neo4j conf file.**</mark>&#x20;
* <mark style="color:orange;">**Increase infra for logstash, search-indexer flink job and ElasticSearch to handle the neo4j transaction data sync.**</mark>
{% endhint %}

The content migration should execute in the below order only. Otherwise there is a chances of migration failure because of dependent content is not yet migrated. [more details](https://docs.google.com/spreadsheets/d/13DaXCx8uToOwinlAPxvTat8NELxiPgG4KXATcKaJm\_c/edit#gid=1675310401\&range=K3)

### Migration Steps

* Before running the migration steps, go [here](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/3257892877/Verification+of+Migration+Steps) and run all the queries and keep the output to compare after migration.
* Go to Deploy/KnowledgePlatform/Neo4jElasticSearchSyncTool jenkins job.
* Select the command as **migratecspdata**
* And copy and paste the parameter one by one in parameter section in jenkins deployment job.

| Sequence | Type                                              | Sync Tool Jenkins Parameters                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| -------- | ------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1        | Video Asset                                       | --graphId domain --objectType Asset --mimeType video/webm,video/mp4 --delay 2000                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| 2        | Other Asset                                       | --graphId domain --objectType Asset --delay 2000                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| 3        | Video Content                                     | --graphId domain --objectType Content,ContentImage --mimeType video/mp4,video/webm --delay 2000                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| 4        | Plugin, Youtube Content, PDF Content,EPUB Content | --graphId domain --objectType Content,ContentImage --mimeType application/vnd.ekstep.plugin-archive,video/x-youtube,application/pdf,application/epub --delay 2000                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| 5        | AssessmentItem                                    | --graphId domain --objectType AssessmentItem --delay 2000                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| 6        | ItemSet                                           | --graphId domain --objectType ItemSet --delay 2000                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| 7        | H5P Content                                       | --graphId domain --objectType Content,ContentImage --mimeType application/vnd.ekstep.h5p-archive --delay 2000                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| 8        | HTML                                              | --graphId domain --objectType Content,ContentImage --mimeType application/vnd.ekstep.html-archive --delay 2000                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| 9        | ECML                                              | --graphId domain --objectType Content,ContentImage --mimeType application/vnd.ekstep.ecml-archive --delay 2000                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| 10       | Collection                                        | --graphId domain --objectType Content,ContentImage,Collection,CollectionImage --mimeType application/vnd.ekstep.content-collection --delay 2000                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| 11       | dialcodes.dialcode\_images                        | <p>Push below event to "{{env}}.cassandra.data.migration.request" kafka topic<br></p><pre><code>{"eid":"BE_JOB_REQUEST","ets":1619527882745,"mid":"LP.1619527882745.32dc378a-430f-49f6-83b5-bd73b767ad36","actor":{"id":"cassandra-data-migration","type":"System"},"context":{"channel":"ORG_001","pdata":{"id":"org.sunbird.platform","ver":"1.0"},"env":"dev"},"edata":{"column":"url", "columnType":"String", "table": "dialcode_images", "keyspace": "dialcodes", "primaryKeyColumn": "filename", "primaryKeyColumnType": "String", "action":"migrate-cassandra","iteration":1}}
</code></pre> |
| 12       | dialcodes.dialcode\_batch                         | <p>Push below event to "{{env}}.cassandra.data.migration.request" kafka topic<br></p><pre><code>{"eid":"BE_JOB_REQUEST","ets":1619527882745,"mid":"LP.1619527882745.32dc378a-430f-49f6-83b5-bd73b767ad36","actor":{"id":"cassandra-data-migration","type":"System"},"context":{"channel":"ORG_001","pdata":{"id":"org.sunbird.platform","ver":"1.0"},"env":"dev"},"edata":{"column":"url", "columnType":"String", "table": "dialcode_batch", "keyspace": "dialcodes", "primaryKeyColumn": "processid", "primaryKeyColumnType": "UUID", "action":"migrate-cassandra","iteration":1}}
</code></pre>   |



{% hint style="info" %}
Note:

* If the 'migratecspdata' command stops before reaching 100%, please wait for 'csp-migrator' job lag to reach 0 before triggerring the same 'migratecspdata' command again.
* ECML migration can be triggered only after Asset, AssessmentItem and ItemSet migration is completed.
* For Collection migration to be triggered, pre-requisites are:

&#x20;       a. Question, QuestionSet migration should be completed (as part of Inquiry BB).

&#x20;       b. All assets and contents are to be migrated successfully.&#x20;

&#x20;       c. All migrated contents data should be synced to ElasticSearch.
{% endhint %}



### Migration status: migrationVersion of the node object

**1.Neo4J & Cassandra data migration started**

* no version => Data migration started for each Neo4j node. It will migrate the Neo4j data and Cassandra data migration failed for the object
* <mark style="color:green;">1.0</mark> => <mark style="color:green;">Success:</mark> Neo4j data and Cassandra data migration completed for the object(node)
* <mark style="color:red;">0.1</mark> => <mark style="color:red;">Fail</mark>: Data migration is failed for the Neo4J data or Cassandra data of the specific node(identifier is the key to know for which node it failed. We can check the logs of the service to know the reason of failure)
* <mark style="color:red;">0.5</mark> => <mark style="color:red;">Skipped</mark>:  migration skipped for the object\


**2.ECAR Generation**(after previous step of Neo4J & Cassandra data migration success)

* <mark style="color:green;">1.1</mark> => <mark style="color:green;">Success:</mark> Neo4j data and Cassandra data migration completed for the object and ECAR is republished.
* <mark style="color:red;">0.2</mark> => <mark style="color:red;">Fail</mark>: Neo4j data and Cassandra data migration completed for the object. But, ECAR republish has failed.

**3.Video streaming generation** (after previous step of ECAR generate is success)

* <mark style="color:green;">1.2</mark> => <mark style="color:green;">Success:</mark> Neo4j data and Cassandra data migration completed for video type of asset/content and streamingUrl is regenerated successfully.

### Verification of migration steps:

More details of verification steps are added in the below confluence wiki

{% embed url="https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/3257892877/Verification+of+Migration+Steps" %}

