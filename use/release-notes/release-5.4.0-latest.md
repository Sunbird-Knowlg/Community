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

**5.4 scope** : Click [here](https://project-sunbird.atlassian.net/issues/?filter=12759\&jql=project%20%3D%20KN%20AND%20issuetype%20in%20\(standardIssueTypes\(\)%2C%20Bug%2C%20Documentation-Issue%2C%20Installation-Issues%2C%20Minor-Enhancement%2C%20RFC\)%20AND%20Sprint%20in%20\(351%2C%20352\)%20ORDER%20BY%20key%20ASC%2C%20created%20DESC) for 5.4 scope

KN-802: SYNC Tool configuration update

| **Variable**                     | **Values**                                                  | **description**                                                                                                                                         |
| -------------------------------- | ----------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `replace_dest_string`            | true/false                                                  | Used to specify if the Relative path string replace is to be enabled                                                                                    |
| `replace_src_string_DIAL_store`  | `DIAL_STORAGE_BASE_PATH`                                    | Currently configured relative path variable name to be stored in database instead of BLOB absolute URL                                                  |
| `replace_dest_string_DIAL_store` | Ex: `https://sunbirddevbbpublic.blob.core.windows.net/dial` | BLOB URL and container combination value that is used to replace ‘`DIAL_STORAGE_BASE_PATH`’ relative path variable while syncing image ‘url’ data to ES |

### **1. Summary of the changes**

This document contains information about the new features and enhancements planned to the Knowlg building block as part of release 5.4.0:

Enhancements: Click [here](https://project-sunbird.atlassian.net/issues/?filter=12759\&jql=project%20%3D%20KN%20AND%20issuetype%20in%20\(Documentation-Issue%2C%20Minor-Enhancement%2C%20RFC\)%20AND%20status%20in%20\(Done%2C%20%22In%20Validation%22\)%20AND%20labels%20in%20\(QA\_Not\_Required%2C%20QA\_Required%2C%20QA\_Required\_Regression%2C%20Regression\)%20AND%20Sprint%20in%20\(351%2C%20352\)%20ORDER%20BY%20key%20ASC%2C%20created%20DESC) to view the list.&#x20;

Bug Fixes - click [here](https://project-sunbird.atlassian.net/issues/?filter=12759\&jql=project%20%3D%20KN%20AND%20issuetype%20%3D%20Bug%20AND%20status%20in%20\(Done%2C%20%22In%20Validation%22\)%20AND%20labels%20in%20\(QA\_Not\_Required%2C%20QA\_Required%2C%20QA\_Required\_Regression%2C%20Regression\)%20AND%20Sprint%20in%20\(351%2C%20352\)%20ORDER%20BY%20key%20ASC%2C%20created%20DESC) to see the list of bugs fixed in this release.

**Test Scenarios:**[ **Link**](https://docs.google.com/spreadsheets/d/1YOe4QB0gqA53gFTzsP-6MtQI02EaKiUzn1SPihZPaeM/edit#gid=117864265)****

**Documentation issue, release 5.4.0:** [KN-839](https://project-sunbird.atlassian.net/browse/KN-839)
