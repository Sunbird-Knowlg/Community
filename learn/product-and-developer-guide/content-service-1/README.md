# Collection service

The Content service uses the Graph engine to communicate with Neo4j. The Graph engine expects schema definitions for each object type. It validates the data object with the object definition during various CRUD operations.

## Learning Assets <a href="#object" id="object"></a>

Knowledge has been the differentiator of the human race from other species for a long time. Humans had understood the importance of knowledge and passed it to next-generation via stone carving, writing on leaf and manuscript etc.

In the era of the digital age, learning and knowledge transfer has also become digital. Now all the knowledge is getting transferred via digital means.

Learning Assets is the core entity to serve the learning need of a user under the content of any domain. Learning assets can be Story, Quiz, Game, Instruction simulation etc. Learning Assets can manifest in formats such as Audio, Video, Slides, Documents etc.

It can cater to different user groups in a _domain_ eg. In the school education context, learning assets for different user groups such as student, teacher and parent can be served via different types of assets such as learning content, video explanation etc organised in a textbook structure.

![](<../../../.gitbook/assets/Learning Assets interactions.png>)

_Learning Assets is a generalized object created using the knowledge microservices. Learning assets (Content Object) is a configurable entity that can be extended to serve tons of use cases in multiple domains_

### **Lifecycle of Learning Assets**

Lifecycle of learning assets is a 5 stage cyclic process, Learning Assets follow maker checked method for assets creations.

Draft --> Review --> Publish --> Package --> Update

![Asset lifecycle](<../../../.gitbook/assets/Asset LifeCycle.png>)



### Additional Information

For further explanation of objects and categories can be found in the following videos:

[Understanding Content Architecture of Sunbird](https://www.youtube.com/watch?v=WxZXaTnj2D0\&t=7s)

[Understand Collection Architecture : Enabling Organised and Contextual Experience](https://www.youtube.com/watch?v=n9H87z0-7eU\&t=1709s)

## :stars:Installation guide

{% content-ref url="../../../use/installation-guide/services/asset-management-service/" %}
[asset-management-service](../../../use/installation-guide/services/asset-management-service/)
{% endcontent-ref %}
