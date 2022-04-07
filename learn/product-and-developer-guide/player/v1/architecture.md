# Architecture

![Content player v1 architecture](<../../../../.gitbook/assets/contentv1fea-Epub player 2.drawio.png>)

Content player v1 can be integrate in Desktop app, Mobile app by using the npm package. This  provide the capability to render ECML, epub, pdf, mp4, youtube, mp3 and html type contents. V1 player has dependency on sunbird telemetry sdk and content plugins.

### Content Launchers

Content player v1 is able to play the different format of content using the configuration. You just need to provide the mimeType and plugin launchers in config. Its capable to load the content launchers according to the mimeType

#### Base launcher

Base launcher is responsible to launch following launchers based on the mime types of the assets

* ECML : ECML launcher derived from the base launcher and also is responsible to launch the ecml type assets
* Epub : Epub type assets can be render by using this launcher
* PDF : If the mime type is application/pdf, base launcher will launches the pdf launcher
* Video : This launcher is responsible to to launch the mp4, mp3, webm and youtube type assets
* HTML : This launcher also derived from the base launcher and this launcher is responsible to launch the Html files.

#### Sample config to launch the ECML assets

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
