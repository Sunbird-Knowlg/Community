# Release - 5.1.0

<mark style="color:blue;">**Hot-fix:  5.1.2**</mark>** (29-12-2022)**

<mark style="color:blue;">**Bugs:**</mark>

Course progress does not get updated correctly. [ KN-710](https://project-sunbird.atlassian.net/browse/KN-710)

| Sunbird-Video-Player | [**​v5.1.3**](https://www.npmjs.com/package/@project-sunbird/sunbird-video-player-v9/v/5.1.3) |  End event summary fix |
| -------------------- | --------------------------------------------------------------------------------------------- | ---------------------- |

### <mark style="color:blue;">**Hot-fix:  5.1.1**</mark>** (14-11-2022)**

<mark style="color:blue;">**Bugs:**</mark>

Null pointer exception thrown while publishing collection when 'objectType' attribute is missing from the children metadata in the collection Hierarchy. [KN-609](https://project-sunbird.atlassian.net/browse/KN-609)&#x20;

<table><thead><tr><th width="140">Component</th><th width="127">Service to be build</th><th width="358">Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Knowledge-platform-jobs</td><td>Build/KnowldgePlatform/Flinkjobs</td><td><a href="https://github.com/project-sunbird/knowledge-platform-jobs/releases/tag/release-5.1.1_RC1"><strong>release-5.1.1_RC1</strong></a></td><td>Build and depoy '<strong>content-publish</strong>' flink job</td></tr></tbody></table>

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


<table><thead><tr><th width="372.5">Component</th><th>Tag</th></tr></thead><tbody><tr><td>Sunbird-Collection-Editor</td><td><a href="https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.1.3"><strong>v5.1.3</strong></a></td></tr><tr><td>Sunbird-pdf-player</td><td><a href="https://www.npmjs.com/package/@project-sunbird/sunbird-pdf-player-v9/v/5.1.1"><strong>v5.1.1</strong></a></td></tr><tr><td>Sunbird-video-player</td><td><a href="https://www.npmjs.com/package/@project-sunbird/sunbird-video-player-v9/v/5.1.1"><strong>v5.1.1</strong></a></td></tr><tr><td>Sunbird-epub-player</td><td><a href="https://www.npmjs.com/package/@project-sunbird/sunbird-epub-player-v9/v/5.1.0"><strong>v5.1.0</strong></a></td></tr><tr><td>knowledge-platform</td><td><a href="https://github.com/project-sunbird/knowledge-platform/tree/release-5.1.0_RC1"><strong>release-5.1.0_RC1</strong></a></td></tr></tbody></table>

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
* PDF player:  Angular migration 9 to 12  #[KN-50](https://project-sunbird.atlassian.net/browse/KN-50) (Knowlg specific)
* Video player: Available as NG module for Angular based app manage it as dependency #[KN-7](https://project-sunbird.atlassian.net/browse/KN-7)

**Bug**

* Already Selected Programs / Verticals values are NOT getting displayed in the editor form when the user edit / send for review #[KN-238](https://project-sunbird.atlassian.net/browse/KN-238) (configuration update - Gourav)

**Deprecations -** [**Release 5.1.0**](../deprecations/release-5.1.0.md)&#x20;

#### Documentations

Content Publish API Postman collection: [https://github.com/project-sunbird/knowledge-platform/blob/release-5.1.0/content-api/api-tests/Collections/Publish%20API.postman\_collection.json](https://github.com/project-sunbird/knowledge-platform/blob/release-5.1.0/content-api/api-tests/Collections/Publish%20API.postman\_collection.json)

DIAL code Release API Postman collection: [https://github.com/project-sunbird/knowledge-platform/blob/release-5.1.0/content-api/api-tests/Collections/Release%20DIAL%20Code%20API.postman\_collection.json](https://github.com/project-sunbird/knowledge-platform/blob/release-5.1.0/content-api/api-tests/Collections/Release%20DIAL%20Code%20API.postman\_collection.json)

#### Configurations

Content Service application configuration:

For Bug [KN-238](https://project-sunbird.atlassian.net/browse/KN-238) The following fields needs to be updated for resource save form API.

**URL:**  /action/data/v1/form/read

**Request parameter** :-

`"type": "content",`

`subtype": "resource",`

`"action": "save"`

**Fields needs to be update**:

```
{
	"code": "verticals",
	"dataType": "text",
	"description": "Verticals",
	"editable": true,
	"index": 12,
	"inputType": "select",
	"label": "Verticals",
	"name": "Verticals",
	"placeholder": "Choose from the list of verticals",
	"renderingHints": {},
	"range": [
		"Nipun Bharat",
		"Adult Education",
		"Vocational Education",
		"CWSN",
		"Virtual Labs"
	],
	"required": false,
	"visible": true
}, {
	"code": "programs",
	"dataType": "text",
	"description": "Programs",
	"editable": true,
	"index": 12,
	"inputType": "select",
	"label": "Programs",
	"name": "Programs",
	"placeholder": "Choose from the list of programs",
	"renderingHints": {},
	"range": [
		"NISHTHA 2.0 (Secondary Level)",
		"NISHTHA 3.0 (Nipun Bharat)",
		"Chapter as a Course"
	],
	"required": false,
	"visible": true
}
```

<table><thead><tr><th width="258"></th><th></th><th>Description</th></tr></thead><tbody><tr><td>kafka.publish.request.topic</td><td> {{ env_name }}.publish.job.request</td><td>variable to redirect publish instructions to kafka topic of content publish flink job.</td></tr><tr><td></td><td></td><td></td></tr></tbody></table>
