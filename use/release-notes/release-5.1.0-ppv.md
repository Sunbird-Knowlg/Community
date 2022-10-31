# Release-5.1.0 (PPV)



### <mark style="color:blue;">5.1.0</mark> (01-08-2022)

Discussion thread: [https://github.com/Sunbird-Knowlg/Community/discussions/42](https://github.com/Sunbird-Knowlg/Community/discussions/42)

|                | Start date  | End date    |
| -------------- | ----------- | ----------- |
| Planning phase | 18 Jul 2022 | 28 Jul 2022 |
| Sprint 1       | 01 Aug 2022 | 19 Aug 2022 |
| Sprint 2       | 22 Aug 2022 | 09 Sep 2022 |
| PPV            | 12 Sep 2022 | 23 Sep 2022 |
| Prod           | 18 Oct 2022 |             |

\


| Component                 | Tag                                                                                                    |
| ------------------------- | ------------------------------------------------------------------------------------------------------ |
| Sunbird-Collection-Editor | ****[**v5.1.3**](https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.1.3)**** |

#### **Features**

* Please fine the Knowlg BB sign-off [here](https://docs.google.com/spreadsheets/d/1mmw6t0DRQs4KUqhpmNT4iLANSdhNVCU42ZLp2B6\_1QM/edit#gid=0).
* Content Publish API LP to KP [#](https://project-sunbird.atlassian.net/browse/SB-30118)[KN-9](https://project-sunbird.atlassian.net/browse/KN-9)&#x20;

&#x20;APIs refactored from learning-service to content-service: "\{{host\}}/api/content/v2/publish/\{{content\_id\}}" & "\{{host\}}/api/collection/v1/publish/\{{collection_\__id\}}"&#x20;

Note: Existing endPoint '{host\}}/api/content/v1/publish/\{{content\_id\}}' will be deprecated soon

* Content - DIAL Release API - LP to KP #[KN-257](https://project-sunbird.atlassian.net/browse/KN-257)&#x20;

APIs refactored from learning-service to content-service: "\{{host\}}/api/content/v2/dialcode/release/\{{content\_id\}}" & "\{{host\}}/api/collection/v1/dialcode/release/\{{collection_\__id\}}" &#x20;

Note: Existing endPoint '{host\}}/api/dial/v1/release/\{{content\_id\}}' will be deprecated soon.

* Collection editor: Angular migration 9 to 12 #[KN-26](https://project-sunbird.atlassian.net/browse/KN-26) (Knowlg specific)
* Integrate cloud-store-sdk for google cloud #[KN-231](https://project-sunbird.atlassian.net/browse/KN-231) (Dev sign off, knowlg specific) (update documentation - Anil or Kumar Gaurav)
* Implementation - Knowlg player app for PDF, Video and Epub player #[KN-239](https://project-sunbird.atlassian.net/browse/KN-239) (Knowlg BB portal specific)
*   **Deprecation Warning:** From release-5.1.0, [<mark style="color:red;">@project-sunbird/sunbird-collection-editor-v9</mark>](https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor-v9) <mark style="color:red;">deprecated.</mark> \ <mark style="color:red;"></mark>Please use [@project-sunbird/sunbird-collection-editor](https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.1.3) for the latest version with angular 12\
    \
    **Install:** _`npm i @project-sunbird/sunbird-collection-editor@5.1.3`_

    **URL:** [https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.1.3](https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.1.3)

**Bug**

* Already Selected Programs / Verticals values are NOT getting displayed in the editor form when the user edit / send for review #[KN-238](https://project-sunbird.atlassian.net/browse/KN-238) (configuration update - Gourav)

#### Documentations

Content Publish API Postman collection: [https://github.com/project-sunbird/knowledge-platform/blob/release-5.1.0/content-api/api-tests/Collections/Publish%20API.postman\_collection.json](https://github.com/project-sunbird/knowledge-platform/blob/release-5.1.0/content-api/api-tests/Collections/Publish%20API.postman\_collection.json)

DIAL code Release API Postman collection: [https://github.com/project-sunbird/knowledge-platform/blob/release-5.1.0/content-api/api-tests/Collections/Release%20DIAL%20Code%20API.postman\_collection.json](https://github.com/project-sunbird/knowledge-platform/blob/release-5.1.0/content-api/api-tests/Collections/Release%20DIAL%20Code%20API.postman\_collection.json)

#### Configurations

Content Service application.conf:

|                             |                                        | Description                                                                            |
| --------------------------- | -------------------------------------- | -------------------------------------------------------------------------------------- |
| kafka.publish.request.topic |  \{{ env\_name \}}.publish.job.request | variable to redirect publish instructions to kafka topic of content publish flink job. |
|                             |                                        |                                                                                        |