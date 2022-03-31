# Product & Developer Guide

## Feature specific components

on this page, we are detailing the list of [capabilities](../capabilities/) mapping to the components. How each capability can be achieved or integrated with the components.

* [Rich & Diverse Assets](./#rich-and-diverse-assets)
* [Organized Collections](./#organized-collections)
* [Asset Lifecycle Management](./#asset-lifecycle-management)
* [Powerful Discovery](./#powerful-discovery)
* [Phygital Discovery](./#phygital-discovery)
* [Observability](./#observability)

### Rich & Diverse Assets

| Component                           | Description                                        |
| ----------------------------------- | -------------------------------------------------- |
| [Content service](content-service/) | Allow users to define Rich & diverse asset schema. |

### Organized Collections

| Component                                                     | Description                                                                                                                                                               |
| ------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Content-service](content-service/)                           | Allow users to define Rich & diverse asset schema. This service also provides APIs to organize the assets as a collection.                                                |
| [Creation - Collection editor](editors/collection-editor-v2/) | As the name indicates, it is a tool used to create the collection or organized assets by the creators.                                                                    |
| <mark style="color:red;">Consumption - no player</mark>       | There is no player to consume or represent a collection at present. But the assets of the collection can be played using the [content-players V1](broken-reference) or V2 |

### Asset Lifecycle Management

###

| Component                                                | Description                                                                                                                                                                                                        |
| -------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Content service](content-service/)                      | <p>Content service API's helps to curate the assets created by creators(using asset creation tools - <a href="editors/">editors</a>).<br><br>The lifecycle to curate the content<br>Draft -> Review -> Publish</p> |
| [Creation - Interactive editor](editors/editor/)         | This tool helps user/creators to create the assets(ECML format).                                                                                                                                                   |
| [Creation - File upload editor](editors/generic-editor/) | This tool helps users/creators to create the assets by uploding the files format of Videos, PDFs, HTML, H5P & EPUBs.                                                                                               |
| [Consumption - Content player V1](broken-reference)      | This tool helps end-users to view/consume the contents created by the creators. This allow to play all the types of contents supported by sunbird platform.                                                        |
| Consumption - Content player's V2                        | This is enhaced or un-bundled version of content-player-V1. Unbundled to be smaller & specific format to play. So adopters can choose specific player as per their need.                                           |

### Powerful Discovery

| Component                                        | Description                                                                                                                                                                          |
| ------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Asset seach service](assets-search-service/)    | This is a service offered for ease of discovery of assets. This service will expose the API's only to read & filter the assets.                                                      |
| [Taxonomy service](taxonomy-and-tagging/)        | This service helps to define our own framework to organize the assets in a specific structure. It also helps to define the categories & tagging the assets specific to the category. |
| Dependency - [Content-service](content-service/) | The data in the content-service will be synced to the asset-search service for ease of discovery.                                                                                    |

### Phygital Discovery

| Component    | Description                                                                                                                                                                               |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Dial service | This service offers to generate the DIAL code & it can be linked to any asset. It also offers physical/digital discovery of the asset using a QR code image generated for each DIAL code. |

### Observability

| Component | Description                                                                                                                                                                                                        |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Telemetry | All the services & tools of the Sunbird Knowlg generate wide list of telemetry events. These telemetry events help to analyze the user actions. Users can build their own reports as per their needs/requirements. |
