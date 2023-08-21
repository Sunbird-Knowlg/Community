# Release - 5.5.0

## <mark style="color:blue;">Hot-fix 5.5.1</mark> (08-08-2023)

**Enhancement:**

KN-902: CSP changes

As part of this hotfix, we have integrated a JavaScript file upload library. This library is designed to function with presignedURLs, file objects, and provider names. Depending on the provided values, the library will initiate interactions with the specified cloud provider and proceed to upload the file to the designated presignedURL.

### Collection **Editor**:

Tag: v5.4.8

Install: _npm i @project-sunbird/sunbird-collection-editor@_5.4.8

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.4.8](https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.4.8)

**NOTE:** Editor is expecting `provider` name inside config. for more details, [clike here](https://github.com/Sunbird-Knowlg/sunbird-collection-editor/blob/release-5.4.0/docs/CONFIGURATION.md)

### File Upload library:

Tag: v1.0.2

Install: _npm i_ @project-sunbird/sunbird-file-upload-library@1.0.2

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-file-upload-library/v/1.0.2](https://www.npmjs.com/package/@project-sunbird/sunbird-file-upload-library/v/1.0.2)



Please build and deploy using blow genric-editor and content-plugin tags for new CSP changes.

### Generic **Editor**:

Tag: release-5.2.1\_RC1

### Content Plugins:

Tag: release-5.2.1\_RC1

**NOTE:** Editor is expecting `provider` name inside config. for more details, [click here](https://github.com/Sunbird-Knowlg/sunbird-generic-editor/blob/release-5.2.1/README.md)

## <mark style="color:blue;">5.5.0</mark> (15-05-2023)

Discussion thread: [https://github.com/orgs/Sunbird-Knowlg/discussions/106](https://github.com/orgs/Sunbird-Knowlg/discussions/106)

Release timeline:

<table><thead><tr><th></th><th width="192.33333333333331">Start date</th><th>End date</th></tr></thead><tbody><tr><td>Planning phase</td><td>27-Feb, 2023</td><td>14-Mar, 2023</td></tr><tr><td>Sprint 1</td><td>15-Mar, 2023</td><td>5-Apr, 2023</td></tr><tr><td>Sprint 2</td><td>6-Apr, 2023</td><td>27-Apr, 2023</td></tr><tr><td>PPV</td><td>28-Apr, 2023</td><td>12-May, 2023</td></tr><tr><td>Prod</td><td>15-May, 2023</td><td></td></tr></tbody></table>

**5.5 total scope**: [Link](https://project-sunbird.atlassian.net/issues/?filter=12779)

### Document Release Version

<table><thead><tr><th width="229">Project</th><th>Release Version</th><th>Date</th></tr></thead><tbody><tr><td>Sunbird Knowlg</td><td>R5.5.0</td><td>15 May 2023</td></tr></tbody></table>

### **1. Summary of the changes**

This document contains information about the new features and enhancements planned to the Knowlg building block as part of release 5.5.0:

Enhancements: Click [here](https://project-sunbird.atlassian.net/issues/?filter=12779\&jql=project%20%3D%20KN%20AND%20issuetype%20in%20\(Documentation-Issue%2C%20Installation-Issues%2C%20Minor-Enhancement%2C%20RFC\)%20AND%20status%20in%20\(Done%2C%20%22In%20Validation%22\)%20AND%20labels%20in%20\(QA\_Not\_Required%2C%20QA\_Required%2C%20QA\_Required\_Regression\)%20AND%20Sprint%20in%20\(383%2C%20384\)%20ORDER%20BY%20key%20ASC%2C%20created%20DESC) to view the list.&#x20;

Bug Fixes - click [here](https://project-sunbird.atlassian.net/issues/?filter=12779\&jql=project%20%3D%20KN%20AND%20issuetype%20%3D%20Bug%20AND%20status%20in%20\(Done%2C%20%22In%20Validation%22\)%20AND%20Sprint%20in%20\(383%2C%20384\)%20ORDER%20BY%20key%20ASC%2C%20created%20DESC) to see the list of bugs fixed in this release.

**Test Scenarios: NA**

**Documentation issue, release 5.4.0:** [KN-866](https://project-sunbird.atlassian.net/browse/KN-866)

## Release Tags:

In this release, we have published NPM package for the below editor and players web components.    These NPM web components can help simplify web development by providing a standardized way to use editors and players in any UI framework, and which can save time and effort eventually.&#x20;

And also we have introduced a oneclick-installation feature using Terraform,allowing easy provisioning of all services,databases and jobs .The installation process has been optimized to reduce manual configuration steps and simplify setup for new users.

### Collection **Editor as Web** component:

Tag: 1.0.2

Install: `npm i @project-sunbird/sunbird-collection-editor-web-component`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor-web-component/v/1.0.2](https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor-web-component/v/1.0.2)

### Sunbird-pdf-player **as Web** component:

Tag: 1.0.1

Install: `npm i @project-sunbird/sunbird-pdf-player-web-component`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-pdf-player-web-component/v/1.0.1](https://www.npmjs.com/package/@project-sunbird/sunbird-pdf-player-web-component/v/1.0.1)

### Sunbird-video-player **as Web** component:

Tag: 1.0.1

Install: `npm i @project-sunbird/sunbird-video-player-web-component`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-video-player-web-component/v/1.0.1](https://www.npmjs.com/package/@project-sunbird/sunbird-video-player-web-component/v/1.0.1)

### Sunbird-epub-player **as Web** component:

Tag: 1.0.1

Install: `npm i @project-sunbird/sunbird-epub-player-web-component`

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-epub-player-web-component/v/1.0.1](https://www.npmjs.com/package/@project-sunbird/sunbird-epub-player-web-component/v/1.0.1)



**Note:** All the player angular libraries are updated with angular version 14 and published to npm with version 5.5.0.\
**From the next release, the web component will be the primary export that is recommended way to use the players.**

### Oneclick-installation:

#### Features:

* Terraform scripts have been implemented to automate the provisioning process, ensuring consistent and reliable deployments.
* Terraform variables and templates have been added, providing users with the ability to customize the deployment according to their specific requirements.

#### Installation and Upgrade Instructions:

Follow the README.md file from the below link for any specific configuration steps or considerations.\
[https://github.com/aimansharief/knowledge-platform/blob/knowlg-oneclick/knowlg-automation/README.md](https://github.com/aimansharief/knowledge-platform/blob/knowlg-oneclick/knowlg-automation/README.md)

