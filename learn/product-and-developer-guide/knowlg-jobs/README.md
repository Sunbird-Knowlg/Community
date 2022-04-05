---
description: This page lists the jobs belong to Sunbird Knowlg.
---

# Knowlg Jobs

### asset-enrichment:&#x20;

Job is used to enrich the uploaded image and video media files as part of the ECML contents. As part of image media file enrichment, image resizing with optimal DPI is done. As part of video media file enrichment, fetching of video metadata, generation of a thumbnail for the video and triggering video-stream-generator job for generation of streamable source is done.

_Source Code:_ [https://github.com/Jayaprakash8887/knowledge-platform-jobs/tree/release-4.8.0/asset-enrichment](https://github.com/Jayaprakash8887/knowledge-platform-jobs/tree/release-4.8.0/asset-enrichment)

### audit-event-generator:&#x20;

Job uses the neo4j transactions to generate audit events.

_Source Code:_ [https://github.com/Jayaprakash8887/knowledge-platform-jobs/tree/release-4.8.0/audit-event-generator](https://github.com/Jayaprakash8887/knowledge-platform-jobs/tree/release-4.8.0/audit-event-generator)

### audit-history-indexer:&#x20;

Job uses the neo4j transactions to index transactions for audit purpose. old and new values of the updated object in each neo4j transacrion will be audited.

_Source Code:_ [https://github.com/Jayaprakash8887/knowledge-platform-jobs/tree/release-4.8.0/audit-history-indexer](https://github.com/Jayaprakash8887/knowledge-platform-jobs/tree/release-4.8.0/audit-history-indexer)

### post-publish-processor:&#x20;

Job is used for trigerring post publish activities when a collection is published. Like,

* Re-publishing herarchy information of shallow copy type of collections when an origin collection is published.
* DIAL Code generation, linking and QR Code image generation for reserved DIAL code by default for a course.
* Based on 'traceability' configuration, triggering auto batch creation for a Course if there is no running batch existing.

_Source Code:_ [https://github.com/Jayaprakash8887/knowledge-platform-jobs/tree/release-4.8.0/post-publish-processor](https://github.com/Jayaprakash8887/knowledge-platform-jobs/tree/release-4.8.0/post-publish-processor)

### content-publish:&#x20;

Job is used for publishing content/collection objects that are submitted for publishing. Job takes care of downloading of media files and packaging them as ECAR for offline consumption.

_Source Code:_ [https://github.com/Jayaprakash8887/knowledge-platform-jobs/tree/release-4.8.0/publish-pipeline](https://github.com/Jayaprakash8887/knowledge-platform-jobs/tree/release-4.8.0/publish-pipeline)

### qrcode-image-generator:&#x20;

Job is used for generating QR Code images for the reserved DIAL codes of a collection using the process Id generated when the [DIAL code reserve API](http://docs.sunbird.org/latest/apis/dialapi/#operation/Reserve%20Dialcode) is invoked.

_Source Code:_ [https://github.com/Jayaprakash8887/knowledge-platform-jobs/tree/release-4.8.0/qrcode-image-generator](https://github.com/Jayaprakash8887/knowledge-platform-jobs/tree/release-4.8.0/qrcode-image-generator)

### search-indexer:&#x20;

Job uses neo4j transactions to index the objects' metadata into Composite search index and DIAL code index in Elaticsearch.

_Source Code:_ [https://github.com/Jayaprakash8887/knowledge-platform-jobs/tree/release-4.8.0/search-indexer](https://github.com/Jayaprakash8887/knowledge-platform-jobs/tree/release-4.8.0/search-indexer)

### video-stream-generator:&#x20;

Job is used to generate streaming media of the uploaded video contents (mp4 and webm mimeTypes).

_Source Code:_ [https://github.com/Jayaprakash8887/knowledge-platform-jobs/tree/release-4.8.0/video-stream-generator](https://github.com/Jayaprakash8887/knowledge-platform-jobs/tree/release-4.8.0/video-stream-generator)



{% hint style="danger" %}
<mark style="color:orange;">**Note:**</mark> Some of the jobs were part of [Samza jobs](https://github.com/project-sunbird/sunbird-learning-platform/tree/master/platform-jobs/samza) before release-4.8.0. Since release-4.8.0, all knowlg jobs are part of [Flink jobs](https://github.com/project-sunbird/knowledge-platform-jobs/tree/release-4.8.0).
{% endhint %}

