# Collection Editor - V2

Please refer to the Github readme document.

{% embed url="https://github.com/Sunbird-Ed/sunbird-collection-editor" %}

### System Requirements <a href="#system-requirements" id="system-requirements"></a>

To install the editor, ensure that your laptop or desktop has the following minimum system requirements:

* Operating System: Windows 7 and above, or 4.2 Mac OS X 10.0 and above/Linux
* RAM: >2GB
* CPU: 2 cores, >2 GHz

### How to setup

Please refer to the [README](https://github.com/Sunbird-Ed/sunbird-collection-editor/tree/release-4.8.0#readme).md of the git repository

### Configuration

Before going to the next section, you should know about [object category definition](https://project-sunbird.atlassian.net/wiki/spaces/SingleSource/pages/2696183813/How+to+configure+forms+in+primaryCategory#Overview) is the key part of the configuration to load the editor.\
\
Following are the configuration for different types of collections.

1. [**Digital Textbook**](https://github.com/Sunbird-Ed/sunbird-collection-editor/blob/release-4.8.0/docs/Digital%20Textbook.json)
2. [**Course**](https://github.com/Sunbird-Ed/sunbird-collection-editor/blob/0b25c7d27aa559a20a58d3d204086b1f6e28141c/docs/Course.json)

For more information, please refer to the [config section of the README.md ](https://github.com/vaibhavbhuva/sunbird-collection-editor-1/blob/release-4.8.0/docs/CONFIGURATION.md)file of the [git repository](collection-editor-v2.md#git-repo)

{% embed url="https://github.com/Sunbird-Ed/sunbird-collection-editor/blob/d033e4d7495e63e2e0f05641491a51184dcc17fa/docs/CONFIGURATION.md" %}

### Dependencies

#### [Content Service](../../../learn/product-and-developer-guide/content-service/)

Content service APIs are being used to read the content details using READ/GET API calls.

#### [<mark style="color:blue;">Content Players</mark>](../players/)

The content players are used to playing the different types of content such as PDF, VIDEO, EPUB, etc...

<mark style="color:blue;">****</mark>[<mark style="color:blue;">**SunbirdEd Forms**</mark>](https://ed.sunbird.org/use/learn-more/specifications/sunbirded-forms)

Contains Form component powered by angular. This component expects a configuration and renders form according to the view.

#### [Sunbird Telemetry](https://telemetry.sunbird.org/)

Sunbird Telemetry is a specification to instrument all the key events. Using this specification reference applications & services will generate telemetry events.

### NPM Repository

{% embed url="https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor" %}
