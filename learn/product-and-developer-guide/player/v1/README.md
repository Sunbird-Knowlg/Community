---
description: >-
  Content player v1 has the capability to play/render a variety of content in
  both mobile and web form factors.
---

# V1

This is the classic version of the player. The following formats are supported by this player:

* ECML
* PDF
* EPUB
* HTML and H5P
* Video (MP4, WebM)
* Youtube

![](<../../../../.gitbook/assets/Screenshot from 2021-11-24 15-00-25.png>)

### MIME Type

**What is mime-type**

MIME Types defines the what type of the content it is. According to the mimeType you can load the specific content launcher and play the different types of contents

#### Sample config to load the MIME types

```
mimetypes: [
    "application/vnd.ekstep.ecml-archive",
    "application/vnd.ekstep.html-archive",
    "application/vnd.ekstep.h5p-archive",
    "application/epub",
    "video/mp4",
    "application/pdf",
    "video/x-youtube",
    "video/webm",
    "audio/mp3"
]
```

**Supported MIME Types are:**

| Content Format                                                                                                                                                              | MIME Type                                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [ECML](players/ecml-player-v1.md)                                                                                                                                           | [application/vnd.ekstep.ecml-archive](players/ecml-player-v1.md)                                                                                                                        |
| [HTML](players/html-h5p-player-v1.md)                                                                                                                                       | [application/vnd.ekstep.html-archive](players/html-h5p-player-v1.md)                                                                                                                    |
| [PDF](https://app.gitbook.com/o/-Mi9QwJlsfb7xuxTBc0J/s/aanfWbeVT74C5lXDPde3/\~/changes/uO8tokGf3RxCXA1P4fnr/learn/product-and-developer-guide/content-player-v1/pdf-player) | [application/pdf](https://app.gitbook.com/o/-Mi9QwJlsfb7xuxTBc0J/s/aanfWbeVT74C5lXDPde3/\~/changes/uO8tokGf3RxCXA1P4fnr/learn/product-and-developer-guide/content-player-v1/pdf-player) |
| [Epub](players/epub-player-v1.md)                                                                                                                                           | [application/epub](players/epub-player-v1.md)                                                                                                                                           |
| [H5P](players/html-h5p-player-v1.md)                                                                                                                                        | [application/vnd.ekstep.h5p-archive](players/html-h5p-player-v1.md)                                                                                                                     |
| YOUTUBE                                                                                                                                                                     | video/x-youtube                                                                                                                                                                         |
| WEBM                                                                                                                                                                        | video/Webm                                                                                                                                                                              |
| MP4                                                                                                                                                                         | video/mp4                                                                                                                                                                               |
| EXTERNAL CONTENT                                                                                                                                                            | text/x-url                                                                                                                                                                              |

