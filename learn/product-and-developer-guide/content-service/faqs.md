---
description: This page addresses frequently asked questions about Content Service.
---

# FAQs

### What is the life-cycle of a content object?

Content when created will have '**Draft**' status. When the Content is submitted for Review, content status will be updated to '**Review**'. When a Content is accepted (submitted for publishing), status will first move to 'Processing' and then to '**Live**' if it is processed successfully else to '**Failed**'. When a published content is edited, a **image** node gets created with the id ending with '**.img**' (do\_Id.img). Status of the image node will be 'Draft' whereas status of non-image node will be 'Live'. Image node will follow the above life cycle.

When a content in 'Review' status is rejected in Review, status of the content will be updated back to 'Draft'.

When a content is submitted for delete/retire, status of the content will be updated to '**Retired**'.

### What happens when a content object is Retired?

When a content retire API is triggered, status of the content will be updated to '**Retired**'. Please note that when a content with both actual node and image node existing is retired, **image node is hard deleted** from the system and actual node's status is updated to '**Retired**'.

### Can I delete only the image node of a content object?

Yes, discard content API can be used to delete the image node of a content object. Please note that the image node will be **hard deleted** from the system.

### What happens when Discard API is used on a content object with only actual node?

Actual node will be **hard deleted** from the system.

### How is Search Content API different from Composite Search API?

[Search Content API](http://docs.sunbird.org/latest/apis/contentapi/index.html#operation/Search%20Content) can be used for fetching object types 'Content', 'ContentImage', 'Collection', 'CollectionImage' and 'Asset' only. Whereas, [Composite search API](http://docs.sunbird.org/latest/apis/searchapi/#tag/Search-APIs) can be used for fetching all types of objects in the application ('Content', 'ContentImage', 'Collection', 'CollectionImage', 'QuestionSet', 'QuestionSetImage', 'Asset', 'Channel', 'Framework', 'ObjectCategory', 'ObjectCategoryDefintion', 'License', 'Question', etc. )

Note: All attributes in [respective object schemas'](https://github.com/project-sunbird/knowledge-platform/tree/master/schemas) can be used for searching in API filters. However, 'objectType' attribute cannot be used in [Search Content API](http://docs.sunbird.org/latest/apis/contentapi/index.html#operation/Search%20Content).

### How are the content objects stored in database?

Content object metadata is stored in the Neo4j database. Uploaded Source for a content and appIcon images are stored in Cloud. Metadata is synced to Elasticsearch and Redis.

### How to read actual node metadata and image node metadata?

Actual node metadata can be read using 'Read Content API' URL in the format '/content/v2/read/do\_id'.

Image node metadata can be read using 'Read Content API' URL in the format '/content/v2/read/do\_id\*\*?mode=edit\*\*' or '/content/v2/read/do\_id\*\*.img\*\*'.

### How to read ECML content 'body'?

ECML content 'body' can be fetched using 'Read Content API' URL in the format '/content/v2/read/do\_id\*\*?fields=body\*\*'.

### What happens in Content 'Publish'?

When a Content object Publish API is invoked, after metadata validation, content-publish flink job is invoked using respective kafka topic. In the flink job, post the pkgVersion validation, a content is first updated to 'Processing' status. Later, packaging of the content starts (ECAR generation) with types SPINE and FULL. Once ECAR is generated and uploaded to cloud, status is updated to 'Live'.

### How to upload a content?

{% embed url="http://docs.sunbird.org/latest/developer-docs/how-to-guide/how_to_upload_existing_content" %}

### What file formats can be uploaded as content?

Currently, the platform supports the following formats for compiled content:

* Text (.pdf)
* Video (.mp4, .webm, YouTube URLs)
* HTML (as .zip)
* ECML (created using the inbuilt content editor)
* EPUB
* H5P

### How the HTML zip content needs to be packaged for upload?

* 'index.html' in the .zip is a must.
* There can be only one level of folders directly inside zip. sub folders (Folders within folders) are not allowed/may not work well.
* File names and Folder names should not contain special characters. It can only be alphanumeric.

### Which attribute of a content contains the uploaded source file path?

When a file is uploaded as a content, source file is copied to the configured cloudstorage blob path and the blob path url is saved in '**artifactUrl**' attribute. When a video content is published, as a post publish process, streaming source is generated and the path is saved in '**streamingUrl**' attribute.
