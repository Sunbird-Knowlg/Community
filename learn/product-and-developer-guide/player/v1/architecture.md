# Architecture

This is the classic version of the asset player. Using this player, users can play the following asset types.

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

| Content Type                                                                                                                                                                | MIME Type                                                                                                                                                                               |
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

### Content Launchers

Content player v1 is able to play the different types of contents using the configuration. You just need to provide the mimeType and plugin launchers in config. Its capable to load the content launchers according to the mimeType

#### Sample config to launch the ECML content

```
"contentLaunchers": [ // content laucher plugins for specific content mimetypes
    { // Plugin used for ECML content to launch, It is default plugin
        "mimeType": 'application/vnd.ekstep.html-archive',
        "id": 'org.sunbird.htmlrenderer',
        "ver": 1.0,
        "type": 'plugin'
    }
]
```

### White List Urls

Content player v1 will allows to play the external streaming url by adding the domain into the whiteListUrl config

**Sample config to add white listed urls**

```
whiteListUrl: [ 
    'self', 'https://.blob.core.windows.net/**',
    'https://ekstep-public-.s3-ap-south-1.amazonaws.com/**' 
]
```

Please refer to the [config section of README.md ](https://github.com/project-sunbird/sunbird-content-player#how-to-render-the-contents)file of the below [git repository](https://github.com/project-sunbird/sunbird-content-player)
