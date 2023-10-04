---
description: This page addresses frequently asked questions about Collection Service.
---

# FAQs

### What is the life-cycle of a collection object?

Collection when created will have '**Draft**' status. When the Collection is submitted for Review, collection status will be updated to '**Review**'. When a Collection is accepted (submitted for publishing), status will first move to 'Processing' and then to '**Live**' if it is processed successfully else to '**Failed**'. When a published collection is edited, an **image** node gets created with the id ending with '**.img**' (do\_Id.img). Status of the image node will be 'Draft' whereas status of non-image node will be 'Live'. Image node will follow the above life cycle.

When a collection in 'Review' status is rejected in Review, status of the collection will be updated back to 'Draft'.

When a collection is submitted for delete/retire, status of the collection will be updated to '**Retired**'.

### What happens when a collection object is Retired?

When a collection retire API is triggered, status of the collection will be updated to '**Retired**'. Please note that when a collection with both actual node and image node existing is retired, **image node is hard deleted** from the system and actual node's status is updated to '**Retired**'.

### Can I delete only the image node of a collection object?

Yes, discard collection API can be used to delete the image node of a collection object. Please note that the image node will be **hard deleted** from the system.

### What happens when Discard API is used on a collection object with only actual node?

Actual node will be **hard deleted** from the system.

### Can I add/remove contents to/from collections without needing to update collection hierarchy using Update Hierarchy API?

Yes, using [Add Hierarchy API](https://documenter.getpostman.com/view/25463377/2s8ZDa32au) and Remove Hierarchy API, one can add or remove contents/collections to/from a collection unit.

### How are the collection objects stored in database?

Collection object metadata is stored in the Neo4j database. Uploaded appIcon images are stored in Cloud. Collection Hierarchy is stored in json format in Cassandra database. Metadata is synced to Elasticsearch and Redis.

### How to read actual node metadata and image node metadata?

Actual node metadata can be read using 'Read Collection API' URL in the format '/collection/v1/read/do\_id'.

Image node metadata can be read using 'Read Collection API' URL in the format '/Collection/v1/read/do\_id\*\*?mode=edit\*\*' or '/collection/v1/read/do\_id\*\*.img\*\*'.

### What happens in Collection 'Publish'?

When a Collection object Publish API is invoked, after metadata validation, content-publish flink job is invoked using respective kafka topic. In the flink job, post the pkgVersion validation, a collection is first updated to 'Processing' status. Later, packaging of the collection starts (ECAR generation) with types ONLINE and SPINE. Once ECAR is generated and uploaded to cloud, status is updated to 'Live'.
