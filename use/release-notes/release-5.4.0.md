# Release - 5.4.0

## <mark style="color:blue;">Hot-fix 5.4.1</mark> (4-07-2023)

**Bugs:**

* Image URL is null when user downloads course QR code from Published bucket- [KN-889](https://project-sunbird.atlassian.net/browse/KN-889)

| Component               | Build Job                         | Build Tag                                                                                                       | Deploy Job                         | Deployment                                                                                                | Comment                                                                                   |
| ----------------------- | --------------------------------- | --------------------------------------------------------------------------------------------------------------- | ---------------------------------- | --------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| Knowledge-platform-jobs | Build/KnowledgePlatform/FlinkJobs | [release-5.4.1\_RC1](https://github.com/Sunbird-Knowlg/knowledge-platform-jobs/releases/tag/release-5.4.1\_RC1) | Deploy/KnowledgePlatform/FlinkJobs | [release-5.4.1\_RC1](https://github.com/Sunbird-Knowlg/sunbird-learning-platform/tree/release-5.4.1\_RC1) | <p>Jobs to be deployed:</p><p><strong>qrcode-image-generator</strong></p><p>flink job</p> |

**Enhancement:**

* As part of KN-889 enhancement has been done to Sync Tool - [KN-889](https://project-sunbird.atlassian.net/browse/KN-889)

'_syncdialcodes_' command has been enhanced to accept '--filenames' as input parameter to which QR Code file names from _dial codes.dialcode\_images_ can be passed to sync '_imageUrl_' of DIAL codes to Elastic search

Sample Command:

```
java -Dconfig.file=/home/learning/sync_tool/application.conf -jar sync-tool-0.0.1-SNAPSHOT.jar syncdialcodes --filenames 0_U7J3S8,0_R9Y6W5
```

<table><thead><tr><th width="186.5">Component</th><th>Service to be Build</th><th width="100">Tag</th><th>Deploy Job</th><th>Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Sunbird-learning-service</td><td>Build/KnowledgePlatform/Learning</td><td><a href="https://github.com/Sunbird-Knowlg/sunbird-learning-platform/releases/tag/release-5.4.1_RC1">release-5.4.1_RC1</a></td><td>Deploy/KnowledgePlatform/Learning</td><td><a href="https://github.com/Sunbird-Knowlg/sunbird-learning-platform/releases/tag/release-5.4.1_RC1">release-5.4.1_RC1</a></td><td></td></tr></tbody></table>

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

<table><thead><tr><th width="229">Project</th><th>Release Version</th><th>Date</th></tr></thead><tbody><tr><td>Sunbird Knowlg</td><td>R5.4.0</td><td>15 March 2022</td></tr></tbody></table>

### **1. Summary of the changes**

This document contains information about the new features and enhancements planned to the Knowlg building block as part of release 5.4.0:

Enhancements: Click [here](https://project-sunbird.atlassian.net/issues/?filter=12759\&jql=project%20%3D%20KN%20AND%20issuetype%20in%20\(Documentation-Issue%2C%20Minor-Enhancement%2C%20RFC\)%20AND%20status%20in%20\(Done%2C%20%22In%20Validation%22\)%20AND%20labels%20in%20\(QA\_Not\_Required%2C%20QA\_Required%2C%20QA\_Required\_Regression%2C%20Regression\)%20AND%20Sprint%20in%20\(351%2C%20352\)%20ORDER%20BY%20key%20ASC%2C%20created%20DESC) to view the list.&#x20;

Bug Fixes - click [here](https://project-sunbird.atlassian.net/issues/?filter=12759\&jql=project%20%3D%20KN%20AND%20issuetype%20%3D%20Bug%20AND%20status%20in%20\(Done%2C%20%22In%20Validation%22\)%20AND%20labels%20in%20\(QA\_Not\_Required%2C%20QA\_Required%2C%20QA\_Required\_Regression%2C%20Regression\)%20AND%20Sprint%20in%20\(351%2C%20352\)%20ORDER%20BY%20key%20ASC%2C%20created%20DESC) to see the list of bugs fixed in this release.

**Test Scenarios:**[ **Link**](https://docs.google.com/spreadsheets/d/1YOe4QB0gqA53gFTzsP-6MtQI02EaKiUzn1SPihZPaeM/edit#gid=117864265)

**Documentation issue, release 5.4.0:** [KN-839](https://project-sunbird.atlassian.net/browse/KN-839)

## Release Tags:

### Collection **Editor**:

Tag: v5.4.3

Install: _npm i @project-sunbird/sunbird-collection-editor@_5.4.3

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.4.3](https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.4.3)

### API Services:

<table><thead><tr><th width="186.5">Component</th><th>Service to be Build</th><th width="100">Tag</th><th>Deploy Job</th><th>Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>dial-service</td><td>Build/Core/Dial</td><td><a href="https://github.com/Sunbird-Knowlg/sunbird-dial-service/releases/tag/release-5.4.0_RC1">release-5.4.0_RC1</a></td><td>Deploy/Kubernetes/Dial</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.4.0-knowlg_RC1">release-5.4.0-knowlg_RC1</a></td><td>Deploy Tag is given for reference only. Please do not use directly for deployment. For Detailed Configuration Details, Please refer to SYNC Tool configuration</td></tr><tr><td>Knowledge-platform-jobs</td><td>Build/KnowldgePlatform/Flinkjobs</td><td><a href="https://github.com/project-sunbird/knowledge-platform-jobs/releases/tag/release-5.4.0_RC1">release-5.4.0_RC1</a></td><td>Deploy/KnowledgePlatform/FlinkJobs</td><td><a href="https://github.com/project-sunbird/sunbird-learning-platform/releases/tag/release-5.4.0_RC1">release-5.4.0_RC1</a></td><td><p>Deploy the </p><p><strong>qrcode-image-generator</strong></p><p>flink job</p></td></tr><tr><td>Sunbird-learning-service</td><td>Build/KnowledgePlatform/Learning</td><td><a href="https://github.com/project-sunbird/sunbird-learning-platform/releases/tag/release-5.4.0_RC1">release-5.4.0_RC1</a></td><td>Deploy/KnowledgePlatform/Learning</td><td><a href="https://github.com/project-sunbird/sunbird-learning-platform/releases/tag/release-5.4.0_RC1">release-5.4.0_RC1</a></td><td></td></tr></tbody></table>

#### KN-802: SYNC Tool configuration update

| **Variable**                     | **Values**                                                  | **description**                                                                                                                                         |
| -------------------------------- | ----------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `replace_dest_string`            | true/false                                                  | Used to specify if the Relative path string replace is to be enabled                                                                                    |
| `replace_src_string_DIAL_store`  | `DIAL_STORAGE_BASE_PATH`                                    | Currently configured relative path variable name to be stored in database instead of BLOB absolute URL                                                  |
| `replace_dest_string_DIAL_store` | Ex: `https://sunbirddevbbpublic.blob.core.windows.net/dial` | BLOB URL and container combination value that is used to replace ‘`DIAL_STORAGE_BASE_PATH`’ relative path variable while syncing image ‘url’ data to ES |

###
