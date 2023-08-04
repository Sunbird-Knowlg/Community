# Technical Architecture

### Component view

<figure><img src="../.gitbook/assets/Component View.png" alt=""><figcaption><p>Component view</p></figcaption></figure>

### Deployment View

<figure><img src="../.gitbook/assets/Deployemnt View (2).png" alt=""><figcaption><p>Deployment View</p></figcaption></figure>

* **Neo4j** functions as the primary data store for the content-service. Within this Neo4j database, the data of each asset is stored as a graph node, allowing for efficient and interconnected data representation.
* The asset data is primarily stored in Neo4J. However, due to the large size of external or additional data associated with the asset, such as the body of the asset, collection hierarchy, and other extensive information, this data is stored separately in **Cassandra**. By utilizing Cassandra to store this large-size data, the system can efficiently manage and retrieve asset-related information without overwhelming the Neo4J database. This approach ensures a scalable and optimized storage solution for assets, allowing Neo4J to focus on managing the core relationships and structure of the asset data, while Cassandra handles the storage of extensive asset-related information.
