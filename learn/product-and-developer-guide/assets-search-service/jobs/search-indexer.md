# Search indexer

### :stars: search-indexer:

\
The job utilizes Neo4j transactions to index the metadata of objects into three different Elasticsearch indexes:

1. Composite search index: This index is used to store metadata related to objects, making it easier to search and retrieve specific information efficiently.
2. DIAL code index: This index is specifically designed to store data related to DIAL codes, allowing for quick retrieval and analysis of DIAL code-related information.
3. DIAL code metrics index: This index is used to store metrics related to DIAL codes, facilitating the tracking and analysis of metrics associated with DIAL codes.

By leveraging Neo4j transactions, the job ensures that the indexing process is reliable and consistent. The indexed data is then stored in the respective Elasticsearch indexes, enabling efficient searching, querying, and analysis of the object metadata, DIAL codes, and associated metrics.

<figure><img src="../../../../.gitbook/assets/search-indexer-job (1).png" alt=""><figcaption><p>Search indexer job</p></figcaption></figure>

### Code:

{% embed url="https://github.com/Sunbird-Knowlg/knowledge-platform-jobs/tree/release-5.5.0/search-indexer" %}

### Configuration:

During the deployment process, the configuration for all knowledge-platform-jobs is sourced from the sunbird-learning-platform repository. On the other hand, for local setups, the configuration is taken from the respective job folders within the knowledge-platform-jobs repository.

**Kafka Topic:**

```
kafka {
      input.topic = "{{ env_name }}.learning.graph.events"
      groupId = "{{ env_name }}-search-indexer-group"
    }
```

**Job configuration variables:**

| Variable                        | Purpose                                                                                                                                                                                 |
| ------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| compositesearch.index.name      | <p>Used to specify index name of composite search in ElasticSearch.<br><em>Default value:</em> "compositesearch"</p>                                                                    |
| dialcode.index.name             | <p>Used to specify index name of DIAL code in ElasticSearch.<br><em>Default value:</em> "dialcode"</p>                                                                                  |
| dailcodemetrics.index.name      | <p>Used to specify index name of DIAL code metrics in ElasticSearch.<br><em>Default value:</em> "dialcodemetrics"</p>                                                                   |
| restrict.metadata.objectTypes   | NOT USED                                                                                                                                                                                |
| nested.fields                   | <p>Used to specify the list of object properties that are of object types with nested attributes which are necessary for indexing in ElasticSearch.<br><em>Default value:</em> [""]</p> |
| schema.definition\_cache.expiry | NOT USED                                                                                                                                                                                |
| restrict.objectTypes            | <p>Used to specify list of object Types for which transaction event output tags are to be restricted/skipped.<br><em>Default value:</em> [""]</p>                                       |
| ignored.fields                  | <p><em>Used to specify the list of object properties that are to be ingored while indexing an object document.</em><br><em>Default value:</em> ["responseDeclaration", "body"]</p>      |
|                                 |                                                                                                                                                                                         |

**Sample Kafka** **event:**

```
{
  "ets": 1649229042072,
  "channel": "01269878797503692810",
  "transactionData": {
    "properties": {
      "childNodes": {
        "ov": [
          "do_213509990427254784111670",
          "do_21351048342788505611737",
          "do_2134250082225192961958",
          "do_21351048359284736011739",
          "do_21351048393799270411741",
          "do_21310354431597772814733"
        ],
        "nv": [
          "do_213509990427254784111670",
          "do_21351048342788505611737",
          "do_2134250082225192961958",
          "do_21351048359284736011739",
          "do_21310354431597772814733",
          "do_21351048393799270411741"
        ]
      },
      "lastUpdatedOn": {
        "ov": "2022-04-06T07:10:27.365+0000",
        "nv": "2022-04-06T07:10:42.041+0000"
      },
      "versionKey": {
        "ov": "1649229027365",
        "nv": "1649229042041"
      }
    }
  },
  "mid": "cb29eb1d-810f-4f26-a174-e37f9a681066",
  "label": "Timer Course",
  "nodeType": "DATA_NODE",
  "userId": "ANONYMOUS",
  "createdOn": "2022-04-06T07:10:42.072+0000",
  "objectType": "Collection",
  "nodeUniqueId": "do_21351048259398041611736",
  "requestId": null,
  "operationType": "UPDATE",
  "nodeGraphId": 1149046,
  "graphId": "domain"
}
```
