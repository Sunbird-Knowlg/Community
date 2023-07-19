# Release - 5.6.0 (latest)

## <mark style="color:blue;">5.6.0</mark> (12-07-2023)

Discussion thread: [https://github.com/orgs/Sunbird-Knowlg/discussions/128](https://github.com/orgs/Sunbird-Knowlg/discussions/128)

Release timeline:

<table><thead><tr><th></th><th width="192.33333333333331">Start date</th><th>End date</th></tr></thead><tbody><tr><td>Planning phase</td><td>28-Apr, 2023</td><td>12-May, 2023</td></tr><tr><td>Sprint 1</td><td>15-May, 2023</td><td>2-Jun, 2023</td></tr><tr><td>Sprint 2</td><td>5-Jun, 2023</td><td>23-Jun, 2023</td></tr><tr><td>PPV</td><td>26-Jun, 2023</td><td>7-Jul, 2023</td></tr><tr><td>Prod</td><td><mark style="color:red;">12 July 2023</mark> (<mark style="color:green;">delayed 2 days</mark>)</td><td></td></tr></tbody></table>

### Document Release Version

<table><thead><tr><th width="229">Project</th><th>Release Version</th><th>Date</th></tr></thead><tbody><tr><td>Sunbird Knowlg</td><td>R5.6.0</td><td>12 July 2023</td></tr></tbody></table>

### **Important note to the adopters:**

As part of this release, we have made two changes which are important to know everyone.

1. As part of the Knowlg Platform upgrade, the Scala version has been updated from 2.11 to 2.12. This upgrade encompasses changes in the Graph engine as well.
2. We have migrated all taxonomy APIs from the learning-service to the taxonomy-service and eliminated the corresponding code from the learning-service. Our plan is to completely decommission the learning-service in the upcoming release, pending confirmation that no APIs are being served from the learning-service.

### Following are the Planned Tickets of R 5.6.0

#### New Features:

None

#### Enhancements / Technical tasks::

<table><thead><tr><th width="83.33333333333331">S.no</th><th width="124">JIRA ID</th><th>Description</th></tr></thead><tbody><tr><td>1</td><td><a href="https://project-sunbird.atlassian.net/browse/KN-10">KN-10</a></td><td>Refactoring taxonomy API's</td></tr><tr><td>2</td><td><a href="https://project-sunbird.atlassian.net/browse/KN-848">KN-848</a></td><td>[Stack] Update Scala version(2.11 to 2.12)</td></tr><tr><td>3</td><td><a href="https://project-sunbird.atlassian.net/browse/KN-868">KN-868</a></td><td>Updating PDF, Video, EPUB player from angular libraries to web component in Collection editor</td></tr><tr><td>4</td><td><a href="https://project-sunbird.atlassian.net/browse/KN-868">KN-869</a></td><td>POC: Change of Graph Database for Sunbird Knowlg</td></tr></tbody></table>

### Release Tags:

#### Upgrade Knowlg From 5.5.0 to 5.6.0

### API Services:

<table><thead><tr><th width="186.5">Component</th><th>Service to be Build</th><th width="100">Tag</th><th>Deploy Job</th><th>Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Schema upload</td><td>NA</td><td>NA</td><td>Deploy/Kubernetes/UploadSchema</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-5.6.0_RC2">release-5.6.0_RC2</a></td><td></td></tr><tr><td>Knowledge-platform</td><td>Build/Core/Content</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-5.6.0_RC3">release-5.6.0_RC3</a></td><td>Deploy/Kubernetes/Content</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td></td></tr><tr><td></td><td>Build/Core/Taxonomy</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-5.6.0_RC2">release-5.6.0_RC2</a></td><td>Deploy/Kubernetes/Taxonomy</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td></td></tr><tr><td>Knowledge-mw-service</td><td>Build/Core/KnowledgeMW</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-mw-service/releases/tag/release-5.6.0_RC1">release-5.6.0_RC1</a></td><td>Deploy/Kubernetes/KnowledgeMW</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td></td></tr><tr><td>Sunbird-learning-service</td><td>Build/KnowledgePlatform/Learning</td><td><a href="https://github.com/Sunbird-Knowlg/sunbird-learning-platform/releases/tag/release-5.6.0_RC1">release-5.6.0_RC1</a></td><td>Deploy/KnowledgePlatform/Learning</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td></td></tr></tbody></table>

### Collection Editor Web Component:

Tag: `v1.1.0`

Install: `npm i @project-sunbird/sunbird-collection-editor-web-component@1.1.0`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor-web-component/v/1.1.0](https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor-web-component/v/1.1.0)

