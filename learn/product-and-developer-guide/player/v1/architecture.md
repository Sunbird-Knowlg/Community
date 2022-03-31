# Architecture

![Content player v1 architecture](<../../../../.gitbook/assets/Content  player Achitecture-PDF player-Epub player 2.drawio (1).png>)

### Content Launchers

Content player v1 is able to play the different format of content using the configuration. You just need to provide the mimeType and plugin launchers in config. Its capable to load the content launchers according to the mimeType

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
