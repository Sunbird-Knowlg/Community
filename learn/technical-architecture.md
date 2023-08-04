# Technical Architecture

### Component view

The diagram provided illustrates the various components comprising the Knowlg Building Block.

<figure><img src="../.gitbook/assets/Component View (1).png" alt=""><figcaption><p>Component View</p></figcaption></figure>

### Deployment View

<figure><img src="../.gitbook/assets/Deployemnt View.png" alt=""><figcaption><p>Deployemnt View</p></figcaption></figure>

The diagram above depicts the components that are part of the Knowlg Building Block and illustrates how they are deployed within the system.

* **Neo4j** functions as the primary data store for the content-service. Within this Neo4j database, the data of each asset is stored as a graph node, allowing for efficient and interconnected data representation.
* The asset data is primarily stored in Neo4J. However, due to the large size of external or additional data associated with the asset, such as the body of the asset, collection hierarchy, and other extensive information, this data is stored separately in **Cassandra**. By utilizing Cassandra to store this large-size data, the system can efficiently manage and retrieve asset-related information without overwhelming the Neo4J database. This approach ensures a scalable and optimized storage solution for assets, allowing Neo4J to focus on managing the core relationships and structure of the asset data, while Cassandra handles the storage of extensive asset-related information.
* To enhance the API's performance and reduce the need for frequent database queries during Read calls, we have implemented **Redis** as a temporary cache. Redis serves as an in-memory data store that holds frequently accessed data. When a Read call is made to the API, the data is first checked in the Redis cache. If the data is found in Redis, the API can retrieve it directly from memory, avoiding the need to hit the database. This caching strategy significantly improves response times and reduces the load on the database, resulting in a more efficient and responsive API. Additionally, by using Redis as a cache, we can ensure that frequently requested data is readily available, further optimizing the overall performance of the API.
* By leveraging **Flink** (Async Jobs), we enable real-time and batch data processing with low latency, high throughput, and fault tolerance.
