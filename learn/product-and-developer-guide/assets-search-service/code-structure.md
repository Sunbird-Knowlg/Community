# Code Structure

### Repository

Please refer to the provided link for the Asset search service code.

{% embed url="https://github.com/Sunbird-Knowlg/knowledge-platform/tree/release-5.7.0/search-api" %}

### Folders structure

#### Search Core

The search core contains the necessary implementations for filters and responses, which are essential functional objects that contribute to the effectiveness and user-friendliness of the search functionality within the system.

Additionally, the search core utilizes a dependency on the Elasticsearch (ES) client to interact with the Elasticsearch service. The ES client is a library or module that enables communication and interaction with the Elasticsearch cluster.

#### Search Actors

Within this module, the functionality to handle concurrency and scalability is implemented using AKKA actors.

#### Search Service

By utilizing the Play framework, this module ensures a streamlined and organized approach to developing RESTful APIs. It simplifies the process of defining routes and implementing controller actions, allowing for efficient handling of incoming requests and consistent responses. The Play framework's emphasis on clean and concise code contributes to the overall maintainability and scalability of the application.

\
