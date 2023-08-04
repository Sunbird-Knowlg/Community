---
description: This page explains the composite service specific configuration parameter
---

# Configuration

Composite search service file configuration is available at [https://github.com/project-sunbird/sunbird-devops/blob/master/ansible/roles/stack-sunbird/templates/search-service\_application.conf](https://github.com/project-sunbird/sunbird-devops/blob/master/ansible/roles/stack-sunbird/templates/search-service\_application.conf)

| Variable                       | Purpose                                                                                                                                                                                                          |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| search.es\_conn\_info\*        | Elastic Search host IP                                                                                                                                                                                           |
| compositesearch.index.name\*   | ElasticSearch index for composite search functionality.                                                                                                                                                          |
| search.fields.mode\_collection | <p>Set of fields that will be part of content result when search mode is collection.<br><em>Default list of fields:</em> "identifier", "name", "objectType", "contentType", "mimeType", "size", "childNodes"</p> |
| search.payload.log\_enable     | <p>Parameter to enable and disable search requests logging.<br><em>Default logging:</em> false</p>                                                                                                               |
| channel.default                | Default channel Id to be populated in search request headers if "x-channel-id" is not part of search request headers. _This is not a mandatory configuration._                                                   |
| telemetry.search.topn          |                                                                                                                                                                                                                  |
| search.batch.size              | Elastic search batch size for number of records to be indexed. _Default value:_ 1000                                                                                                                             |
| search.fields.query            |                                                                                                                                                                                                                  |
| search.fields.date             | Used to identify date fields of object models that are being synced to elastic search in ElasticSearchUtil Class. _This is not a mandatory configuration._                                                       |
| time-zone                      | Used to define time zone property in ElasticSearchUtil Class. _This is not a mandatory configuration._                                                                                                           |
|                                |                                                                                                                                                                                                                  |

{% hint style="info" %}
'\*' - mandatory configuration fields
{% endhint %}
