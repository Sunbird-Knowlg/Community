# Release - 5.7.0 (latest)

## <mark style="color:blue;">5.7.0</mark> (13-09-2023)

Discussion thread: [https://github.com/orgs/Sunbird-Knowlg/discussions/146](https://github.com/orgs/Sunbird-Knowlg/discussions/146)

Release timeline:

<table><thead><tr><th></th><th width="192.33333333333331">Start date</th><th>End date</th></tr></thead><tbody><tr><td>Planning phase</td><td>3-Jul, 2023</td><td>14-Jul, 2023</td></tr><tr><td>Sprint 1</td><td>17-Jul, 2023</td><td>4-Aug, 2023</td></tr><tr><td>Sprint 2</td><td>7-Aug, 2023</td><td>25-Aug, 2023</td></tr><tr><td>PPV</td><td>28-Aug, 2023</td><td>8-Sept, 2023</td></tr><tr><td>Prod</td><td>13-Sept, 2023 (<mark style="color:red;">delayed 2 days</mark>)</td><td></td></tr></tbody></table>

**5.7.0 total scope**: [Link](https://project-sunbird.atlassian.net/issues/?filter=12824)

### Document Release Version

<table><thead><tr><th width="229">Project</th><th>Release Version</th><th>Date</th></tr></thead><tbody><tr><td>Sunbird Knowlg</td><td>R5.7.0</td><td>13-Sept, 2023 </td></tr></tbody></table>

### **1. Summary of the changes**

This document contains information about the new features and enhancements planned to the Knowlg building block as part of release 5.7.0:

Enhancements: Click [here](https://project-sunbird.atlassian.net/issues/?filter=12828\&jql=project%20%3D%20KN%20AND%20issuetype%20in%20\(Documentation-Issue%2C%20Installation-Issues%2C%20Minor-Enhancement%2C%20RFC\)%20AND%20status%20in%20\(Done%2C%20DONE%2C%20%22In%20Validation%22\)%20AND%20labels%20in%20\(QA\_Not\_Required%2C%20QA\_Required%2C%20QA\_Required\_Regression\)%20AND%20Sprint%20in%20\(459%2C%20460\)%20ORDER%20BY%20cf%5B10010%5D%20ASC%2C%20created%20DESC) to view the list. (CSP changes was Hotfix taken as part of previous release, ticket updated for this release)

Bug Fixes - click [here](https://project-sunbird.atlassian.net/issues/?filter=12828\&jql=project%20%3D%20KN%20AND%20issuetype%20%3D%20Bug%20AND%20status%20in%20\(Done%2C%20%22In%20Validation%22\)%20AND%20Sprint%20in%20\(459%2C%20460\)%20ORDER%20BY%20cf%5B10010%5D%20ASC%2C%20created%20DESC) to see the list of bugs fixed in this release.

**Test Scenarios: NA**

### Following are the Planned Tickets of R 5.7.0

#### New Features:

None

#### Enhancements / Technical tasks::

<table><thead><tr><th width="83.33333333333331">S.no</th><th width="124">JIRA ID</th><th>Description</th></tr></thead><tbody><tr><td>1</td><td><a href="https://project-sunbird.atlassian.net/browse/KN-502">KN-502</a></td><td>Learning service deprecation</td></tr><tr><td>2</td><td><a href="https://project-sunbird.atlassian.net/browse/KN-920">KN-920</a></td><td>Knowlg: CSP changes</td></tr><tr><td>3</td><td><a href="https://project-sunbird.atlassian.net/browse/KN-906">KN-906</a></td><td>Refresh Lock API refactoring</td></tr><tr><td>4</td><td><a href="https://project-sunbird.atlassian.net/browse/KN-907">KN-907</a></td><td>Retire Lock API refactoring</td></tr><tr><td>5</td><td><a href="https://project-sunbird.atlassian.net/browse/KN-908">KN-908</a></td><td>List Lock API refactoring</td></tr><tr><td>6</td><td><a href="https://project-sunbird.atlassian.net/browse/KN-880">KN-880</a></td><td>Create Lock API refactoring</td></tr></tbody></table>

### Release Tags:

#### Upgrade Knowlg From 5.6.0 to 5.7.0

### API Services:

<table><thead><tr><th width="186.5">Component</th><th>Service to be Build</th><th width="100">Tag</th><th>Deploy Job</th><th>Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Schema upload</td><td>NA</td><td>NA</td><td>Deploy/Kubernetes/UploadSchema</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/tree/release-5.7.0_RC3">release-5.7.0_RC3</a></td><td></td></tr><tr><td>Knowledge-platform</td><td>Build/Core/Content</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-5.7.0_RC2">release-5.7.0_RC2</a></td><td>Deploy/Kubernetes/Content</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td></td></tr></tbody></table>

### Configuration/Environment variable changes:

In this release, we have deprecated the `Sunbird Learning service`, including an API that was previously served by this service. We have relocated this API to the `Sunbird content service`. Consequently, we need to update the Kong file to ensure that the upstream URL for the license validation API (`asset/v3/validate`) points to the `Content service` instead of the `Learning service`.

### Breaking changes (The existing features will break the if we don’t do the below actions):

During the upgrade to version 5.7.0, it is essential to ensure that the mentioned services and environments are properly updated. Previously, the APIs mentioned were part of the sunbird-learning-service, but now they have been moved to the content-service without altering the API contract. Additionally, changes have been made to ensure that these APIs are no longer served from the sunbird-learning-service.&#x20;

Therefore, it is crucial to verify that the necessary updates are implemented correctly for a smooth transition to version 5.7.0.

**List of APIs moved to Content Service:**

<table><thead><tr><th width="89">S.No</th><th>API</th></tr></thead><tbody><tr><td>1</td><td>/asset/v3/validate</td></tr></tbody></table>
