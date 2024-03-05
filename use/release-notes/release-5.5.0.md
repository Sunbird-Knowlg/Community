# Release - 5.5.0

## <mark style="color:blue;">Hot-fix 5.5.1</mark> (08-08-2023)

**Enhancement:**

KN-902: CSP changes

As part of this hotfix, we have integrated a JavaScript file upload library. This library is designed to function with presignedURLs, file objects, and provider names. Depending on the provided values, the library will initiate interactions with the specified cloud provider and proceed to upload the file to the designated presignedURL.

### Release Tags:

### File Upload library:

Tag: v1.0.3

Install: _npm i_ @project-sunbird/sunbird-file-upload-library@1.0.3

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-file-upload-library/v/1.0.3](https://www.npmjs.com/package/@project-sunbird/sunbird-file-upload-library/v/1.0.3)

Please [click here](https://github.com/Sunbird-Knowlg/sunbird-file-upload-library#sunbirdfileuploadlib) to find more details about how to install and use of this library.

#### How to extend the _File upload library_ code to other Cloud Service Providers (CSPs):

The current iteration of this library has been developed with a primary focus on facilitating operations within the Azure cloud environment. Should you have the intention of expanding its capabilities to encompass additional Cloud Service Providers (CSPs) such as AWS, GCP, or Oracle, I highly recommend referring to the accompanying documentation. This document offers a comprehensive and detailed guide, providing step-by-step instructions and valuable insights on how to successfully extend the library's functionality to these other CSPs, ensuring seamless integration and compatibility.

{% embed url="https://github.com/Sunbird-Knowlg/sunbird-file-upload-library#how-to-extended-to-other-cloud-providers" %}

### Content Plugins:

Please build and deploy using blow content-plugin tags for new CSP changes.

Tag: release-5.2.1\_RC4

### Collection **Editor**:

Tag: v5.4.10

Install: _npm i @project-sunbird/sunbird-collection-editor@_5.4.10

URL: [https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.4.10](https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.4.10)

**NOTE:**&#x20;

1. &#x20;Editor is expecting `provider` name inside config. for more details, [clike here](https://github.com/Sunbird-Knowlg/sunbird-collection-editor/blob/release-5.4.0/docs/CONFIGURATION.md)
2. Please add File Upload library in `package.json`. Collection editor has a dependency on File Upload library.   &#x20;

### Sunbird Content **Editor**:

Please build and deploy using blow content-editor and content-plugin tags for new CSP changes.

### Content **Editor**:

Tag: release-5.2.1\_RC3

### Content Plugins:

Tag: release-5.2.1\_RC3

**NOTE:** Editor is expecting `provider` name inside config. For more details, [click here](https://github.com/Sunbird-Knowlg/sunbird-content-editor/blob/release-5.2.1/README.md)

### Sunbird Generic **Editor**:

Please build and deploy using blow genric-editor and content-plugin tags for new CSP changes.

### Generic **Editor**:

Tag: release-5.2.1\_RC2

### Content Plugins:

Tag: release-5.2.1\_RC2

**NOTE:** Editor is expecting `provider` name inside config. For more details, [click here](https://github.com/Sunbird-Knowlg/sunbird-generic-editor/blob/release-5.2.1/README.md)

### <mark style="color:blue;background-color:red;">Crucial Note Regarding CSP Changes:</mark>

At present, all editors are utilizing the default file upload library, which is designed to support the _Azure_ CSP provider. However, if an adopter wishes to extend this library to incorporate new CSPs such as _AWS or GCP_, the following modifications need to be made in both Editors and Plugins to ensure their functionality:

1. The editor anticipates the inclusion of the `provider` name within the configuration. Please ensure that the provider name is added to the configuration as specified in the readme.md file.
2. Update the package.json file with the new version of the **File Upload library**. It's important to note that the Collection editor relies on the File Upload library, so this update is crucial.
3. In order to incorporate the new version of the **File Upload library**, make the following changes to the specified plugins, and subsequently perform the build and deployment for both the Content editor and Generic editor. It's essential to replace the mentioned file at the following location: `editor/libs/sunbird-file-upload-library.js`, ensuring that the filename remains unchanged.
   * org.ekstep.assetbrowser-1.4
   * org.ekstep.uploadlargecontent-1.0
   * org.ekstep.uploadcontent-1.5

### API Services:

<table><thead><tr><th width="186.5">Component</th><th>Service to be Build</th><th width="100">Tag</th><th>Deploy Job</th><th>Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Knowledge-platform</td><td>Build/Core/Content</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-5.5.0_RC2">release-5.5.0_RC2</a></td><td>Deploy/Kubernetes/Content</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.5.0-knowlg_RC1">release-5.5.0-knowlg_RC1</a></td><td></td></tr><tr><td>Knowledge-platform-jobs</td><td>Build/KnowledgePlatform/FlinkJobs</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform-jobs/releases/tag/release-5.5.0_RC2">release-5.5.0_RC2</a></td><td>Deploy/KnowledgePlatform/FlinkJobs</td><td><a href="https://github.com/Sunbird-Knowlg/sunbird-learning-platform/tree/release-5.5.0_RC1">release-5.5.0_RC1</a></td><td>Jobs to be deployed:<br>1. <strong>asset-enrichment</strong><br>2.<strong>content-publish</strong><br>3. <strong>post-publish-processor</strong><br>4. <strong>qrcode-image-generator</strong><br>5. <strong>video-stream-generator</strong></td></tr></tbody></table>

### Jenkins **Configurations for CSP support:**

Set the variables _**CLOUD\_STORE\_GROUP\_ID**, **CLOUD\_STORE\_ARTIFACT\_ID**_ and _**CLOUD\_STORE\_VERSION**_ with appropriate values in Jenkins, either at the global level or for each individual service in the build job's configuration.\
For above-mentioned build jobs, configure like as we mentioned below.

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-12 at 10.23.57 AM.png" alt=""><figcaption></figcaption></figure>

#### Configure the following values:

| Name                       |                 |                                                                                                                        |
| -------------------------- | --------------- | ---------------------------------------------------------------------------------------------------------------------- |
| CLOUD\_STORE\_GROUP\_ID    | org.sunbird     | Set the cloud storage SDK group\_id ex: org.sunbird                                                                    |
| CLOUD\_STORE\_ARTIFACT\_ID | cloud-store-sdk | Set the cloud storage artefact id ex: cloud-store-sdk                                                                  |
| CLOUD\_STORE\_VERSION      | 1.4.6           | <p>Set the cloud storage version ex: 1.4.6<br><strong>NOTE</strong>: For OCI changes, we crated new version 1.4.7.</p> |

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