### Configuration/Environment variable changes:

#### Knowledge-mw-service:

To provide the taxonomy service URL in the Knowledge Middleware (Knowlg MW) service, you can add the following environment variable:

Variable name: `sunbird_taxonomy_service_api_base_url`&#x20;

Value: \[`http://taxonomy-service:9000`]

Make sure to replace `[http://taxonomy-service:9000]` with the actual URL of the taxonomy service. By setting this environment variable, the Knowlg MW service will be able to connect to the taxonomy service using the specified URL.

#### Knowledge-platform -> Taxonomy Service:

Add the below env variables in `taxonomy-service_application.conf`

1. framework.keyspace="\{{ lp\_cassandra\_keyspace\_prefix \}}\_hierarchy\_store"&#x20;
2. framework.hierarchy.table="framework\_hierarchy"&#x20;
3. framework.categories\_cached=\["subject", "medium", "gradeLevel", "board"]&#x20;
4. framework.cache.ttl=86400 framework.cache.read=true&#x20;
5. framework.max\_term\_creation\_limit=200

**NOTE:** In the previous configuration, these settings were included in the sunbird-learning-service. However, for this release, we have transferred all framework APIs to the taxonomy-service. Therefore, you will need to add the above configuration as part of the `taxonomy-service_application.conf` file.

### Deprecations and Removals:

As part of this release, we have deprecated the below list of APIs.

<table><thead><tr><th width="96">S.No</th><th>API</th></tr></thead><tbody><tr><td>1</td><td>/framework/v3/list</td></tr><tr><td>2</td><td>/framework/v3/term/search</td></tr><tr><td>3</td><td>/framework/v3/category/search</td></tr><tr><td>4</td><td>/framework/v3/category/master/search</td></tr></tbody></table>

### Breaking changes (The existing features will break the if we don’t do the below actions):

During the upgrade to version 5.6.0, it is essential to ensure that the mentioned services and environments are properly updated. Previously, the APIs mentioned were part of the sunbird-learning-service, but now they have been moved to the content-service & taxonomy-service without altering the API contract. Additionally, changes have been made to ensure that these APIs are no longer served from the sunbird-learning-service.&#x20;

Therefore, it is crucial to verify that the necessary updates are implemented correctly for a smooth transition to version 5.6.0.

**List of APIs moved to Content Service:**

<table><thead><tr><th width="89">S.No</th><th>API</th></tr></thead><tbody><tr><td>1</td><td>/content/v3/publish</td></tr><tr><td>2</td><td>/content/v3/retire</td></tr><tr><td>3</td><td>/content/v3/unlisted/publish</td></tr><tr><td>4</td><td>/content/v3/dialcode/link</td></tr><tr><td>5</td><td>/content/v3/dialcode/release</td></tr><tr><td>6</td><td>/content/v3/dialcode/reserve</td></tr></tbody></table>

**List of APIs moved to Taxonomy Service:**

<table><thead><tr><th width="94">S.No</th><th>API</th></tr></thead><tbody><tr><td>1</td><td>/framework/v3/read</td></tr><tr><td>2</td><td>/framework/v3/create</td></tr><tr><td>3</td><td>/framework/v3/update</td></tr><tr><td>4</td><td>/framework/v3/copy</td></tr><tr><td>5</td><td>/framework/v3/publish</td></tr><tr><td>6</td><td>/framework/v3/retire</td></tr><tr><td>7</td><td>/framework/v3/term/read</td></tr><tr><td>8</td><td>/framework/v3/term/create</td></tr><tr><td>9</td><td>/framework/v3/term/update</td></tr><tr><td>10</td><td>/framework/v3/term/retire</td></tr><tr><td>11</td><td>/framework/v3/category/read</td></tr><tr><td>12</td><td>/framework/v3/category/create</td></tr><tr><td>13</td><td>/framework/v3/category/update</td></tr><tr><td>14</td><td>/framework/v3/category/retire</td></tr><tr><td>15</td><td>/framework/v3/category/master/create</td></tr><tr><td>16</td><td>/framework/v3/category/master/update</td></tr><tr><td>17</td><td>/framework/v3/category/master/read</td></tr><tr><td>18</td><td>/framework/v3/category/master/retire</td></tr></tbody></table>

### Additional Info:

**Test Scenarios:** [Link](https://project-sunbird.atlassian.net/browse/KN-901)

**Documentation issue, release 5.6.0:** [Link](https://project-sunbird.atlassian.net/browse/KN-897)
