# Deployment

{% hint style="danger" %}
The Sunbird-Knowlg can be deployed independently. But at present we dont have installation guide to deploy Sunbird-Knowlg alone. Please reach out to our technical team  to deploy independently. \
[https://github.com/Sunbird-knowlg/Community/discussions](https://github.com/Sunbird-knowlg/Community/discussions)
{% endhint %}



{% hint style="danger" %}
At present Sunbird-Knowlg deployment steps is packaged with Sunbird-ED. \
Please refer to the [Sunbird-Ed deployment ](https://ed.sunbird.org/use/prerequisites-for-your-own-sunbird-ed-instance)for more details.
{% endhint %}

{% content-ref url="https://app.gitbook.com/o/-Mi9QwJlsfb7xuxTBc0J/s/-MkgPDmvKwE_DgYJbvPS/" %}
[Sunbird ED](https://app.gitbook.com/o/-Mi9QwJlsfb7xuxTBc0J/s/-MkgPDmvKwE\_DgYJbvPS/)
{% endcontent-ref %}

![](<../.gitbook/assets/SB-Knowlg (2).png>)

[SB-Knowlg ](https://app.gitbook.com/o/-Mi9QwJlsfb7xuxTBc0J/s/aanfWbeVT74C5lXDPde3/)is packaged with some micro-services as shown in the above architecture.

* [Content-service](../learn/product-and-developer-guide/content-service/)
* [Search-service](../learn/product-and-developer-guide/assets-search-service/)(also called asset-search-service)
* [Taxonomy-service](../learn/product-and-developer-guide/taxonomy-and-tagging/)
* [DIAL-service](installation-guide/services/dial-service.md)

The below list of DB's are used in the above micro-services

* **Neo4J**: \
  This is used as a primary data store of the content-service & Taxonomy-service. The data of each asset is stored as a graph node. The data from this Neo4j DB will sync to Elasticsearch through flinkJob(search-Indxer) for ease of discovery.
* **Cassandra:**\
  This DB is used by content-service, Taxonomy-service & DIAL service. \
  _Content-service:_ The asset data is stored in Neo4J. B the external/additional data of the asset will be stored in Cassandra because of large size data/information like Body, Collection hierarchy etc.\
  _Taxonomy-service_: Object category definations are stored here. \
  DIAL-service: We are using Cassadra as a primary store of DIAL data/information. This data will be synced to Elasticsearch through flinkJob(search-Indxer)
* **Redis:**\
  ****To improve the performance of API instead of hitting the DB for every Read call, we are using the Redis as temp cache.
* **Elasticsearch:**\
  ****This is the primary DB of the search-service(asset-search-service). There is not directly feed/post of the data to the elastic-search DB. The data will be synced from Neo4J to elasticsearch through Flink job(Search-indexer) only.\


****

