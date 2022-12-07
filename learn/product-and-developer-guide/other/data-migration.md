---
description: >-
  This document details about migration of data from cloud absolute paths stored
  in the database with relative paths OR with new CSP abosulte paths.
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

#### Sequence of migration steps:

The content migration should execute in the below order only. Otherwise there is a chances of migration failure because of dependent content is not yet migrated. [more details](https://docs.google.com/spreadsheets/d/13DaXCx8uToOwinlAPxvTat8NELxiPgG4KXATcKaJm\_c/edit#gid=1675310401\&range=K3)

| Sequence | Type            | Sync Tool Jenkins Parameters                                                                                              |
| -------- | --------------- | ------------------------------------------------------------------------------------------------------------------------- |
| 1        | Video Asset     | --graphId domain --objectType Asset --mimeType video/webm,video/mp4 --limit 1000                                          |
| 2        | Other Asset     | --graphId domain --objectType Asset --limit 1000                                                                          |
| 3        | Video Content   | --graphId domain --objectType Content,ContentImage --mimeType video/mp4,video/webm -limit 1000                            |
| 4        | Plugin          | --graphId domain --objectType Content --mimeType application/vnd.ekstep.plugin-archive --limit 1000                       |
| 5        | AssessmentItem  | --graphId domain --objectType AssessmentItem --limit 1000                                                                 |
| 6        | ItemSet         | --graphId domain --objectType ItemSet --limit 1000                                                                        |
| 7        | Youtube Content | --graphId domain --objectType Content,ContentImage --mimeType video/x-youtube -limit 1000                                 |
| 8        | PDF Content     | --graphId domain --objectType Content,ContentImage --mimeType application/pdf -limit 1000                                 |
| 9        | EPUB Content    | --graphId domain --objectType Content,ContentImage --mimeType application/epub -limit 1000                                |
| 10       | H5P Content     | --graphId domain --objectType Content,ContentImage --mimeType application/vnd.ekstep.h5p-archive -limit 1000              |
| 11       | HTML            | --graphId domain --objectType Content,ContentImage --mimeType application/vnd.ekstep.html-archive -limit 1000             |
| 12       | Question        | --graphId domain --objectType Question  -limit 1000                                                                       |
| 13       | QuestionSet     | --graphId domain --objectType QuestionSet,QuestionSetImage  -limit 1000                                                   |
| 14       | ECML            | --graphId domain --objectType Content,ContentImage --mimeType application/vnd.ekstep.ecml-archive -limit 1000             |
| 15       | Collection      | --graphId domain --objectType Collection,CollectionImage --mimeType application/vnd.ekstep.content-collection -limit 1000 |

#### Migration Version status Information:

* 1.0 => neo4j data and cassandra data migration completed for the object
* 0.1 => neo4j data migration or cassandra data migration failed for the object
* 0.5 => migration skipped for the object
* 1.1 => neo4j data and cassandra data migration completed for the object and ECAR is republished.
* 0.2 => neo4j data and cassandra data migration completed for the object. But, ECAR republish has failed.
* 1.2 => neo4j data and cassandra data migration completed for video type of asset/content and streamingUrl is regenerated successfully.

#### Verification of migration steps:

