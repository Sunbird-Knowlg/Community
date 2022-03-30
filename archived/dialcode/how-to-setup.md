# How to setup

Presently it is tightly integrated into Portal & Mobile code(consumption or usability).

#### Portal Dialcode Module:

{% embed url="https://github.com/Sunbird-Ed/SunbirdEd-portal/tree/release-4.5.0/src/app/client/src/app/modules/dial-code-search" %}

#### Mobile Dialcode Module:

Cordova plugin is to scan the dialcode.

{% embed url="https://github.com/project-sunbird/cordova-plugin-qr-scanner" %}

After successful scanning of the dialcode, it will redirect to the screen to show the dialcode linked contents.

{% embed url="https://github.com/Sunbird-Ed/SunbirdEd-mobile-app/tree/master/src/app/qrcoderesult" %}

#### Dialcode service

Dialcode service exposes APIs to get the contents linked to dialcode.

{% embed url="https://github.com/project-sunbird/sunbird-dial-service" %}

Internal Dependencies
