# Release - 6.1.0 (latest)

## <mark style="color:blue;">Hot-fix 6.1.0</mark> (18-06-2024)

1. Knowlg: Replace Azure Media Services with MediaKind(MK.IO)

### Overview:

This hot-fix addresses the upcoming retirement of Azure Media Services (AMS) on June 30, 2024. To ensure a smooth transition, we are implementing MediaKind, a Microsoft partner solution, as an alternative to AMS. Currently, Azure Media Services is used for generating streaming URLs. Due to its upcoming retirement, we are transitioning to MediaKind to maintain continuity in our streaming services.

### Details:

#### Issue Fixed

Azure Media Services will be retired on June 30, 2024. As a replacement, we are migrating to MediaKind. This includes:&#x20;

1. Generating streaming URLs for new assets using MediaKind.
2. Migrating all existing streaming assets to MediaKind.&#x20;

#### Migration Steps to MediaKind (MK.IO)

To migrate Azure Media Services (AMS) data to MediaKind (MK.IO), follow these steps:

1. **Get an MK.IO Subscription**:
   * Visit [MK.IO Sign-Up](https://docs.mk.io/docs/sign-up) for subscription details and registration.
2. **Generate MediaKind Authentication Token**:
   * Once your MK.IO subscription is activated, log in to your MK.IO account.
   * Navigate to [MediaKind Authentication Token](https://api.mk.io/auth/token/) to generate an authentication token for accessing MediaKind APIs.
3. **Connect Your Azure Storage Account**:
   * Refer to [Connecting My Current Storage Accounts](https://docs.mk.io/docs/connecting-my-current-storage-accounts) in the MK.IO documentation for detailed instructions on connecting your Azure storage account.
4. **Create a Streaming Endpoint**:
   * During the creation of a streaming endpoint, provide a name and select the appropriate streaming endpoint type as per your requirements.
5. **Create a Transform in Video Processing**:
   * When creating a transform in Video Processing, specify a name and choose a suitable Built-in preset value according to your encoding needs.

#### Additional Information

* **Preparation for Migration**:
  * Ensure you are logged into your MK.IO account before accessing the provided links.
  * Follow the steps sequentially for a smooth migration process from AMS to MediaKind (MK.IO).
* **Additional Resources**:
  * For detailed steps on using MK.IO APIs, refer to [MK.IO APIs Step-by-Step Guide](https://support.mk.io/portal/en/kb/articles/how-to-use-mkio-apis-step-by-step).
  * Watch a tutorial on setting up MK.IO on [YouTube](https://www.youtube.com/watch?v=uMRn7bDcb-o).
*   **Bulk Migration Documentation**:

    * Once the above steps are completed, refer to the document for instructions on bulk migration of old assets from AMS to your MK.IO account.

    [https://docs.mk.io/docs/bulk-asset-migration-from-ams-storage](https://docs.mk.io/docs/bulk-asset-migration-from-ams-storage)

_**NOTE: Once migration done. We need to republish the contents**:_

* _As we know, streaming URLs are stored in content metadata, which we use to play the streaming assets. Since these assets are migrated to MK.IO, the base path will change as shown below. Therefore, we need to republish all those contents._

**Before Migration: Azure Streaming URL**:

```bash
https://sunbirddevmedia-inct.streaming.media.azure.net/daac53ae-f3a9-44b6-a546-7fc08c37848c/do_2133506859240161281539_163308.ism/manifest(format=m3u8-cmaf)
```

**After Migration: MK.IO Streaming URL**:

```bash
https://ep-default-mkservicepoc.japaneast.streaming.mediakind.com/daac53ae-f3a9-44b6-a546-7fc08c37848c/do_2133506859240161281539_163308.ism/manifest(format=m3u8-cmaf)
```

* If you observe both URLs, only the base path is changing.

### Configuration/Environment variable changes: <a href="#configuration-environment-variable-changes" id="configuration-environment-variable-changes"></a>

#### New Configurations:&#x20;

| Variable Name	                         | Description                                                                                                                                                                           | Default Value                                     |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------- |
| azure\_mediakind.project\_name         | MK.IO subscription name                                                                                                                                                               |                                                   |
| azure\_mediakind.auth\_token           | MK.IO authentication token to access the MediaKind APIs. Please refer above **step2** for auth token generation.                                                                      |                                                   |
| azure\_mediakind.account\_name         | MK.IO storage account name. Please refer above **step3** to get this name.                                                                                                            |                                                   |
| azure\_mediakind.api.endpoint          | MK.IO API endpoint                                                                                                                                                                    | [https://api.mk.io/api](https://api.mk.io/api%22) |
| azure\_mediakind.transform.default     | Please refer above **step5** to get this value. While creating we have used name `media_transform_default` that is waht we kept as default you can this value whatever name you want. | media\_transform\_default                         |
| azure\_mediakind.stream.base\_url      | Please refer above **step4** to get this value. Once you created streaming endpoint it will provide some base url copy that value here.                                               |                                                   |
| azure\_mediakind.stream.endpoint\_name | Please refer above **step4** to get this value.                                                                                                                                       |                                                   |
| azure\_mediakind.stream.protocol       |                                                                                                                                                                                       | Hls                                               |
| azure\_mediakind.stream.policy\_name   |                                                                                                                                                                                       | Predefined\_ClearStreamingOnly                    |

#### Deprecated Configurations:

| Variable Name	                               | Description                             |
| -------------------------------------------- | --------------------------------------- |
| media\_service\_azure\_tenant                | Azure media service tenant name         |
| media\_service\_azure\_subscription\_id      | Azure media service subscription ID     |
| media\_service\_azure\_account\_name         | Azure media service account name        |
| media\_service\_azure\_resource\_group\_name | Azure media service resource group name |
| media\_service\_azure\_token\_client\_key    | Azure media service client key          |
| media\_service\_azure\_token\_client\_secret | Azure media service client secret       |



### Release Tags

<table><thead><tr><th width="186.5">Component</th><th>Service to be Build</th><th width="100">Tag</th><th>Deploy Job</th><th>Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Knowledge-platform-jobs</td><td>Build/KnowledgePlatform/FlinkJobs</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform-jobs/releases/tag/release-6.1.0_RC2">release-6.1.0_RC2</a></td><td>Deploy/KnowledgePlatform/FlinkJobs</td><td><a href="https://github.com/Sunbird-Knowlg/sunbird-learning-platform/releases/tag/release-5.7.0_RC7">release-5.7.0_RC7</a></td><td>Jobs to be deployed:<br>1. <strong>video-stream-generator</strong></td></tr></tbody></table>



## <mark style="color:blue;">Hot-fix 6.1.0</mark> (07-06-2024)

1. DIAL service Build issue fix

### Release Tags

<table><thead><tr><th width="186.5">Component</th><th>Service to be Build</th><th width="100">Tag</th><th>Deploy Job</th><th>Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>dial-service</td><td>Build/Core/Dial</td><td><a href="https://github.com/Sunbird-Knowlg/sunbird-dial-service/releases/tag/release-6.1.0_RC2">release-6.1.0_RC2</a></td><td>Deploy/Kubernetes/Dial</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td>Deploy Tag is given for reference only. Please do not use directly for deployment.</td></tr></tbody></table>

## <mark style="color:blue;">Hot-fix 6.1.0</mark> (08-05-2024)

1. Image URL is not getting generated when QR code is searched - [KN-1071](https://project-sunbird.atlassian.net/browse/KN-1071)

### Release Tags

<table><thead><tr><th width="186.5">Component</th><th>Service to be Build</th><th width="100">Tag</th><th>Deploy Job</th><th>Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Schema upload</td><td>NA</td><td>NA</td><td>Deploy/Kubernetes/UploadSchema</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-6.1.0_RC2">release-6.1.0_RC2</a></td><td></td></tr><tr><td>Knowledge-platform</td><td>Build/Core/Content</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-6.1.0_RC2">release-6.1.0_RC2</a></td><td>Deploy/Kubernetes/Content</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td>Deploy Tag is given for reference only. Please do not use directly for deployment.</td></tr><tr><td></td><td>Build/Core/Taxonomy</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-6.1.0_RC6">release-6.1.0_RC6</a></td><td>Deploy/Kubernetes/Taxonomy</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td>Deploy Tag is given for reference only. Please do not use directly for deployment.</td></tr></tbody></table>

### Configuration/Environment variable changes:

#### Variables Added in Content-Service:

| Variable Name                   | Description                                                  | Default Value |
| ------------------------------- | ------------------------------------------------------------ | ------------- |
| cloud\_storage\_dial\_container | Storage container name to store dial codes                   | dial          |
| dialcode\_image.keyspace        | Keyspace name to store dial code images details in Cassandra | dialcodes     |



## <mark style="color:blue;">6.1.0</mark> (29-04-2024)

Discussion thread: [https://github.com/orgs/Sunbird-Knowlg/discussions/190](https://github.com/orgs/Sunbird-Knowlg/discussions/190)

Release timeline:

|                | Start date   | End date     |
| -------------- | ------------ | ------------ |
| Planning phase | 12-Feb, 2024 | 23-Feb, 2024 |
| Sprint 1       | 26-Feb, 2024 | 15-Mar, 2024 |
| Sprint 2       | 18-Mar, 2024 | 5-Apr, 2024  |
| PPV            | 8-Apr, 2024  | 19-Apr, 2024 |
| Prod           | 22-Apr, 2024 |              |

**6.1.0 total scope**: [Link](https://project-sunbird.atlassian.net/issues/?filter=12877)

## Document Release Version

| Project        | Release Version | Date |
| -------------- | --------------- | ---- |
| Sunbird Knowlg | R6.1.0          |      |

## **Important note to the adopters:**

As part of this release, we have made the below changes, which are important to know everyone.

### **We have upgraded Elasticsearch upgrade 6.8.22 to 7.17.13 —** [**KN-976**](https://project-sunbird.atlassian.net/browse/KN-976)

#### Elasticsearch Upgrade Release Notes: 6.8.22 to 7.17.13

**Upgrade Overview:**

This release involves upgrading Elasticsearch from version 6.8.22 to version 7.17.13. The upgrade brings significant enhancements, bug fixes, and potential breaking changes that administrators and developers need to be aware of.

**Upgrade Steps:**

1. **Preparation:**
   * Ensure compatibility with Java 11, as Elasticsearch 7.17.13 requires this version.
2. **Backup:**
   * Before proceeding with the upgrade, ensure all data is backed up to prevent any loss during the migration process.
   * Please [**Click here**](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/3446112295/Elasticsearch+Backup+Restore+In+Azure+and+Local+Environment) for Backup & Restore In Local & Azure documentation
3. **Upgrade Process:**
   * Follow the Elasticsearch upgrade documentation for detailed instructions on upgrading from version 6.8.22 to 7.17.13.
   * Please  [**Click Here**](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/3439198248/Elasticsearch+Version+Upgrade+6.8.23+to+7.17.13) for upgrading ES from 6.8.22 to 7.17.13 documentation.

Once you have upgraded to Elasticsearch 7.17.13, please consider using the below release tags for API services and Flink Jobs deployment.

### Following are the Planned Tickets of R 6.1.0 <a href="#release-tags" id="release-tags"></a>

#### New Features:

None

#### Enhancements / Technical tasks:

<table><thead><tr><th width="83.33333333333331">S.no</th><th width="165">JIRA ID</th><th>Description</th></tr></thead><tbody><tr><td>1</td><td><a href="https://project-sunbird.atlassian.net/browse/KN-976">KN-976</a></td><td>Elasticsearch upgrade 6.8.22 to 7.17.13</td></tr><tr><td>2</td><td><a href="https://project-sunbird.atlassian.net/browse/KN-982">KN-982</a></td><td>Sunbird Video Player - Angular version upgrade 15 to 17</td></tr><tr><td>3</td><td><a href="https://project-sunbird.atlassian.net/browse/KN-983">KN-983</a></td><td>Sunbird PDF Player - Angular version upgrade 15 to 17</td></tr><tr><td>4</td><td><a href="https://project-sunbird.atlassian.net/browse/KN-979">KN-979</a></td><td>Angular version update for Player SDK from 13 to 17</td></tr><tr><td>5</td><td><a href="https://project-sunbird.atlassian.net/browse/KN-1068">KN-1068</a></td><td>Sunbird Collection editor documentation changes</td></tr><tr><td>6</td><td><a href="https://project-sunbird.atlassian.net/browse/KN-879">KN-879</a></td><td>DIAL code APIs Move from Knowlg MW to Content Service</td></tr></tbody></table>

### Release Tags: <a href="#release-tags" id="release-tags"></a>

### Upgrade Knowlg From 6.0.0 to 6.1.0

### API Services:

<table data-full-width="true"><thead><tr><th>Component</th><th>Service to be Build</th><th>Tag</th><th>Deploy Job</th><th>Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Schema upload</td><td>NA</td><td>NA</td><td>Deploy/Kubernetes/UploadSchema</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-6.1.0_RC1">release-6.1.0_RC1</a></td><td></td></tr><tr><td>Knowledge-platform</td><td>Build/Core/Content</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-6.1.0_RC1">release-6.1.0_RC1</a></td><td>Deploy/Kubernetes/Content</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td>Deploy Tag is given for reference only. Please do not use directly for deployment.</td></tr><tr><td></td><td>Build/Core/Taxonomy</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/tree/release-6.1.0_RC4">release-6.1.0_RC4</a></td><td>Deploy/Kubernetes/Taxonomy</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td>Deploy Tag is given for reference only. Please do not use directly for deployment.</td></tr><tr><td></td><td>Build/Core/search</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/tree/release-6.1.0_RC4">release-6.1.0_RC4</a></td><td>Deploy/Kubernetes/Search</td><td></td><td>Deploy Tag is given for reference only. Please do not use directly for deployment.</td></tr><tr><td>dial-service</td><td>Build/Core/Dial</td><td><a href="https://github.com/Sunbird-Knowlg/sunbird-dial-service/releases/tag/release-6.1.0_RC1">release-6.1.0_RC1</a></td><td>Deploy/Kubernetes/Dial</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td>Deploy Tag is given for reference only. Please do not use directly for deployment.</td></tr><tr><td>Knowledge-platform-jobs</td><td>Build/KnowledgePlatform/FlinkJobs</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform-jobs/tree/release-6.1.0_RC1">release-6.1.0_RC1</a></td><td>Deploy/KnowledgePlatform/FlinkJobs</td><td><a href="https://github.com/Sunbird-Knowlg/sunbird-learning-platform/releases/tag/release-5.7.0_RC6">release-5.7.0_RC6</a></td><td><p>Jobs to be deployed: </p><ol><li><strong>Search-indexer</strong></li><li><strong>asset-enrichment</strong></li><li><strong>Content-publish</strong></li><li><strong>post-publish-processor</strong> </li><li><strong>qrcode-image-generator</strong></li><li><strong>video-stream-generator</strong></li><li><strong>transaction-event-processor (This job is Optional. )</strong></li></ol></td></tr></tbody></table>

**Note:** _transaction-event-processor Flink job is optional. Because we merged both audit-history-indexer & audit-event-generator into one job. If you want to continue with two separate jobs, you don't need to deploy transaction-event-processor Flink job._

### Sunbird player SDK:

**Angular version - 13**

**Install:** _npm i @project-sunbird/sunbird-player-sdk-v9@6.0.2_

[ ](https://www.npmjs.com/package/@project-sunbird/sunbird-player-sdk-v9/v/6.0.2)[https://www.npmjs.com/package/@project-sunbird/sunbird-player-sdk-v9/v/6.0.2](https://www.npmjs.com/package/@project-sunbird/sunbird-player-sdk-v9/v/6.0.2)

**Angular version - 14**

**Install:** _npm i @project-sunbird/sunbird-player-sdk-v9@6.0.3_

[https://www.npmjs.com/package/@project-sunbird/sunbird-player-sdk-v9/v/6.0.3](https://www.npmjs.com/package/@project-sunbird/sunbird-player-sdk-v9/v/6.0.3)

**Angular version - 15**

**Install:** _npm i @project-sunbird/sunbird-player-sdk-v9@6.0.4_

[https://www.npmjs.com/package/@project-sunbird/sunbird-player-sdk-v9/v/6.0.4](https://www.npmjs.com/package/@project-sunbird/sunbird-player-sdk-v9/v/6.0.4)

**Angular version - 16**

**Install:** _npm i @project-sunbird/sunbird-player-sdk-v9@6.0.5_

[https://www.npmjs.com/package/@project-sunbird/sunbird-player-sdk-v9/v/6.0.5](https://www.npmjs.com/package/@project-sunbird/sunbird-player-sdk-v9/v/6.0.5)

**Angular version - 17**

**Install:** _npm i @project-sunbird/sunbird-player-sdk-v9@6.0.7_

[https://www.npmjs.com/package/@project-sunbird/sunbird-player-sdk-v9/v/6.0.7](https://www.npmjs.com/package/@project-sunbird/sunbird-player-sdk-v9/v/6.0.7)

### Sunbird PDF Player:

**Angular version - 16**

**Install:** _npm i @project-sunbird/sunbird-pdf-player-v9@6.1.0_

[https://www.npmjs.com/package/@project-sunbird/sunbird-pdf-player-v9/v/6.1.0](https://www.npmjs.com/package/@project-sunbird/sunbird-pdf-player-v9/v/6.1.0)

**Angular version - 17**

**Install:** _npm i @project-sunbird/sunbird-pdf-player-v9@6.1.1_

[https://www.npmjs.com/package/@project-sunbird/sunbird-pdf-player-v9/v/6.1.1](https://www.npmjs.com/package/@project-sunbird/sunbird-pdf-player-v9/v/6.1.1)

### Sunbird Video Player:

**Angular Version - 16**

**Install:** _npm i @project-sunbird/sunbird-video-player-v9@6.1.0_

[https://www.npmjs.com/package/@project-sunbird/sunbird-video-player-v9/v/6.1.0](https://www.npmjs.com/package/@project-sunbird/sunbird-video-player-v9/v/6.1.0)

**Angular Version - 17**

**Install:** _npm i @project-sunbird/sunbird-video-player-v9@6.1.1_

[https://www.npmjs.com/package/@project-sunbird/sunbird-video-player-v9/v/6.1.1](https://www.npmjs.com/package/@project-sunbird/sunbird-video-player-v9/v/6.1.1)

### Configuration/Environment variable changes:

In this release, we've transferred the following two APIs from _**Knowledge-MW-service**_ to _**Content-Service.**_ Because we moved these APIs to the _**Content-Service**_, the endpoints have been updated to ensure consistency with other content APIs.

<table><thead><tr><th width="89">S.No</th><th>Old API Endpoint</th><th>New API Endpoint</th></tr></thead><tbody><tr><td>1</td><td>/v1/dialcode/reserve/:identifier</td><td>/content/v3/dialcode/reserve/:identifier (OR)<br>/content/v4/dialcode/reserve/:identifier</td></tr><tr><td>2</td><td>/v1/dialcode/process/status</td><td><p>/content/v3/process/status/:processid</p><p>(OR)<br>/content/v4/process/status/:processid</p></td></tr></tbody></table>

Consequently, to reflect these changes, we'll need to update the _**upstream\_url**_ configuration in kong-api layer to reference Content-Service instead of Knowledge-MW-service.&#x20;

**Previous:**

```
- name: reserveDialcode
  uris: "{{ dialcode_service_prefix }}/v1/reserve"
  upstream_url: "{{ knowledge_mw_service_url }}/v1/dialcode/reserve"
  
- name: qrCodeBatchProcessStatus
  uris: "{{ dialcode_service_prefix }}/v1/process/status"
  upstream_url: "{{ knowledge_mw_service_url }}/v1/dialcode/process/status"
```

**Update to:**

```
- name: reserveDialcode
  uris: "{{ dialcode_service_prefix }}/v1/reserve"
  upstream_url: "{{ content_service_url }}/content/v3/dialcode/reserve"
  
- name: qrCodeBatchProcessStatus
  uris: "{{ dialcode_service_prefix }}/v1/process/status"
  upstream_url: "{{ content_service_url }}/content/v3/process/status
```

#### Variables Added in Content-Service:

| Variable Name            | Description                                                   | Default Value                     |
| ------------------------ | ------------------------------------------------------------- | --------------------------------- |
| kafka.dial.request.topic | Input Kafka Topic Name                                        | \{{ env\_name \}}.qrimage.request |
| dialcode.keyspace        | Keyspace name to store dial code process details in Cassandra | dialcodes                         |



