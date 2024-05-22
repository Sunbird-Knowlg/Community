# Release - 6.1.0 (latest)

## <mark style="color:blue;">Hot-fix 6.1.0</mark> (08-05-2024)

1. Image URL is not getting generated when QR code is searched - [KN-1071](https://project-sunbird.atlassian.net/browse/KN-1071)

### Release Tags

<table><thead><tr><th width="186.5">Component</th><th>Service to be Build</th><th width="100">Tag</th><th>Deploy Job</th><th>Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Schema upload</td><td>NA</td><td>NA</td><td>Deploy/Kubernetes/UploadSchema</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-6.1.0_RC2">release-6.1.0_RC2</a></td><td></td></tr><tr><td>Knowledge-platform</td><td>Build/Core/Content</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-6.1.0_RC2">release-6.1.0_RC2</a></td><td>Deploy/Kubernetes/Content</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td>Deploy Tag is given for reference only. Please do not use directly for deployment.</td></tr></tbody></table>

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

<table data-full-width="true"><thead><tr><th>Component</th><th>Service to be Build</th><th>Tag</th><th>Deploy Job</th><th>Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Schema upload</td><td>NA</td><td>NA</td><td>Deploy/Kubernetes/UploadSchema</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-6.1.0_RC1">release-6.1.0_RC1</a></td><td></td></tr><tr><td>Knowledge-platform</td><td>Build/Core/Content</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-6.1.0_RC1">release-6.1.0_RC1</a></td><td>Deploy/Kubernetes/Content</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td>Deploy Tag is given for reference only. Please do not use directly for deployment.</td></tr><tr><td></td><td>Build/Core/Taxonomy</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/tree/release-6.1.0_RC4">release-6.1.0_RC4</a></td><td>Deploy/Kubernetes/Taxonomy</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td>Deploy Tag is given for reference only. Please do not use directly for deployment.</td></tr><tr><td></td><td>Build/Core/search</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/tree/release-6.1.0_RC4">release-6.1.0_RC4</a></td><td>Deploy/Kubernetes/Search</td><td></td><td>Deploy Tag is given for reference only. Please do not use directly for deployment.</td></tr><tr><td>dial-service</td><td>Build/Core/Dial</td><td><a href="https://github.com/Sunbird-Knowlg/sunbird-dial-service/releases/tag/release-6.1.0_RC1">release-6.1.0_RC1</a></td><td>Deploy/Kubernetes/Dial</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td>Deploy Tag is given for reference only. Please do not use directly for deployment.</td></tr><tr><td>Knowledge-platform-jobs</td><td>Build/KnowledgePlatform/FlinkJobs</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform-jobs/tree/release-6.1.0_RC1">release-6.1.0_RC1</a></td><td>Deploy/KnowledgePlatform/FlinkJobs</td><td><a href="https://github.com/Sunbird-Knowlg/sunbird-learning-platform/commits/release-5.7.0_RC4">release-5.7.0_RC4</a></td><td><p>Jobs to be deployed: </p><ol><li><strong>Search-indexer</strong></li><li><strong>asset-enrichment</strong></li><li><strong>Content-publish</strong></li><li><strong>post-publish-processor</strong> </li><li><strong>qrcode-image-generator</strong></li><li><strong>video-stream-generator</strong></li></ol></td></tr></tbody></table>

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



