# Content service

The Content service uses the Graph engine to communicate with Neo4j. The Graph engine expects schema definitions for each object type. It validates the data object with the object definition during various CRUD operations.

Content-service is the core of the SB-Knowlg. All the API's related to Asset & it's life-cycle are part of this service.&#x20;

This service is also packaged with other services like tenant/channel & License.&#x20;

{% content-ref url="channel-service/" %}
[channel-service](channel-service/)
{% endcontent-ref %}

{% content-ref url="license-service/" %}
[license-service](license-service/)
{% endcontent-ref %}

{% hint style="info" %}
The above Channel & License services will be moving out from content-service as part of the product roadmap.
{% endhint %}

### :stars:Installation guide

{% content-ref url="../../../use/installation-guide/services/asset-management-service/" %}
[asset-management-service](../../../use/installation-guide/services/asset-management-service/)
{% endcontent-ref %}

### Additional Information

For further explanation of objects and categories can be found in the following videos:

[Understanding Content Architecture of Sunbird](https://www.youtube.com/watch?v=WxZXaTnj2D0\&t=7s)

[Understand Collection Architecture : Enabling Organised and Contextual Experience](https://www.youtube.com/watch?v=n9H87z0-7eU\&t=1709s)
