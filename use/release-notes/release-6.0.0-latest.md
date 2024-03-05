# Release - 6.0.0 (latest)

## <mark style="color:blue;">6.0.0</mark> (04-03-2024)

Discussion thread: [https://github.com/orgs/Sunbird-Knowlg/discussions/189](https://github.com/orgs/Sunbird-Knowlg/discussions/189)

Release timeline:

|                | Start date   | End date     |
| -------------- | ------------ | ------------ |
| Planning phase | 23-Oct, 2023 | 3-Nov, 2023  |
| Sprint 1       | 6-Nov, 2023  | 24-Nov, 2023 |
| Sprint 2       | 27-Nov, 2023 | 15-Feb, 2024 |
| PPV            | 16-Feb, 2024 | 1-Mar, 2024  |
| Prod           | 4-Mar, 2024  |              |

**6.0.0 total scope**: [Link](https://project-sunbird.atlassian.net/issues/?filter=12876)

### **1. Summary of the changes**

This document contains information about the new features and enhancements planned to the Knowlg building block as part of release 6.0.0:

Enhancements: Click [here](https://project-sunbird.atlassian.net/issues/?filter=12902) to view the list.

Bug Fixes - click [here](https://project-sunbird.atlassian.net/issues/?filter=12903) to see the list of bugs fixed in this release.

**Test Scenarios:** [**KN-968**](https://project-sunbird.atlassian.net/browse/KN-968)

### Document Release Version

<table><thead><tr><th width="229">Project</th><th>Release Version</th><th>Date</th></tr></thead><tbody><tr><td>Sunbird Knowlg</td><td>R6.0.0</td><td></td></tr></tbody></table>

### **Important note to the adopters:**

As part of this release, we have made the below changes, which are important to know everyone.

1.  As part of our efforts to address **vulnerabilities**, we've upgraded the following version in each repository.

    1. We've upgraded the **Angular version to 15** for our players.
       1. sunbird-pdf-player
       2. sunbird-video-player
       3. sunbird-epub-player
    2.  We've updated the following dependencies for the sunbird-cloud-storage-sdk:



        |                 | **From** | **TO** |
        | --------------- | -------- | ------ |
        | Tika version    | 1.18     | 2.9.0  |
        | jackson version | 2.7.8    | 2.13.5 |
    3.  We've updated the following dependencies for the DIAL-servcie:

        |                         | **From** | **TO**   |
        | ----------------------- | -------- | -------- |
        | org.xerial.snappy       | 1.0.9.6  | 1.1.10.4 |
        | jackson version         | 2.9.8    | 2.13.5   |
        | logback-classic         |          | 1.2.0    |
        | logback-core            |          | 1.2.9    |
        | xercesImpl              |          | 2.12.2   |
        | jackson-dataformat-cbor |          | 2.12.1   |
        | gson                    |          | 2.8.9    |
    4. We've updated the following dependencies for the content-servcie, taxonomy-servcie & search-servcie:

    |                   | **From** | **TO** |
    | ----------------- | -------- | ------ |
    | Play version      | 2.7.2    | 2.8.20 |
    | jackson version   | 2.9.8    | 2.13.5 |
    | cloud storage sdk | 1.4.6    | 1.4.7  |


2.  As part of this release, we planned to fix **vulnerabilities** in Knowlg building block, and we have finished for below repos.

    1. knowledge-platform
    2. sunbird-dial-service
    3. sunbird-pdf-player
    4. sunbird-video-player
    5. sunbird-epub-player

    _<mark style="color:red;">**Note:**</mark> <mark style="color:red;"></mark><mark style="color:red;">We also started to fix</mark> <mark style="color:red;"></mark><mark style="color:red;">`knowledge-platform-jobs`</mark> <mark style="color:red;"></mark><mark style="color:red;">but we encountered some issues so we will fix this repo for upcoming release.</mark>_

### Following are the Planned Tickets of R 6.0.0

#### New Features:

None

#### Enhancements / Technical tasks::

<table><thead><tr><th width="83.33333333333331">S.no</th><th width="124">JIRA ID</th><th>Description</th></tr></thead><tbody><tr><td>1</td><td><a href="https://project-sunbird.atlassian.net/browse/KN-939">KN-939</a></td><td>Fixing vulnerabilities in Knowlg building block</td></tr><tr><td>2</td><td><a href="https://project-sunbird.atlassian.net/browse/KN-968">KN-968</a></td><td>Term create API enhancement</td></tr><tr><td>3</td><td><a href="https://project-sunbird.atlassian.net/browse/KN-955">KN-955</a></td><td>Framework API automation (Framework category and Framework term)</td></tr><tr><td>4</td><td><a href="https://project-sunbird.atlassian.net/browse/KN-958">KN-958</a></td><td>Content APIs automation</td></tr></tbody></table>

### Release Tags:

### Upgrade Knowlg From 5.7.0 to 6.0.0

### API Services:

<table><thead><tr><th width="186.5">Component</th><th>Service to be Build</th><th width="100">Tag</th><th>Deploy Job</th><th>Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Knowledge-platform</td><td>Build/Core/Content</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-6.0.0_RC1">release-6.0.0_RC1</a></td><td>Deploy/Kubernetes/Content</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td>Deploy Tag is given for reference only. Please do not use directly for deployment.</td></tr><tr><td></td><td>Build/Core/Taxonomy</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-6.0.0_RC1">release-6.0.0_RC1</a></td><td>Deploy/Kubernetes/Taxonomy</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td>Deploy Tag is given for reference only. Please do not use directly for deployment.</td></tr><tr><td></td><td>Build/Core/search</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-6.0.0_RC1">release-6.0.0_RC1</a></td><td>Deploy/Kubernetes/Search</td><td></td><td>Deploy Tag is given for reference only. Please do not use directly for deployment.</td></tr><tr><td>dial-service</td><td>Build/Core/Dial</td><td><a href="https://github.com/Sunbird-Knowlg/sunbird-dial-service/releases/tag/release-6.0.0_RC1">release-6.0.0_RC1</a></td><td>Deploy/Kubernetes/Dial</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td>Deploy Tag is given for reference only. Please do not use directly for deployment.</td></tr></tbody></table>

### PDF  **Player**:

**Angular Library**

**Install:** _npm i @project-sunbird/sunbird-pdf-player-v9@6.0.0_

[https://www.npmjs.com/package/@project-sunbird/sunbird-pdf-player-v9/v/6.0.0](https://www.npmjs.com/package/@project-sunbird/sunbird-pdf-player-v9/v/6.0.0)

**Web component**

**Install:** _npm i @project-sunbird/sunbird-pdf-player-web-component@1.2.0_

[https://www.npmjs.com/package/@project-sunbird/sunbird-pdf-player-web-component/v/1.2.0](https://www.npmjs.com/package/@project-sunbird/sunbird-pdf-player-web-component/v/1.2.0)

### Epub  **Player**:

**Angular Library**

**Install:** _npm i @project-sunbird/sunbird-epub-player-v9@6.0.0_

[https://www.npmjs.com/package/@project-sunbird/sunbird-epub-player-v9/v/6.0.0](https://www.npmjs.com/package/@project-sunbird/sunbird-epub-player-v9/v/6.0.0)

**Web component**

**Install:** _npm i @project-sunbird/sunbird-epub-player-web-component@1.2.0_

[https://www.npmjs.com/package/@project-sunbird/sunbird-epub-player-web-component/v/1.2.0](https://www.npmjs.com/package/@project-sunbird/sunbird-epub-player-web-component/v/1.2.0?activeTab=versions)

### Video  **Player**:

**Angular Library**

**Install:** _npm i @project-sunbird/sunbird-video-player-v9@6.0.0_

&#x20;[https://www.npmjs.com/package/@project-sunbird/sunbird-video-player-v9/v/6.0.0](https://www.npmjs.com/package/@project-sunbird/sunbird-video-player-v9/v/6.0.0)

**Web component**

**Install:** _npm i @project-sunbird/sunbird-epub-player-web-component@1.1.0_

&#x20;[https://www.npmjs.com/package/@project-sunbird/sunbird-video-player-web-component/v/1.1.1](https://www.npmjs.com/package/@project-sunbird/sunbird-video-player-web-component/v/1.1.1)

### Telemetry JS SDK:

**Install:** _npm i @project-sunbird/telemetry-sdk@1.3.0_

[https://www.npmjs.com/package/@project-sunbird/telemetry-sdk/v/1.3.0](https://www.npmjs.com/package/@project-sunbird/telemetry-sdk/v/1.3.0)



