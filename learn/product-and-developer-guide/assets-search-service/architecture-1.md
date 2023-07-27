# Architecture

The below diagram represents the components involved and their arrangement in **Search** service.

1. The **search service** module has a play application and its internal actor module.&#x20;
2. By leveraging **Elasticsearch**, we can deliver an efficient and robust search experience to our users, ensuring that our application performs exceptionally well and remains flexible to adapt to future needs.
3. By leveraging **Flink**, we enable real-time and batch data processing with low latency, high throughput, and fault tolerance.

<figure><img src="../../../.gitbook/assets/asset-search-architecture (7).png" alt=""><figcaption><p>asset-search-architecture</p></figcaption></figure>

## Flow-diagram

With the content/collection APIs, we have the ability to create or update assets (content/collection). These assets are stored in Neo4j, and to track any transactions, we've implemented custom [neo4j-extensions](https://github.com/Sunbird-Knowlg/knowledge-platform-db-extensions) that generate transaction logs and store them in log files associated with asset changes in Neo4j.

To process these transaction logs and ensure their real-time availability, we employ Logstash to read the logs from the files and push them to the transaction events Kafka topic. Subsequently, we use a Flink job to consume and process these events, finally storing them in Elasticsearch for further analysis and querying.&#x20;

<figure><img src="../../../.gitbook/assets/search-service-flow-diagram (1).png" alt=""><figcaption><p>search-service-flow-diagram</p></figcaption></figure>
