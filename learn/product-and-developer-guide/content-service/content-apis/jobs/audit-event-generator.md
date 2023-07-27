# Audit event generator

### :stars: audit-event-generator:

The Job utilizes the neo4j mutation data to generate AUDIT events for the Knowlg objects, following the [Sunbird Telemetry specification](https://telemetry.sunbird.org/learn/v3\_event\_details). These AUDIT events are specifically structured and formatted to adhere to the telemetry standards defined by Sunbird.

By generating these AUDIT events, the Job creates a valuable data source that can be consumed by various data analytics jobs. These data analytics jobs leverage the AUDIT events to perform in-depth analysis, monitoring, and reporting on the activities and changes related to the Knowlg objects within the system.

The AUDIT events provide valuable insights into the life-cycle and modifications of Knowlg objects, enabling data analysts to track and understand user interactions, content updates, and other relevant events. This data-driven approach empowers data analytics teams to derive meaningful patterns, trends, and metrics, facilitating data-driven decision-making and continuous improvement of the Knowlg platform.

In summary, the Job leverages neo4j mutation data to generate AUDIT events that align with Sunbird Telemetry specifications. These events serve as a valuable data source for data analytics jobs, enabling detailed analysis and monitoring of Knowlg objects and supporting data-driven insights to enhance the platform's performance and user experience.

<figure><img src="../../../../../.gitbook/assets/ audit-event-generator.png" alt=""><figcaption><p>audit-event-generator</p></figcaption></figure>

### Code:

{% embed url="https://github.com/Sunbird-Knowlg/knowledge-platform-jobs/tree/release-5.5.0/audit-event-generator" %}

### Configuration:

During the deployment process, the configuration for all knowledge-platform-jobs is sourced from the sunbird-learning-platform repository. On the other hand, for local setups, the configuration is taken from the respective job folders within the knowledge-platform-jobs repository.

**Kafka Topic:**

```
kafka {
      input.topic = "{{ env_name }}.learning.graph.events"
      groupId = "{{ env_name }}-audit-event-generator-group"
      output.topic = "{{ env_name }}.telemetry.raw"
}
```

**Job configuration variables:**

<table><thead><tr><th width="227.3754826523833">Variable</th><th>Purpose</th></tr></thead><tbody><tr><td>schema.basepath*</td><td>Used to access object schema files basepath that are hosted publicly using which object schema file path can be constructed. (Basepath Example: <a href="https://sunbirddev.blob.core.windows.net/sunbird-dial-dev/schemas/local">https://sunbirddev.blob.core.windows.net/sunbird-dial-dev/schemas/local</a>, Object schema file path example: <a href="https://sunbirddev.blob.core.windows.net/sunbird-dial-dev/schemas/local/content/schema.json">https://sunbirddev.blob.core.windows.net/sunbird-dial-dev/schemas/local/content/schema.json</a>)</td></tr><tr><td>channel.default*</td><td>Used to generate context information.</td></tr></tbody></table>

**Sample Kafka event:**

```
{
  "ets": 1649228985316,
  "channel": "01269878797503692810",
  "transactionData": {
    "properties": {
      "childNodes": {
        "ov": [
          "do_213509990427254784111670",
          "do_21351048342788505611737",
          "do_21351048359284736011739"
        ],
        "nv": [
          "do_213509990427254784111670",
          "do_21351048342788505611737",
          "do_21351048359284736011739",
          "do_2134250082225192961958"
        ]
      },
      "lastUpdatedOn": {
        "ov": "2022-04-06T07:09:14.653+0000",
        "nv": "2022-04-06T07:09:45.288+0000"
      },
      "versionKey": {
        "ov": "1649228954653",
        "nv": "1649228985288"
      }
    }
  },
  "mid": "1f33cab7-a8ba-4245-87cb-a11ab648d9c8",
  "label": "Timer Course",
  "nodeType": "DATA_NODE",
  "userId": "ANONYMOUS",
  "createdOn": "2022-04-06T07:09:45.316+0000",
  "objectType": "Collection",
  "nodeUniqueId": "do_21351048259398041611736",
  "requestId": null,
  "operationType": "UPDATE",
  "nodeGraphId": 1149046,
  "graphId": "domain"
}
```

