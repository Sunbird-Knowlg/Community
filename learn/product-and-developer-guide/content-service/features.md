---
description: >-
  Content service is a micro-service which provides APIs to manage the lifecycle
  and workflows of creation and consumption of content object.
---

# Features

Content service is a micro-service which provides APIs to manage the lifecycle and workflows of creation and consumption of content object.

### **Offline Play**

Enables offline consumption via generation of ECAR files in the packaging stage of the publish lifecycle. Contents can be download from _**downloadUrl**_. Two _**variants**_ of the ECAR are available for each content. i.e. FULL and SPINE. ECAR can be downloaded and extracted in client (mobile and desktop) to play offline.

```
"downloadUrl": "<full ecar url>",
"variants": {
    "full": {
        "ecarUrl": "<full ecar url>",
        "size": "<size in byte>"
    },
    "spine": {
        "ecarUrl": "<spine ecar url>",
        "size": "<size in byte>"
    },
    "online": {
        "ecarUrl": "<online ecar url>",
        "size": "<size in byte>"
    }
}
```

### **Publish control**

Content publishing can be done in two ways: Public (status: Live) and Private (status: Unlisted). When the content status is _**Live**,_ content is available for consumption publicly. When the content status is _**Unlisted**,_ content can be accessed only by direct content link (deep link).

### ECAR generation

TBD

### **Video Streaming**

_**streamingUrl**_ attribute captures the link of video streaming. For more details, refer to the job [here](../knowlg-jobs.md).&#x20;

### **Source file storage**

Source file of the uploaded content is stored in cloud. Source file URL is captured in _**artifactUrl**_ attribute.

### **Content lifecycle management**

Content can have the following status throughout the lifecycle:

```
Create (status: Draft)
Update (status: Draft)
Review (status: Review)
Reject (status: Draft)
Publish (status: Live/Unlisted)
Retired (status: Retired)
Failed (status: Failed)
```

Content object having the status Retired can't be discovered for consumption/adoption.\


![](<../../../.gitbook/assets/sunbird-knowlg-status flow diagram.png>)

### **Player compatibility**

Player compatibility level of a content is stored in _**compatibilityLevel**_ attribute. Based on the value, players can decide to play the content or show the incompatibility message.

### **Version control**

Whenever publish the content _**pkgVersion**_ bumpup by +1. Platform always maintains the latest version (Live and Draft) of the content. Old version of the content won't be available.

### **Extracting ECAR**

Extracting ECAR based on contentEncoding and contentDisposition.\


| contentEncoding | contentDisposition | Behaviour                                            |
| :-------------: | :----------------: | ---------------------------------------------------- |
|       gzip      |       inline       | Content artifact with zip file. e.g. ecml, html, h5p |
|     identity    |       inline       | Content artifact without zip file. e.g. pdf, webm    |
|     identity    |       online       | Content without artifact                             |
|     identity    |     online-only    | mp4                                                  |

### **Controlling access using visibility**

Public, private and parent content (visibility: Default, Private, Parent) can be created. visibility: Parent, which can be discoverable only within a specific Collection.

### **Targeted audience**

You can define the target audience e.g. Student, Teacher, Administrator, Parent.

### **Organizing content based on channel**

TBD channel/createdFor

### Organizing content by taxonomy

TBD framework

### List of supported content mimeType

TBD

### Copy content

* **Shallow copy:**\
  TBD
* **Deep copy:**\
  TBD

### DIAL code
