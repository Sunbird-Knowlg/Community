# How to setup

Please refer to the github readme document.

{% embed url="https://github.com/project-sunbird/sunbird-video-player/tree/release-4.5.0#readme" %}

### System Requirements <a href="#system-requirements" id="system-requirements"></a>

To install common player, ensure that your laptop or desktop has the following minimum system requirements:

* Operating System: Windows 7 and above, or 4.2 Mac OS X 10.0 and above/Linux
* RAM: >1.5GB
* CPU: 2 cores, >2 GHz

### Technical specifications

| Technology | Version | Details                                                 |
| ---------- | ------- | ------------------------------------------------------- |
| Node       | > 8.0   | To run project locally                                  |
| Cordova    | ^ 6.0   | Used expecially to communicate with mobile app(cordova) |
| HTML, JS   |         |                                                         |
| Sass       |         | Used for styles                                         |

### Configuration

The common player(content-player) is customizable and configurable before launching any type of content inside any environment (preview or device) it expects few configurations. Based on the configuration content will be rendered in the respective environment.

{% embed url="https://github.com/project-sunbird/sunbird-content-player/tree/release-4.4.0#how-to-render-the-contents" %}

### Internal Dependencies

#### [API Service](../../../../learn/product-and-developer-guide/content-service/)

The APIs service is used to read the content details using READ/GET API calls.

### External Dependencies

#### [Sunbird Telemetry](http://localhost:5000/o/-Mi9QwJlsfb7xuxTBc0J/s/-MkM7F4oILSpCJPO0YUu/)

Sunbird Telemetry is a specification to instrument all the key events. Using this specification reference applications & services will generate telemetry events.

#### [Sunbird inQuiry](http://localhost:5000/o/-Mi9QwJlsfb7xuxTBc0J/s/Wu4HIWGkb7dD4y0Kup4W/)

Sunbird inQuiry is used to play the questionnnaire while playing the content. This is especially used to play Interactive-video content.
