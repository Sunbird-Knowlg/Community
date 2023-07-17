# Player

Players are embeddable tools which help in rendering the assets. For ex., a video player plays all video content. Below are the players provided by Sunbird Knowlg building block:

<table><thead><tr><th width="171.13336635502452">Content Format</th><th width="261">MIME Type</th><th width="150">Player</th><th>Player v2</th></tr></thead><tbody><tr><td>ECML</td><td>application/vnd.ekstep.ecml-archive</td><td><a href="v1/players/ecml-player-v1/">Yes</a></td><td>No</td></tr><tr><td>HTML, H5P</td><td>application/vnd.ekstep.html-archive, application/vnd.ekstep.h5p-archive</td><td><a href="v1/players/html-h5p-player-v1.md">Yes</a></td><td>No</td></tr><tr><td>PDF</td><td>application/pdf</td><td><a href="v1/players/pdf-player-v1.md">Yes</a></td><td><a href="v2/pdf-player/">Yes</a></td></tr><tr><td>Epub</td><td>application/epub</td><td><a href="v1/players/epub-player-v1.md">Yes</a></td><td><a href="../../../use/installation-guide/players/v2/epub-player.md">Yes</a></td></tr><tr><td>WEBM, MP4</td><td>video/Webm, video/mp4</td><td><a href="v1/players/video-player-v1.md">Yes</a></td><td><a href="v2/video-player/">Yes</a></td></tr><tr><td>YOUTUBE</td><td>video/x-youtube, </td><td><a href="v1/players/video-player-v1.md#youtube">Yes</a></td><td>No</td></tr></tbody></table>

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

Please refer developer doc for [offline telemetry sync](telemetry-events/offline-telemetry.md) support
