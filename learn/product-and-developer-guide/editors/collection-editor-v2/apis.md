# APIs

### [**DIAL Service**](../../dialcode/apis.md)

The DIAL service is used to generate, link, and check the status of the DIAL code.

<table><thead><tr><th width="248.78987889750402">API</th><th>Description</th></tr></thead><tbody><tr><td><code>{host}/action/dialcode/v1/reserve/{collection_id}</code></td><td>To <code>reserve</code> DIAL codes for the collection.</td></tr><tr><td><code>{host}/action/dialcode/v1/process/status/{process_id}</code></td><td>To check the status of  QR Code images generation of the reserved DIAL codes . </td></tr><tr><td><code>{host}/action/dialcode/v3/search</code></td><td>It is used for searching the DIAL codes of a channel.</td></tr></tbody></table>

### [**Collection service**](../../content-service/content-service-1/content-api.md)

It is used to organize your assets in a multi-level hierarchy and creation processes like Draft, Review, and Publish

<table><thead><tr><th width="271.8951583323191">API</th><th>Description</th></tr></thead><tbody><tr><td><code>{host}/action/content/v3/hierarchy/update</code></td><td>It is used to update hierarchy of the collection.</td></tr><tr><td><code>{host}/action/content/v3/hierarchy/{collection_id}?mode=edit</code></td><td>This is used to fetch the collection hierarchy in the draft/review status.</td></tr><tr><td><code>{host}/action/content/v3/review/{collection_id}</code></td><td>It is used to send the collection for review.</td></tr><tr><td><code>{host}/action/content/v3/reject/{collection_id}</code></td><td>To reject the collection which is up for review.</td></tr><tr><td><code>{host}/action/content/v3/publish/{collection_id}</code></td><td>To publish the content which is up for review.</td></tr></tbody></table>

### [**Content service**](../../content-service/content-apis/content-api.md)

It is used to fetch the content metadata.

<table><thead><tr><th width="319.40060078281294">API</th><th>Description</th></tr></thead><tbody><tr><td><code>{host}/action/content/v3/read/{content_id}</code></td><td>This is used to fetch the published content metadata.</td></tr><tr><td><code>{host}/content/data/v1/telemetry</code></td><td>It is used to log the <a href="http://127.0.0.1:5000/o/-Mi9QwJlsfb7xuxTBc0J/s/-MkM7F4oILSpCJPO0YUu/">telemetry</a> data.</td></tr></tbody></table>

### [**Channel Service**](../../content-service/channel-service/apis.md)

It's used to fetch the channel details.

<table><thead><tr><th width="306.8770382608114">API</th><th>Description</th></tr></thead><tbody><tr><td><code>{host}/api/channel/v1/read/{channel_id}</code></td><td>It is used to read a <a href="../../content-service/channel-service/">channel</a> details.</td></tr></tbody></table>

### [**Media service**](../../content-service/content-service-2/content-api.md)

The asset manager for easy creation and discovery of assets (Images, Videos, etc…)

<table><thead><tr><th width="283.8642226748133">API</th><th>Description</th></tr></thead><tbody><tr><td><code>{host}/action/asset/v1/create</code></td><td>It is used to create asset(media files) viz images, videos</td></tr><tr><td><code>{host}/action/content/v3/upload/url/{asset_id}</code></td><td>It is used to fetch the pre-signed cloud URL location to upload asset. </td></tr><tr><td><code>{host}/action/asset/v1/upload/{asset_id}</code></td><td>It is used to upload the asset artifact to the pre-signed cloud URL location.</td></tr></tbody></table>

### [**Assets search service**](../../assets-search-service/apis.md)

The asset search service provides services to search and discover [assets](../../assets-search-service/).

<table><thead><tr><th width="284.81864841745085">API</th><th>Description</th></tr></thead><tbody><tr><td><code>{host}/action/composite/v3/search</code></td><td>Used for fetching objects such as Collection, Content, Asset, etc...</td></tr></tbody></table>

### [**Framework Service**](../../taxonomy-and-tagging/framework-service/apis.md)

The framework service provides the ability to organize and manage. It is used to identify the “relevant” learning assets to be shown for users.

<table><thead><tr><th width="302.5">API</th><th>Description</th></tr></thead><tbody><tr><td><code>{host}/api/framework/v1/read/{framework_id}</code></td><td>Fetching a specific <a href="../../taxonomy-and-tagging/framework-service/">framework</a></td></tr></tbody></table>

### [**Object Category Service**](../../taxonomy-and-tagging/object-category-service/apis.md)

It is used to configure fields displayed in a form used in editors for the creation, modification, and viewing of an asset

<table><thead><tr><th width="249.67764401568172">API</th><th>Description</th></tr></thead><tbody><tr><td><code>{host}/action/object/category/definition/v1/read?fields=objectMetadata,forms,name</code></td><td>It is used to read <a href="../../taxonomy-and-tagging/object-category-service/">object category defination</a> of a primary category. (Ex. Digital textbook, Explanation Resourse, etc...)</td></tr></tbody></table>

### [<mark style="color:blue;">**User Service**</mark>](http://127.0.0.1:5000/s/4ZKyfmmhMWpPkD6iYvKF/learn/product-and-developer-guide/user-and-org-service/api-documentation)

The user service is used to fetch the list of users for [collaboration](features.md).  It's optional service when collaboration feature is disabled in the editor.

<table><thead><tr><th width="317.1284403669724">API</th><th>Description</th></tr></thead><tbody><tr><td><code>{host}/action/user/v1/search?fields=orgName</code></td><td>For searching a particular user of a channel.</td></tr></tbody></table>
