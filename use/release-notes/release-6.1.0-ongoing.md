# Release - 6.1.0 (Ongoing)

## <mark style="color:blue;">6.1.0</mark> (Ongoing)

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

### Release Tags: <a href="#release-tags" id="release-tags"></a>

### Upgrade Knowlg From 6.0.0 to 6.1.0

### API Services:

| Component               | Service to be Build               | Tag                                                                                                          | Deploy Job                         | Deployment Tag                                                                                                        | Comment                                                                                                                                                                                                                                                                                                                                                                             |
| ----------------------- | --------------------------------- | ------------------------------------------------------------------------------------------------------------ | ---------------------------------- | --------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Schema upload           | NA                                | NA                                                                                                           | Deploy/Kubernetes/UploadSchema     | [release-6.1.0\_RC1](https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-6.1.0\_RC1)            |                                                                                                                                                                                                                                                                                                                                                                                     |
| Knowledge-platform      | Build/Core/Content                | [release-6.1.0\_RC1](https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-6.1.0\_RC1)   | Deploy/Kubernetes/Content          | [release-5.6.0-knowlg\_RC1](https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg\_RC1) | Deploy Tag is given for reference only. Please do not use directly for deployment.                                                                                                                                                                                                                                                                                                  |
|                         | Build/Core/Taxonomy               | [release-6.1.0\_RC1](https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-6.1.0\_RC1)   | Deploy/Kubernetes/Taxonomy         | [release-5.6.0-knowlg\_RC1](https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg\_RC1) | Deploy Tag is given for reference only. Please do not use directly for deployment.                                                                                                                                                                                                                                                                                                  |
|                         | Build/Core/search                 | [release-6.1.0\_RC1](https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-6.1.0\_RC1)   | Deploy/Kubernetes/Search           |                                                                                                                       | Deploy Tag is given for reference only. Please do not use directly for deployment.                                                                                                                                                                                                                                                                                                  |
| dial-service            | Build/Core/Dial                   | [release-6.1.0\_RC1](https://github.com/Sunbird-Knowlg/sunbird-dial-service/releases/tag/release-6.1.0\_RC1) | Deploy/Kubernetes/Dial             | [release-5.6.0-knowlg\_RC1](https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg\_RC1) | Deploy Tag is given for reference only. Please do not use directly for deployment.                                                                                                                                                                                                                                                                                                  |
| Knowledge-platform-jobs | Build/KnowledgePlatform/FlinkJobs | [release-6.1.0\_RC1](https://github.com/Sunbird-Knowlg/knowledge-platform-jobs/tree/release-6.1.0\_RC1)      | Deploy/KnowledgePlatform/FlinkJobs | [release-5.7.0\_RC3](https://github.com/Sunbird-Knowlg/sunbird-learning-platform/commits/release-5.7.0\_RC3)          | <p>Jobs to be deployed: </p><ol><li><strong>Search-indexer</strong></li><li><strong>transaction-event-processor</strong></li><li><strong>asset-enrichment</strong></li><li><strong>Content-publish</strong> </li><li><strong>post-publish-processor</strong> </li><li><strong>qrcode-image-generator</strong> </li><li><strong>video-stream-generator</strong></li></ol><p><br></p> |

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





