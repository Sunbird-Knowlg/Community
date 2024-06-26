# Release - 5.7.0

## <mark style="color:blue;">Hot-fix 5.7.0</mark> (06-05-2024)

1. Not able to download QR-codes from published collection. [KN-1057](https://project-sunbird.atlassian.net/browse/KN-1057)

<table><thead><tr><th width="186.5">Component</th><th>Service to be Build</th><th width="100">Tag</th><th>Deploy Job</th><th>Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Knowledge-platform</td><td>Build/Core/Content</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-5.7.0_RC11">release-5.7.0_RC11</a></td><td>Deploy/Kubernetes/Content</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td></td></tr><tr><td>Knowledge-platform-jobs</td><td>Build/KnowledgePlatform/FlinkJobs</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform-jobs/tree/release-5.7.0_RC3">release-5.7.0_RC3</a></td><td>Deploy/KnowledgePlatform/FlinkJobs</td><td><a href="https://github.com/Sunbird-Knowlg/sunbird-learning-platform/commits/release-5.7.0_RC4">release-5.7.0_RC4</a></td><td>Jobs to be deployed:<br>1. <strong>post-publish-processor</strong> </td></tr></tbody></table>

## <mark style="color:blue;">Hot-fix 5.7.0</mark> (17-04-2024)

1. Removing inQuiry schemas from Knowlg repo ([IQ-750](https://project-sunbird.atlassian.net/browse/IQ-750))

### Release Tags:

<table><thead><tr><th width="186.5">Component</th><th>Service to be Build</th><th width="100">Tag</th><th>Deploy Job</th><th>Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Schema upload</td><td>NA</td><td>NA</td><td>Deploy/Kubernetes/UploadSchema</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-5.7.0_RC9">release-5.7.0_RC9</a></td><td></td></tr></tbody></table>

## <mark style="color:blue;">Hot-fix 5.7.0</mark> (20-03-2024)

Bug:

1. cloud storage SDK values pass in build time in search-service: [KN-1033](https://project-sunbird.atlassian.net/browse/KN-1033)
2. Question & Question Set objects image nodes issue &#x20;

### Release Tags:

### API Services:

<table><thead><tr><th width="183.5">Component</th><th>Service to be Build</th><th width="100">Tag</th><th>Deploy Job</th><th>Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Search-service</td><td>Build/Core/search</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/tree/release-5.7.0_RC8">release-5.7.0_RC8</a></td><td>Deploy/Kubernetes/Search</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td>Deploy Tag is given for reference only. Please do not use directly for deployment.</td></tr></tbody></table>

## <mark style="color:blue;">Hot-fix 5.7.0</mark> (07-03-2024)

**Bugs:**

1. CLONE - Imported Questionset is not playing in staging - [IQ-682](https://project-sunbird.atlassian.net/browse/IQ-682)

### Release Tags:

### API Services:

<table><thead><tr><th width="161.5">Component</th><th>Service to be Build</th><th width="100">Tag</th><th>Deploy Job</th><th width="126">Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Knowledge-platform-jobs</td><td>Build/KnowledgePlatform/FlinkJobs</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform-jobs/tree/release-5.7.0_RC2">release-5.7.0_RC2</a></td><td>Deploy/KnowledgePlatform/FlinkJobs</td><td><a href="https://github.com/Sunbird-Knowlg/sunbird-learning-platform/tree/release-5.5.0_RC1">release-5.5.0_RC1</a></td><td>Jobs to be deployed:<br>1. <strong>auto-creator-v2</strong></td></tr></tbody></table>

## <mark style="color:blue;">Hot-fix 5.7.0</mark> (27-02-2024)

**Bugs:**

1. CLONE - New framework category values are not getting saved while creating resource content - [KN-972](https://project-sunbird.atlassian.net/browse/KN-972)

### Release Tags:

### API Services:

<table><thead><tr><th width="183.5">Component</th><th>Service to be Build</th><th width="100">Tag</th><th>Deploy Job</th><th>Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Knowledge-platform-jobs</td><td>Build/KnowledgePlatform/FlinkJobs</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform-jobs/releases/tag/release-5.7.0_RC1">release-5.7.0_RC1</a></td><td>Deploy/KnowledgePlatform/FlinkJobs</td><td><a href="https://github.com/Sunbird-Knowlg/sunbird-learning-platform/tree/release-5.5.0_RC1">release-5.5.0_RC1</a></td><td>Jobs to be deployed:<br>1. <strong>content-publish</strong></td></tr></tbody></table>

### Sunbird Content **Editor**:

Please build and deploy using blow content-editor and content-plugin tags for above bug fix.

### Content **Editor**:

Tag: release-5.2.1\_RC4

### Content Plugins:

Tag: release-5.2.1\_RC4



## <mark style="color:blue;">Hot-fix 5.7.0</mark> (14-02-2024)

**Bugs:**

1. Portal: When content creator TN tried to save course, its throwing error "Something went wrong" -[KN-973](https://project-sunbird.atlassian.net/browse/KN-973)
2. \[Mobile]\[SSO]: After accepting the Global Consent pop up, the user navigates to the 'Edit Profile' screen, where the user is unable to select the fields. - [KN-974](https://project-sunbird.atlassian.net/browse/KN-974)

<table><thead><tr><th width="186.5">Component</th><th>Service to be Build</th><th width="100">Tag</th><th>Deploy Job</th><th>Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Knowledge-platform</td><td>Build/Core/Content</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-5.7.0_RC7">release-5.7.0_RC7</a></td><td>Deploy/Kubernetes/Content</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td></td></tr><tr><td></td><td>Build/Core/Taxonomy</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-5.7.0_RC7">release-5.7.0_RC7</a></td><td>Deploy/Kubernetes/Taxonomy</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td></td></tr></tbody></table>

#### **Configurations**:

As part of this release, we moved `retire`  API to content service. So, please update/add below kafka topic as a configuration.

```properties
kafka.topics.graph.event = "<ENV>.learning.graph.events"
```

Example:    `dev.knowlg.learning.graph.events`&#x20;

## <mark style="color:blue;">Hot-fix 5.7.0</mark> (12-02-2024)

**Bugs:**

1. Configured Category values are not coming for the Draft and Published Text Book - [KN-966](https://project-sunbird.atlassian.net/browse/KN-966)
2. \[SHALLOW COPY]: User is able to delete the Shallow copy created book where user should not be able to delete the Book. - [KN-970](https://project-sunbird.atlassian.net/browse/KN-970)



<table><thead><tr><th width="186.5">Component</th><th>Service to be Build</th><th width="100">Tag</th><th>Deploy Job</th><th>Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Knowledge-platform</td><td>Build/Core/Content</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-5.7.0_RC6">release-5.7.0_RC6</a></td><td>Deploy/Kubernetes/Content</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td></td></tr></tbody></table>



<mark style="color:blue;">5.7.0</mark> (13-09-2023)

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

<table><thead><tr><th width="186.5">Component</th><th>Service to be Build</th><th width="100">Tag</th><th>Deploy Job</th><th>Deployment Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Schema upload</td><td>NA</td><td>NA</td><td>Deploy/Kubernetes/UploadSchema</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-5.7.0_RC4">release-5.7.0_RC4</a></td><td></td></tr><tr><td>Knowledge-platform</td><td>Build/Core/Content</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-5.7.0_RC4">release-5.7.0_RC4</a></td><td>Deploy/Kubernetes/Content</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td></td></tr><tr><td></td><td>Build/Core/Taxonomy</td><td><a href="https://github.com/Sunbird-Knowlg/knowledge-platform/releases/tag/release-5.7.0_RC4">release-5.7.0_RC4</a></td><td>Deploy/Kubernetes/Taxonomy</td><td><a href="https://github.com/project-sunbird/sunbird-devops/releases/tag/release-5.6.0-knowlg_RC1">release-5.6.0-knowlg_RC1</a></td><td></td></tr></tbody></table>

## user-pii-data-updater:

We can utilize the Flink job created by the inquiry team to update user PII data in Knowlg, along with the necessary configuration changes. The details are provided below for your reference:

| Component | Service to be Build                             | Tag                                                                                            | Deploy Job                                                | Deployment Tag                                                                                 | Comment                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| --------- | ----------------------------------------------- | ---------------------------------------------------------------------------------------------- | --------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Flink Job | Build/job/KnowledgePlatform/job/InquiryFlinkJob | [release-7.0.0\_RC3](https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-7.0.0\_RC3) | Deploy/job/dev/job/KnowledgePlatform/job/InquiryFlinkJob/ | [release-7.0.0\_RC3](https://github.com/Sunbird-inQuiry/data-pipeline/tree/release-7.0.0\_RC3) | <p>A New Flink Job user-pii-data-updater is added. This job is used to cleanup Personal Identifiable Information (PII) of deleted user from Asset metadata. (e.g: Content/Collection metadata).<br>This job need pii configuration in each target object type configured. <br>Ref for PII Config Sample: <a href="https://github.com/Sunbird-inQuiry/inquiry-api-service/blob/1e57d014004f4c515c50fa8af6fb0d0de6c0cb2d/schemas/question/1.1/config.json#L74">https://github.com/Sunbird-inQuiry/inquiry-api-service/blob/1e57d014004f4c515c50fa8af6fb0d0de6c0cb2d/schemas/question/1.1/config.json#L74</a><br>Config File Reference For Above Job:<br><a href="https://github.com/Sunbird-inQuiry/data-pipeline/blob/2297fe1288654283f586d1802d458f4238c1e3f6/kubernetes/helm_charts/datapipeline_jobs/values.j2#L264">https://github.com/Sunbird-inQuiry/data-pipeline/blob/2297fe1288654283f586d1802d458f4238c1e3f6/kubernetes/helm_charts/datapipeline_jobs/values.j2#L264</a></p> |

## Variables Added For user-pii-data-updater Flink job:

| Variable Name                          | Description                                                                                                                                                                                                                                              | Default Value                                      |
| -------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| user\_pii\_updater\_kafka\_topic\_name | Input Kafka Topic Name                                                                                                                                                                                                                                   | \{{ env\_name \}}.delete.user                      |
| user\_pii\_updater\_group              | Group Name For The Flink Job                                                                                                                                                                                                                             | \{{ env\_name \}}-user-pii-updater-group           |
| user\_pii\_target\_object\_types       | <p>Target Object Type and Schema Version should be configured as value .<br>e.g: If you want to process 5 different objects for deleted user, then all 5 object types should be part of this configuration along with corresponding schema versions.</p> | '{ "Content": \["1.0"], "Collection": \["1.0"] }'  |
| user\_pii\_replacement\_value          | The value which need to be inserted for target pii fields.                                                                                                                                                                                               | "Deleted User"                                     |
| admin\_email\_notification\_enable     | This falg is used to enable/disable  email notification for admin                                                                                                                                                                                        | true                                               |
| user\_org\_service\_base\_url          | Base Url of userorg service for sending notification                                                                                                                                                                                                     | "http://\{{private\_ingressgateway\_ip\}}/userorg" |
| email\_notification\_subject           | Subject Line for Email Notification                                                                                                                                                                                                                      | "User Account Deletion Notification"               |
| email\_notification\_regards           | Value For Regards in Email Notification                                                                                                                                                                                                                  | "Team"                                             |

_**NOTE**: If any adopter is deploying Knowlg alone, they should extract this specific job from the inQuiry codebase and include the mentioned configurations. Alternatively, if they are using both Knowlg and inQuiry, they only need to update the configuration values for user\_pii\_target\_object\_types that encompass both Knowlg and inQuiry objects._

### Configuration/Environment variable changes:

In this release, we have deprecated the `Sunbird Learning service`, including an API that was previously served by this service. We have relocated this API to the `Sunbird content service`. Consequently, we need to update the Kong file to ensure that the upstream URL for the license validation API (`asset/v3/validate`) points to the `Content service` instead of the `Learning service`.

### Breaking changes (The existing features will break the if we don’t do the below actions):

During the upgrade to version 5.7.0, it is essential to ensure that the mentioned services and environments are properly updated. Previously, the APIs mentioned were part of the sunbird-learning-service, but now they have been moved to the content-service without altering the API contract. Additionally, changes have been made to ensure that these APIs are no longer served from the sunbird-learning-service.&#x20;

Therefore, it is crucial to verify that the necessary updates are implemented correctly for a smooth transition to version 5.7.0.

**List of APIs moved to Content Service:**

<table><thead><tr><th width="89">S.No</th><th>API</th></tr></thead><tbody><tr><td>1</td><td>/asset/v3/validate</td></tr></tbody></table>
