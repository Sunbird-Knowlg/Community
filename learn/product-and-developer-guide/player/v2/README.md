# V2

### Overview

The V2 version of the content players are designed to be lighter, deliver better performance & to be specific to the requirement.

<figure><img src="../../../../.gitbook/assets/Player Overview.png" alt=""><figcaption></figcaption></figure>

Below are the players for the V2 version:

{% content-ref url="pdf-player/" %}
[pdf-player](pdf-player/)
{% endcontent-ref %}

{% content-ref url="epub-player/" %}
[epub-player](epub-player/)
{% endcontent-ref %}

{% content-ref url="video-player/" %}
[video-player](video-player/)
{% endcontent-ref %}



**Default Features**

<details>

<summary>Side Menu</summary>



In the side menu, one can configure additional capabilities such as 'Share', 'Download'xt and 'Print'. \
![](../../../../.gitbook/assets/pdfPlayerV2Sidemenu.png)

Sample config:

```
"config": {  
    "sideMenu": { 
      "showShare": true, // show/hide share button in side menu. default value is true
      "showDownload": true, // show/hide download button in side menu. default value is true
      "showExit": false, // show/hide exit button in side menu. default value is false
      "showPrint": true // show/hide print button in side menu. default value is true
    }
}
```

</details>

