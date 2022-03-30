---
description: Video player is used to play the Youtube, Mp4, Webm and Mp3type video contents
---

# Video Player v1

## Features

Content Player v1 supports to play the following types of video contents

### **Youtube**

You can render the video of video/x-youtube mime type. Content player v1 takes the youtube url and play the youtube url online. The youtube player will not work offline. The download button will also not available for youtube contents

![](../../../../../.gitbook/assets/youtube.png)

YouTube player as capable to show the following controllers same as YouTube

* Play pause buttons
* Streaming video controls
* Full screen
* Caption reader
* Timer

### Mp4/Mp3 and Webm

Content player supports to play video/mp4 mime type video contents.  video/Webm mime type video contents comes under this category. The video renderer is also capable to play the Mp3 file.

#### **Streaming video**

Mp4 contents can be plays online and offline. The streamingUrl enhanced the capabilities of video renderer player so that user can control the streaming playback speed. The Streaming options will show for this type of contents where user can select the streaming options.&#x20;

![](../../../../../.gitbook/assets/streaming1.png)

Sample streaming URL in metadata

```
metadata: {
     "streamingUrl": "https://sunbirddevmedia-inct.streaming.media.azure.net/624b8eb7-d10b-4b48-a325-279a9d936374/mp4_9.ism/manifest(format=m3u8-aapl-v3)",
}
```

#### Download

This is the default button on the mp4/webm player. By clicking on this button user can download the video file

&#x20;

![](../../../../../.gitbook/assets/downloadvideo.png)
