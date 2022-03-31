# Product & Developer Guide

## Feature specific components

In this page, we map the [capabilities](../capabilities/) offered by Knowlg to the various components in the Sunbird Knowlg building block. This view provides you understanding what components are needed to enable a specific capability.&#x20;

* [Rich & Diverse Assets](./#rich-and-diverse-assets)
* [Organized Collections](./#organized-collections)
* [Asset Lifecycle Management](./#asset-lifecycle-management)
* [Powerful Discovery](./#powerful-discovery)
* [Phygital Discovery](./#phygital-discovery)
* [Observability](./#observability)

### Rich & Diverse Assets

| Component                           | Description                           |
| ----------------------------------- | ------------------------------------- |
| [Content service](content-service/) | Enables users to define asset schema. |

### Organized Collections

| Component                                                     | Description                                                                                                                                              |
| ------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Content-service](content-service/)                           | Enables users to define asset schema and consists of APIs to organize the assets as a collection.                                                        |
| [Creation - Collection editor](editors/collection-editor-v2/) | It is a pluggable tool used to create the collections.                                                                                                   |
| <mark style="color:red;">Consumption - no player</mark>       | There is no separate collection player however the assets linked to the collection can be played using the [content-players V1](broken-reference) or V2. |

### Asset Lifecycle Management

###

| Component                                                | Description                                                                                                                                                                                                        |
| -------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Content service](content-service/)                      | <p>Content service API's helps to curate the assets created by creators(using asset creation tools - <a href="editors/">editors</a>).<br><br>The lifecycle to curate the content<br>Draft -> Review -> Publish</p> |
| [Creation - Interactive editor](editors/editor/)         | This tool helps user/creators to create the assets(ECML format).                                                                                                                                                   |
| [Creation - File upload editor](editors/generic-editor/) | Upload editor tool allows creators to create assets by a simple upload. Supports Video, PDF, HTML, H5P & EPUB format.                                                                                              |
| [Consumption - Content player V1](broken-reference)      | Content player V1 enables users to consume content. This player is compatible with all asset format supported by sunbird platform.                                                                                 |
| Consumption - Content player's V2                        | This is enhanced or un-bundled version of content-player-V1. Unbundled to be lighter & specific to the format. For ex., video player to play video content, epub player to play epub content etc.                  |

### Powerful Discovery

| Component                                        | Description                                                                                                                                                       |
| ------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Asset seach service](assets-search-service/)    | This is a service offered for ease of discovery of assets. This service will expose the API's only to read & filter the assets.                                   |
| [Taxonomy service](taxonomy-and-tagging/)        | This service helps to define your own framework to organize the assets in a specific structure. It also enables you to define the categories & tagging of assets. |
| Dependency - [Content-service](content-service/) | The data in the content-service will be synced to the asset-search service for ease of discovery.                                                                 |

### Phygital Discovery

| Component    | Description                                                                                                                                                                               |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Dial service | This service offers to generate the DIAL code & it can be linked to any asset. It also offers physical/digital discovery of the asset using a QR code image generated for each DIAL code. |

### Observability

| Component | Description                                                                                                                                                                                                        |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Telemetry | All the services & tools of the Sunbird Knowlg generate wide list of telemetry events. These telemetry events help to analyze the user actions. Users can build their own reports as per their needs/requirements. |
