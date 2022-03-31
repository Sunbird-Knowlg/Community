---
description: >-
  Content service is a micro-service which provides APIs to manage the lifecycle
  and workflows of creation and consumption of content object.
---

# Features

Content service is a micro-service which provides APIs to manage the lifecycle and workflows of creation and consumption of content object.

### Features:

1.  **Offline Play:** Enables offline consumption via generation of ECAR files in the packaging stage of the publish lifecycle. Contents can be download from _**downloadUrl**_. Two _**variants**_ of the ECAR are available for each content. i.e. FULL and SPINE. ECAR can be downloaded and extracted in client (mobile and desktop) to play offline.

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
2. **Publish control:** Content publishing can be done in two ways: Public (status: Live) and Private (status: Unlisted). When the content status is _**Live**,_ content is available for consumption publicly. When the content status is _**Unlisted**,_ content can be accessed only by direct content link (deep link).
3. **Video Streaming: **_**streamingUrl**_ attribute captures the link of video streaming. For more details, refer to the job [here](../knowlg-jobs.md).&#x20;
4. **Source file storage:** Source file of the uploaded content is stored in cloud. Source file URL is captured in _**artifactUrl**_ attribute.
5.  **Content lifecycle management:** Content can have the following status throughout the lifecycle:

    ```
    Create (status: Draft)
    Update (status: Draft)
    Review (status: Review)
    Reject (status: Draft)
    Publish (status: Live/Unlisted)
    Retired (status: Retired)
    Failed (status: Failed)
    ```

    Content object having the status Retired can't be discovered for consumption/adoption.
6. **Player compatibility:** Player compatibility level of a content is stored in _**compatibilityLevel**_ attribute. Based on the value, players can decide to play the content or show the incompatibility message.
7. **Version control:** Whenever publish the content _**pkgVersion**_ bumpup by +1. Platform always keep the latest version of the content in DB.
8. **Extracting ECAR:** Extracting ECAR based on contentEncoding and contentDisposition.
9. **Controlling access using visibility:** Public, private and parent content (visibility: Default, Private, Parent) can be created. visibility: Parent, which can be discoverable only within a specific Collection.
10. **Targeted audience:** You can define the target audience e.g. Student, Teacher, Administrator, Parent.
11. trackable: User can track their progress by enabling the trackable. Also he can create the batch and join the batch by enabling this at the time of creation.&#x20;
12. **Auto batch creation:** Default value is _No._
13. **Organising content based on channel:** channel/createdFor
14. framework:&#x20;
