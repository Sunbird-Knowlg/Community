---
description: Multilevel hierarchy contents like Book, Course, Collection, etc.
---

# Collection Editor - V2

Collection Editor - V2 is a generalized editor which can be used for creating, viewing and editing multiple types of learning assets that are assets of collection mime-type. They can be - a collection of content (like textbook, course, program etc.), a Question set (collection of questions) or any other object type that is a collection of other objects. The generalized collection editor has the following benefits:

* Ensure all existing collection categories like textbook, course use the same code. Hence, ease of maintenance.
* Editors for new collection categories can be enabled with minimal or no coding.

### :stars:Capabilities

* [x] Efficient and performant handling of large data sets
* [x] Ability to load dynamic reactive forms and validations of form through configuration
* [x] Configuration driven architecture
* [x] The asset manager for easy creation and discovery of assets (Images, Videos, etc…)
* [x] Ability to organize your assets in a multi-level hierarchy
* [x] Ability to generate and link DIALcode(QRCodes) to any level of hierarchy.
* [x] Ability to preview linked assets
* [x] Collaboration of users
* [x] Collection creation processes like Draft, Review, and Publish

### :stars:Tech Stack

1. Angular
2. Typescript
3. Javascript
4. HTML/SCSS

### :stars:Installation guide

{% content-ref url="../../../../use/installation-guide/editors/collection-editor-v2.md" %}
[collection-editor-v2.md](../../../../use/installation-guide/editors/collection-editor-v2.md)
{% endcontent-ref %}

### :stars:APIs

* [**DIAL Service**](../../dialcode/apis.md)****\
  ****The DIAL service is used to generate, link, and check the status of the DIAL code.

| API                                                     | Description                                                                     |
| ------------------------------------------------------- | ------------------------------------------------------------------------------- |
| `{host}/action/dialcode/v1/reserve/{collection_id}`     | To `reserve` DIAL codes for the collection.                                     |
| `{host}/action/dialcode/v1/process/status/{process_id}` | To check the status of  QR Code images generation of the reserved DIAL codes .  |
| `{host}/action/dialcode/v3/search`                      | It is used for searching the DIAL codes of a channel.                           |



* [**Collection service**](../../content-service-1/content-api.md)****\
  ****It is used to organize your assets in a multi-level hierarchy and creation processes like Draft, Review, and Publish

| API                                                            | Description                                                                |
| -------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `{host}/action/content/v3/hierarchy/update`                    | It is used to update hierarchy of the collection.                          |
| `{host}/action/content/v3/hierarchy/{collection_id}?mode=edit` | This is used to fetch the collection hierarchy in the draft/review status. |
| `{host}/action/content/v3/review/{collection_id}`              | It is used to send the collection for review.                              |
| `{host}/action/content/v3/reject/{collection_id}`              | To reject the collection which is up for review.                           |
| `{host}/action/content/v3/publish/{collection_id}`             | To publish the content which is up for review.                             |

* [**Content service**](../../content-service/content-api.md)****\
  ****It is used to fetch the content metadata.

| API                                          | Description                                           |
| -------------------------------------------- | ----------------------------------------------------- |
| `{host}/action/content/v3/read/{content_id}` | This is used to fetch the published content metadata. |
| `{host}/content/data/v1/telemetry`           | It is used to log the telemetry data.                 |

* [**Channel Service**](../../content-service/channel-service/apis.md)****\
  ****It's used to fetch the channel details.

| API                                       | Description                           |
| ----------------------------------------- | ------------------------------------- |
| `{host}/api/channel/v1/read/{channel_id}` | It is used to read a channel details. |

* [**Media service**](../../content-service-2/content-api.md)****\
  ****The asset manager for easy creation and discovery of assets (Images, Videos, etc…)

| API                                              | Description                                                                   |
| ------------------------------------------------ | ----------------------------------------------------------------------------- |
| `{host}/action/asset/v1/create`                  | It is used to create asset(media files) viz images, videos                    |
| `{host}/action/content/v3/upload/url/{asset_id}` | It is used to fetch the pre-signed cloud URL location to upload asset.        |
| `{host}/action/asset/v1/upload/{asset_id}`       | It is used to upload the asset artifact to the pre-signed cloud URL location. |

* [**Assets search service**](../../assets-search-service/apis.md)****\
  ****The asset search service provides services to search and discover assets.

| API                                 | Description                                                          |
| ----------------------------------- | -------------------------------------------------------------------- |
| `{host}/action/composite/v3/search` | Used for fetching objects such as Collection, Content, Asset, etc... |

* [**Framework Service**](../../taxonomy-and-tagging/framework-service/apis.md)****\
  ****The framework service provides the ability to create, organize and manage taxonomy frameworks.

| API                                           | Description                   |
| --------------------------------------------- | ----------------------------- |
| `{host}/api/framework/v1/read/{framework_id}` | Fetching a specific framework |

* [**Object Category Service**](../../taxonomy-and-tagging/object-category-service/apis.md)****\
  ****It is used to configure fields displayed in a form used in editors for the creation, modification, and viewing of an asset

| API                                                                                 | Description                                                                                                               |
| ----------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `{host}/action/object/category/definition/v1/read?fields=objectMetadata,forms,name` | It is used to read object category defination of a primary category. (Ex. Digital textbook, Explanation Resourse, etc...) |

* <mark style="color:blue;">****</mark>[<mark style="color:blue;">**User Service**</mark>](https://app.gitbook.com/s/4ZKyfmmhMWpPkD6iYvKF/learn/product-and-developer-guide/user-and-org-service/api-documentation)<mark style="color:blue;">****</mark>\ <mark style="color:blue;">****</mark>The user service is used to fetch the list of users for collaboration.

| API                                           | Description                                   |
| --------------------------------------------- | --------------------------------------------- |
| `{host}/action/user/v1/search?fields=orgName` | For searching a particular user of a channel. |
