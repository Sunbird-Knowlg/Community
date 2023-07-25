# Content service

The Content service uses the Graph engine to communicate with Neo4j. The Graph engine expects schema definitions for each object type. It validates the data object with the object definition during various CRUD operations.

Below are the details of the other services that are included in the package along with content-service

{% content-ref url="content-service-1/" %}
[content-service-1](content-service-1/)
{% endcontent-ref %}

{% content-ref url="content-service-2/" %}
[content-service-2](content-service-2/)
{% endcontent-ref %}

{% content-ref url="channel-service/" %}
[channel-service](channel-service/)
{% endcontent-ref %}

{% content-ref url="license-service/" %}
[license-service](license-service/)
{% endcontent-ref %}

{% hint style="info" %}
As part of the product roadmap, the Collection, Media, Channel, and License APIs mentioned above will be moving out from the content-service.
{% endhint %}

