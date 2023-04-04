# Release - 5.4.0(latest)

## <mark style="color:blue;">5.4.0</mark> (15-03-2023)

Discussion thread: [https://github.com/orgs/Sunbird-Knowlg/discussions/93](https://github.com/orgs/Sunbird-Knowlg/discussions/93)

Release timeline:

|                | Start date  | End date     |
| -------------- | ----------- | ------------ |
| Planning phase | 02-Jan-2023 | 13-Jan-2023  |
| Sprint 1       | 16-Jan-2023 | 03-Feb- 2023 |
| Sprint 2       | 06-Feb-2023 | 24-Feb-2023  |
| PPV            | 27-Feb-2023 | 10-Mar-2023  |
| Prod           | 13-Mar-2023 |              |

### Document Release Version

| Project        | Release Version | Date          |
| -------------- | --------------- | ------------- |
| Sunbird Knowlg | R5.4.0          | 15 March 2022 |

### **1. Summary of the changes**

This document contains information about the new features and enhancements planned to the Knowlg building block as part of release 5.4.0:

Enhancements: Click [here](https://project-sunbird.atlassian.net/issues/?filter=12759\&jql=project%20%3D%20KN%20AND%20issuetype%20in%20\(Documentation-Issue%2C%20Minor-Enhancement%2C%20RFC\)%20AND%20status%20in%20\(Done%2C%20%22In%20Validation%22\)%20AND%20labels%20in%20\(QA\_Not\_Required%2C%20QA\_Required%2C%20QA\_Required\_Regression%2C%20Regression\)%20AND%20Sprint%20in%20\(351%2C%20352\)%20ORDER%20BY%20key%20ASC%2C%20created%20DESC) to view the list.&#x20;

Bug Fixes - click [here](https://project-sunbird.atlassian.net/issues/?filter=12759\&jql=project%20%3D%20KN%20AND%20issuetype%20%3D%20Bug%20AND%20status%20in%20\(Done%2C%20%22In%20Validation%22\)%20AND%20labels%20in%20\(QA\_Not\_Required%2C%20QA\_Required%2C%20QA\_Required\_Regression%2C%20Regression\)%20AND%20Sprint%20in%20\(351%2C%20352\)%20ORDER%20BY%20key%20ASC%2C%20created%20DESC) to see the list of bugs fixed in this release.

**Test Scenarios:**[ **Link**](https://docs.google.com/spreadsheets/d/1YOe4QB0gqA53gFTzsP-6MtQI02EaKiUzn1SPihZPaeM/edit#gid=117864265)****

**Documentation issue, release 5.4.0:** [KN-839](https://project-sunbird.atlassian.net/browse/KN-839)

## Release Tags:

### Collection **Editor**:

Tag: v5.4.3

Install: _npm i @project-sunbird/sunbird-collection-editor@_5.4.3

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.4.3](https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.4.3)

### API Services:

| Component        | Service To Build                                | Build Tag                                                                                            | Service To Deploy                                         | Deploy Tag                                                                                                      | Comment                                                                                                                                                      |
| ---------------- | ----------------------------------------------- | ---------------------------------------------------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Assessment       | Build/job/Core/job/Assessment/                  | [Release-5.4.0\_RC1](https://github.com/Sunbird-inQuiry/inquiry-api-service/tree/release-5.4.0\_RC1) | Deploy/job/dev/job/Kubernetes/job/Assessment/             | [release-5.2.0-inquiry\_RC1](https://github.com/project-sunbird/sunbird-devops/tree/release-5.2.0-inquiry\_RC1) | Deploy Tag is given for reference only. Please do not use directly for deployment. For Detailed Configuration Details, Please refer to Configuration Section |
| InQuiryFlink Job | Build/job/KnowledgePlatform/job/InquiryFlinkJob | [Release-5.2.0\_RC3](https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-5.2.0\_RC3)       | Deploy/job/dev/job/KnowledgePlatform/job/InquiryFlinkJob/ | [Release-5.2.0\_RC3](https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-5.2.0\_RC3)                  | <p>Please deploy below jobs:<br><code>async-questionset-publish</code><br><code>questionset-republish</code></p>                                             |

| Component                | Service to be Build              | Tag                                                                                                                | Deploy Job                         | Deployment Tag                                                                                                        | Comment                                                                                                                                                        |
| ------------------------ | -------------------------------- | ------------------------------------------------------------------------------------------------------------------ | ---------------------------------- | --------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Knowledge-platform       | Build/Kubernetes/Content         | [release-5.4.0\_RC1](https://github.com/project-sunbird/knowledge-platform/releases/tag/release-5.4.0\_RC1)        | Deploy/Kubernetes/Content          | [release-5.4.0-knowlg\_RC1](https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.4.0-knowlg\_RC1) | Deploy Tag is given for reference only. Please do not use directly for deployment. For Detailed Configuration Details, Please refer to SYNC Tool configuration |
| Knowledge-platform-jobs  | Build/KnowldgePlatform/Flinkjobs | [release-5.4.0\_RC1](https://github.com/project-sunbird/knowledge-platform-jobs/releases/tag/release-5.4.0\_RC1)   | Deploy/KnowledgePlatform/FlinkJobs | [release-5.4.0\_RC1](https://github.com/project-sunbird/sunbird-learning-platform/releases/tag/release-5.4.0\_RC1)    | <p>Deploy the </p><p><strong>qrcode-image-generator</strong></p><p>flink job</p>                                                                               |
| Sunbird-learning-service | Build/KnowledgePlatform/Learning | [release-5.4.0\_RC1](https://github.com/project-sunbird/sunbird-learning-platform/releases/tag/release-5.4.0\_RC1) | Deploy/KnowledgePlatform/Learning  | [release-5.4.0\_RC1](https://github.com/project-sunbird/sunbird-learning-platform/releases/tag/release-5.4.0\_RC1)    |                                                                                                                                                                |

#### KN-802: SYNC Tool configuration update

| **Variable**                     | **Values**                                                  | **description**                                                                                                                                         |
| -------------------------------- | ----------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `replace_dest_string`            | true/false                                                  | Used to specify if the Relative path string replace is to be enabled                                                                                    |
| `replace_src_string_DIAL_store`  | `DIAL_STORAGE_BASE_PATH`                                    | Currently configured relative path variable name to be stored in database instead of BLOB absolute URL                                                  |
| `replace_dest_string_DIAL_store` | Ex: `https://sunbirddevbbpublic.blob.core.windows.net/dial` | BLOB URL and container combination value that is used to replace ‘`DIAL_STORAGE_BASE_PATH`’ relative path variable while syncing image ‘url’ data to ES |

### ****
