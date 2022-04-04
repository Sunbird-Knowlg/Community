# Content service

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

The initial stage of asset creation is _Draft_. In this stage asset creation happens. After the creation asset move to the _Review_ stage\_.\_ In the _review_ stage, \_\_ the reviewer approves, reject or request changes in the assets. Reject and request change assets move back to the Draft stage. While approved assets move to Publish stage.

Packaging follows immediately after the Publish stage. In the Package stage, an asset is prepared for online and offline usage. For online usage (streaming), assets are prepared for streaming flows. For offline assets are package and bundle to be used offline, Offline usage involves assets downloads first and uses later.

### Additional information

For further explanation of objects and categories can be found in the following videos:

[Understanding Content Architecture of Sunbird](https://www.youtube.com/watch?v=WxZXaTnj2D0\&t=7s)

[Understand Collection Architecture : Enabling Organised and Contextual Experience](https://www.youtube.com/watch?v=n9H87z0-7eU\&t=1709s)
