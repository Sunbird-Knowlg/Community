# Player

Players are embeddable tools which help in rendering the assets. For ex., a video player plays all video content. Below are the players provided by Sunbird Knowlg building block:

| Content Format | MIME Type                                                               | Player                                       | Player v2                                                        |
| -------------- | ----------------------------------------------------------------------- | -------------------------------------------- | ---------------------------------------------------------------- |
| ECML           | application/vnd.ekstep.ecml-archive                                     | [Yes](v1/players/ecml-player-v1.md)          | No                                                               |
| HTML, H5P      | application/vnd.ekstep.html-archive, application/vnd.ekstep.h5p-archive | [Yes](v1/players/html-h5p-player-v1.md)      | No                                                               |
| PDF            | application/pdf                                                         | [Yes](v1/players/pdf-player-v1.md)           | [Yes](v2/pdf-player/)                                            |
| Epub           | application/epub                                                        | [Yes](v1/players/epub-player-v1.md)          | [Yes](../../../use/installation-guide/players/v2/epub-player.md) |
| WEBM, MP4      | video/Webm, video/mp4                                                   | [Yes](v1/players/video-player-v1.md)         | [Yes](v2/video-player/)                                          |
| YOUTUBE        | video/x-youtube,                                                        | [Yes](v1/players/video-player-v1.md#youtube) | No                                                               |

### MIME Type

MIME Types defines the what type of the content it is. According to the mimeType you can load the specific [content launcher](v1/architecture.md#content-launchers) and play the different types of contents

### Online

Players are capable to rendering the assets online in web browser, mobile app and desktop app using the streaming url

#### Streaming url

Streaming URL is a used to stream the asset online. This streaming Url can be present in content metadata. If the streaming Url is present in metadata, the assets can be play online.

Sample streaming URL

```
metadata: {
    "streamingUrl":"https://sunbirddevmedia-inct.streaming.media.azure.net/9e45c4d8-37bf-430f-a467-388b37075d25/webm1-copy-17.ism/manifest(format=m3u8-aapl-v3)"
}
```

### Offline

Assets can be rendered offline in the player. Only html/h5p player v1 won't support the offline play.&#x20;

Please refer developer doc for [offline telemetry sync](http://docs.sunbird.org/2.0.0/developer-docs/how-to-guide/sync\_telemetry\_data\_captured\_from\_offline\_devices/) support
