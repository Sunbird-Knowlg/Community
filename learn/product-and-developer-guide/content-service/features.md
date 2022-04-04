---
description: >-
  Content service is a micro-service which provides APIs to manage the lifecycle
  and workflows of creation and consumption of content.
---

# Features

Content service is a micro-service which provides APIs to manage the lifecycle and workflows of creation and consumption of content.

### **Offline Play**

Enables offline consumption via generation of ECAR files in the packaging stage of the publish lifecycle. Contents can be download from _**downloadUrl**_. Two _**variants**_ of the ECAR are available for each content. i.e. FULL and SPINE. ECAR can be downloaded and extracted in client (mobile and desktop) to play offline.

### **Publish control**

Content publishing can be done in two ways: Public (status: Live) and Private (status: Unlisted). When the content status is _**Live**,_ content is available for consumption publicly. When the content status is _**Unlisted**,_ content can be accessed only by direct content link (deep link).

### ECAR generation

ECAR is an archive file which contains metadata and artifact related to content. After generating the ECAR file, it's uploaded to the cloud and tagged the _**downloadUrl**_ with the cloud path. ECAR generates the different variants - FULL, SPINE and ONLINE. All the variants URL are tagged in _**variants**_ attribute.

* FULL - It contains metadata and all the artifacts.
* SPINE - It contains metadata and app icons.
* ONLINE - It contains only metadata.

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

Content having the status Retired can't be discovered for consumption/adoption.\


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

Contents created within an organization tagged with _channel_. Content created by any organization can be consumed by other organization, this can be managed by _createdFor_ attribute.&#x20;

### Organizing content by taxonomy

Contents can be tagged with framework and its category terms to categories it based on framework and enhance the search capabilities. To broaden the search criteria, it would be better to tag content with multiple framework and their category terms. With this, content can be available for different frameworks for consumption.

Contents created within an organisation framework can also be available for other frameworks. Contents can be tagged with multiple frameworks and their respective categories, so that while searching with different frameworks (framework within which content is not created), contents can be available.

More detail can be found [here](https://project-sunbird.atlassian.net/wiki/spaces/User/pages/1878884361/Tag+Contents+with+Multiple+Frameworks).

### List of supported content mimeType

```
"application/pdf",
"application/vnd.ekstep.ecml-archive",  
"application/vnd.ekstep.html-archive",  
"application/vnd.android.package-archive",  
"application/vnd.ekstep.content-archive", 
"application/epub", 
"application/msword",   
"application/vnd.ekstep.h5p-archive", 
"video/webm", 
"video/mp4"
```

### Copy content

Platform supports deep and shallow copy. _**copyType**_ attribute hold the value of copy type. When you copy a content, it is tagged with _**origin**_ (URI of the source object) and _**originData**_ (basic metadata of the source object).

* **Shallow copy:**\
  A collection can also be reused (adopted) by creating a shallow copy of the collection. When a shallow copy is created, the hierarchy of the original collection is not modifiable in the shallow copy. Only the metadata such as name, description, icon etc. of the shallow copy is modifiable. Any change to the hierarchy of the original collection automatically reflects in the shallow copy.
* **Deep copy:**\
  Deep  copy makes the duplicate copy of the content. After that user can modify any metadata of the content.

### [DIAL code generation](https://project-sunbird.atlassian.net/wiki/spaces/SingleSource/pages/1966080027/DIAL+Code+generation)

A DIAL code is a unique code associated to a QR image. A DIAL code can be linked to any learning asset. However, sourcing solution currently enables generating DIAL codes for a collection and link them to the root as well as any node in its hierarchy.

DIAL codes can be generated and linked to a draft version of a collection.

### Concurrent Modification

_versionKey_ attribute is used for concurrent modification. When ever update happened, content tagged wit the updated version key.

### License

Default licenses are available in systems listed below

```
"CC BY-NC-SA 4.0",
"CC BY-NC 4.0",
"CC BY-SA 4.0",
"CC BY 4.0",
"CC BY-ND 4.0",
"Standard YouTube License"
```
