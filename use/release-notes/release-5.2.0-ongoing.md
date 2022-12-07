# Release-5.2.0 (ongoing)

### <mark style="color:blue;">5.2.0</mark> (12-09-2022)

Discussion thread: [https://github.com/Sunbird-Knowlg/Community/discussions/76](https://github.com/Sunbird-Knowlg/Community/discussions/76)

|                | Start date   | End date     |
| -------------- | ------------ | ------------ |
| Planning phase | 12 Sept 2022 | 23 Sept 2022 |
| Sprint 1       | 26 Sept 2022 | 14 Oct 2022  |
| Sprint 2       | 17 Oct 2022  | 4 Nov 2022   |
| PPV            | 7 Nov 2022   | 18 Nov 2022  |
| Prod           | 21 Nov 2022  |              |



| Component                 | Service to be build                                             | Tag                                                                                                                      | Comment                                                                                                                                                                                                                                                                                                                                                                                            |
| ------------------------- | --------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Knowledge-platform        | <p>Build/Kubernetes/Content</p><p>Build/Kubernetes/Taxonomy</p> | ****[**release-5.2.0\_RC1**](https://github.com/project-sunbird/knowledge-platform/tree/release-5.2.0\_RC1)****          | Deploy the content-service and taxonomy-service. Please find the configuration changes below in [Configurations](https://knowlg.sunbird.org/use/release-notes/release-5.2.0-ongoing#configurations) section.                                                                                                                                                                                       |
| Sunbird-learning-service  | Build/KnowldgePlatform/Learning                                 | ****[**release-5.2.0\_RC1**](https://github.com/project-sunbird/sunbird-learning-platform/tree/release-5.2.0\_RC1)****   | Deploy the learning service.                                                                                                                                                                                                                                                                                                                                                                       |
| Knowledge-platform-jobs   | Build/KnowldgePlatform/Flinkjobs                                | ****[**release-5.2.0\_RC1**](https://github.com/project-sunbird/knowledge-platform-jobs/tree/release-5.2.0\_RC1)****     | Please deploy the **assessment-enrichment**, **content-publish**, **qrcode-image-generator**, **search-indexer**, **csp-migrator,** **live-node-publisher,** **live-video-stream-generator,** **cassandra-data-migration** flink jobs. Please find the configuration changes below in [Configurations](https://knowlg.sunbird.org/use/release-notes/release-5.2.0-ongoing#configurations) section. |
| Sunbird-Collection-Editor | NA                                                              | [**v5.2.4**](https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.2.4)****                       | NA                                                                                                                                                                                                                                                                                                                                                                                                 |
| Sunbird-Content-Editor    | Build/Plugins/ContentEditor                                     | [**release-5.2.0\_RC1**](https://github.com/project-sunbird/sunbird-content-editor/releases/tag/release-5.2.0\_RC1)****  | NA                                                                                                                                                                                                                                                                                                                                                                                                 |
| Sunbird-Generic-Editor    | Build/Plugins/GenericEditor                                     | [**release-5.2.0\_RC1**](https://github.com/project-sunbird/sunbird-generic-editor/releases/tag/release-5.2.0\_RC1)      | NA                                                                                                                                                                                                                                                                                                                                                                                                 |
| Sunbird-content-plugins   | Build/Plugins/ContentPlugins                                    | [**release-5.2.0\_RC1**](https://github.com/project-sunbird/sunbird-content-plugins/releases/tag/release-5.2.0\_RC1)**** | NA                                                                                                                                                                                                                                                                                                                                                                                                 |

### Configurations

| Service/Jobs                                                                                                                                                                                             | Old Configuration                                                                                                                                                                                                                                                                    | New Configuration                                                                                                                                                                                                                                                                                                                                     |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [content-service](https://github.com/project-sunbird/sunbird-devops/blob/3ed1a90d8b8eed09666468194fcac2a655c05c96/ansible/roles/stack-sunbird/templates/content-service\_application.conf#L485)          | <p>cloud_storage_type: "{{ sunbird_cloud_storage_type }}" azure_storage_key: "{{ sunbird_public_storage_account_name }}" </p><p>azure_storage_secret: "{{ sunbird_public_storage_account_key }}" </p><p>azure_storage_container: "{{ sunbird_content_azure_storage_container }}"</p> | cloud\_storage\_type: "\{{ cloud\_service\_provider \}}" cloud\_storage\_key: "\{{ cloud\_public\_storage\_accountname \}}" cloud\_storage\_secret: "\{{ cloud\_public\_storage\_secret \}}" cloud\_storage\_endpoint: "\{{ cloud\_public\_storage\_endpoint \}}" cloud\_storage\_container: "\{{ cloud\_storage\_content\_bucketname \}}"            |
| [content-service](https://github.com/project-sunbird/sunbird-devops/blob/3ed1a90d8b8eed09666468194fcac2a655c05c96/ansible/roles/stack-sunbird/templates/content-service\_application.conf#L643)          |                                                                                                                                                                                                                                                                                      | <p>cloudstorage { metadata.replace_absolute_path={{ cloudstorage_replace_absolute_path | default('false') }} relative_path_prefix={{ cloudstorage_relative_path_prefix_content }} </p><p>metadata.list={{ cloudstorage_metadata_list }} read_base_path="{{ cloudstorage_base_path }}" write_base_path={{ valid_cloudstorage_base_urls }} </p><p>}</p> |
| [taxonomy-service](https://github.com/project-sunbird/sunbird-devops/blob/3ed1a90d8b8eed09666468194fcac2a655c05c96/ansible/roles/stack-sunbird/templates/taxonomy-service\_application.conf#L368)        | <p>cloud_storage_type: "azure" azure_storage_key: "{{ sunbird_public_storage_account_name }}" </p><p>azure_storage_secret: "{{ sunbird_public_storage_account_key }}" </p><p>azure_storage_container: "{{ sunbird_content_azure_storage_container }}"</p>                            | <p>cloud_storage_type: "{{ cloud_service_provider }}" cloud_storage_key: "{{ cloud_public_storage_accountname }}" </p><p>cloud_storage_secret: "{{ cloud_public_storage_secret }}" cloud_storage_endpoint: "{{ cloud_public_storage_endpoint }}" cloud_storage_container: "{{ cloud_storage_content_bucketname }}"</p>                                |
| [taxonomy-service](https://github.com/project-sunbird/sunbird-devops/blob/3ed1a90d8b8eed09666468194fcac2a655c05c96/ansible/roles/stack-sunbird/templates/taxonomy-service\_application.conf#L402)        |                                                                                                                                                                                                                                                                                      | <p>cloudstorage { metadata.replace_absolute_path={{ cloudstorage_replace_absolute_path | default('false') }} relative_path_prefix={{ cloudstorage_relative_path_prefix_content }} </p><p>metadata.list={{ cloudstorage_metadata_list }} read_base_path="{{ cloudstorage_base_path }}" write_base_path={{ valid_cloudstorage_base_urls }} </p><p>}</p> |
| [assessment-service](https://github.com/project-sunbird/sunbird-devops/blob/release-5.2.0-knowlg/ansible/roles/stack-sunbird/templates/assessment-service\_application.conf#L386)                        | <p>cloud_storage_type: "azure" azure_storage_key: "{{ sunbird_public_storage_account_name }}" </p><p>azure_storage_secret: "{{ sunbird_public_storage_account_key }}" </p><p>azure_storage_container: "{{ sunbird_content_azure_storage_container }}"</p>                            | cloud\_storage\_type: "\{{ cloud\_service\_provider \}}" cloud\_storage\_key: "\{{ cloud\_public\_storage\_accountname \}}" cloud\_storage\_secret: "\{{ cloud\_public\_storage\_secret \}}" cloud\_storage\_endpoint: "\{{ cloud\_public\_storage\_endpoint \}}" cloud\_storage\_container: "\{{ cloud\_storage\_content\_bucketname \}}"            |
| [assessment-service](https://github.com/project-sunbird/sunbird-devops/blob/3ed1a90d8b8eed09666468194fcac2a655c05c96/ansible/roles/stack-sunbird/templates/assessment-service\_application.conf#L431)    |                                                                                                                                                                                                                                                                                      | <p>cloudstorage { metadata.replace_absolute_path={{ cloudstorage_replace_absolute_path | default('false') }} relative_path_prefix={{ cloudstorage_relative_path_prefix_content }} </p><p>metadata.list={{ cloudstorage_metadata_list }} read_base_path="{{ cloudstorage_base_path }}" write_base_path={{ valid_cloudstorage_base_urls }} </p><p>}</p> |
| [asset-enrichment flink job](https://github.com/project-sunbird/sunbird-learning-platform/blob/92604bb70357cea083a879f818a5c6b30bebbaeb/kubernetes/helm\_charts/datapipeline\_jobs/values.j2#L318)       | <p>cloud_storage_type="{{ cloud_store }}" </p><p>azure_storage_key="{{ sunbird_public_storage_account_name }}" </p><p>azure_storage_secret="{{ sunbird_public_storage_account_key }}" </p><p>azure_storage_container="{{ azure_public_container }}"</p>                              | cloud\_storage\_type: "\{{ cloud\_service\_provider \}}" cloud\_storage\_key: "\{{ cloud\_public\_storage\_accountname \}}" cloud\_storage\_secret: "\{{ cloud\_public\_storage\_secret \}}" cloud\_storage\_endpoint: "\{{ cloud\_public\_storage\_endpoint \}}" cloud\_storage\_container: "\{{ cloud\_storage\_content\_bucketname \}}"            |
| [asset-enrichment flink job](https://github.com/project-sunbird/sunbird-learning-platform/blob/92604bb70357cea083a879f818a5c6b30bebbaeb/kubernetes/helm\_charts/datapipeline\_jobs/values.j2#L323)       |                                                                                                                                                                                                                                                                                      | <p>cloudstorage { metadata.replace_absolute_path={{ cloudstorage_replace_absolute_path | default('false') }} relative_path_prefix={{ cloudstorage_relative_path_prefix_content }} </p><p>metadata.list={{ cloudstorage_metadata_list }} read_base_path="{{ cloudstorage_base_path }}" write_base_path={{ valid_cloudstorage_base_urls }} </p><p>}</p> |
| [content-publish flink job](https://github.com/project-sunbird/sunbird-learning-platform/blob/92604bb70357cea083a879f818a5c6b30bebbaeb/kubernetes/helm\_charts/datapipeline\_jobs/values.j2#L622)        | <p>cloud_storage_type="{{ cloud_store }}" </p><p>azure_storage_key="{{ sunbird_public_storage_account_name }}" </p><p>azure_storage_secret="{{ sunbird_public_storage_account_key }}" </p><p>azure_storage_container="{{ azure_public_container }}"</p>                              | cloud\_storage\_type: "\{{ cloud\_service\_provider \}}" cloud\_storage\_key: "\{{ cloud\_public\_storage\_accountname \}}" cloud\_storage\_secret: "\{{ cloud\_public\_storage\_secret \}}" cloud\_storage\_endpoint: "\{{ cloud\_public\_storage\_endpoint \}}" cloud\_storage\_container: "\{{ cloud\_storage\_content\_bucketname \}}"            |
| [content-publish flink job](https://github.com/project-sunbird/sunbird-learning-platform/blob/92604bb70357cea083a879f818a5c6b30bebbaeb/kubernetes/helm\_charts/datapipeline\_jobs/values.j2#L627)        |                                                                                                                                                                                                                                                                                      | <p>cloudstorage { metadata.replace_absolute_path={{ cloudstorage_replace_absolute_path | default('false') }} relative_path_prefix={{ cloudstorage_relative_path_prefix_content }} </p><p>metadata.list={{ cloudstorage_metadata_list }} read_base_path="{{ cloudstorage_base_path }}" write_base_path={{ valid_cloudstorage_base_urls }} </p><p>}</p> |
| [qrcode-image-generator flink job](https://github.com/project-sunbird/sunbird-learning-platform/blob/92604bb70357cea083a879f818a5c6b30bebbaeb/kubernetes/helm\_charts/datapipeline\_jobs/values.j2#L679) | <p>cloud_storage_type="{{ cloud_store }}" </p><p>azure_storage_key="{{ sunbird_public_storage_account_name }}" </p><p>azure_storage_secret="{{ sunbird_public_storage_account_key }}" </p><p>azure_storage_container="{{ azure_public_container }}"</p>                              | <p>cloud_storage_type="{{ cloud_service_provider }}" cloud_storage_key="{{ cloud_public_storage_accountname }}" </p><p>cloud_storage_secret="{{ cloud_public_storage_secret }}" cloud_storage_container="{{ cloud_storage_dial_bucketname | default("dial") }}"</p>                                                                                   |
| [qrcode-image-generator flink job](https://github.com/project-sunbird/sunbird-learning-platform/blob/92604bb70357cea083a879f818a5c6b30bebbaeb/kubernetes/helm\_charts/datapipeline\_jobs/values.j2#L671) |                                                                                                                                                                                                                                                                                      | <p>cloudstorage { metadata.replace_absolute_path={{ cloudstorage_replace_absolute_path | default('false') }} relative_path_prefix={{ cloudstorage_relative_path_prefix_dial }} </p><p>metadata.list={{ cloudstorage_metadata_list }} read_base_path="{{ cloudstorage_base_path }}" write_base_path={{ valid_cloudstorage_base_urls }} </p><p>}</p>    |
| [search-indexer flink job](https://github.com/project-sunbird/sunbird-learning-platform/blob/92604bb70357cea083a879f818a5c6b30bebbaeb/kubernetes/helm\_charts/datapipeline\_jobs/values.j2#L269)         |                                                                                                                                                                                                                                                                                      | <p>cloudstorage { metadata.replace_absolute_path={{ cloudstorage_replace_absolute_path | default('false') }} relative_path_prefix={{ cloudstorage_relative_path_prefix_content }} </p><p>metadata.list={{ cloudstorage_metadata_list }} read_base_path="{{ cloudstorage_base_path }}" </p><p>}</p>                                                    |

#### Default values for config

default config for [flink-jobs](https://github.com/project-sunbird/sunbird-learning-platform/blob/92604bb70357cea083a879f818a5c6b30bebbaeb/kubernetes/ansible/roles/flink-jobs-deploy/defaults/main.yml#L399) and [services](https://github.com/project-sunbird/sunbird-devops/blob/cc90889f2d13c4385a1cef0bfefbeec30e71406e/ansible/roles/stack-sunbird/defaults/main.yml#L1052)

```
cloudstorage_relative_path_prefix_content: "CONTENT_STORAGE_BASE_PATH"
cloudstorage_relative_path_prefix_dial: "DIAL_STORAGE_BASE_PATH"
cloudstorage_metadata_list: '["appIcon","posterImage","artifactUrl","downloadUrl","variants","previewUrl","pdfUrl", "streamingUrl", "toc_url"]
```

#### <mark style="color:red;">Deprecated variables</mark>

* <mark style="color:red;">sunbird\_cloud\_storage\_type</mark>
* <mark style="color:red;">sunbird\_public\_storage\_account\_name</mark>
* <mark style="color:red;">sunbird\_public\_storage\_account\_key</mark>
* <mark style="color:red;">azure\_public\_container</mark>
* <mark style="color:red;">sunbird\_content\_azure\_storage\_container</mark>



**New Flink Jobs:**

* [csp-migrator](https://knowlg.sunbird.org/learn/product-and-developer-guide/knowlg-jobs/configuration#csp-migrator)
* [live-node-publisher](https://knowlg.sunbird.org/learn/product-and-developer-guide/knowlg-jobs/configuration#live-node-publisher)
* [live-video-stream-generator](https://knowlg.sunbird.org/learn/product-and-developer-guide/knowlg-jobs/configuration#live-video-stream-generator)
* [cassandra-data-migration](https://knowlg.sunbird.org/learn/product-and-developer-guide/knowlg-jobs/configuration#cassandra-data-migration)

### Migration process:

refer [data-migration.md](../../learn/product-and-developer-guide/other/data-migration.md "mention") page for more details.

Reference diagram to know how the migration of existing data with CNAME(storing relative path DB)&#x20;

{% embed url="https://app.diagrams.net/#G1HzUob6a9_TrVWhcoo1nWoKPVN0PKzpmQ" %}
migration flow diagram (migration-job flow & migration-process workflow)
{% endembed %}

#### Sequence of migration steps:

The content migration should execute in the below order only. Otherwise there is a chances of migration failure because of dependent content is not yet migrated. [more details](https://docs.google.com/spreadsheets/d/13DaXCx8uToOwinlAPxvTat8NELxiPgG4KXATcKaJm\_c/edit#gid=1675310401\&range=K3)

| Sequence | Type        |
| -------- | ----------- |
| 1        | Asset       |
| 1        | Other       |
| 2        | EPUB        |
| 2        | H5P         |
| 2        | HTML        |
| 2        | PDF         |
| 2        | Question    |
| 2        | QuestionSet |
| 2        | Video       |
| 2        | Youtube     |
| 3        | ECML        |
| 4        | Collection  |

#### Verification of migration steps:

*   Verify all the nodes of specific asset type is migrated to "1.0" for not.

    TBU: Script to verify the nodes are migrated
*   Verify any node is have failed while doing migration. Logs will have detailed migration fail reasons

    * 0.1 => Node migration failed&#x20;
    * 0.2 => Node migration failed while publishing of the content
    * 0.3 => Node migration failed while streaming

    TBU: Script to verify any nodes have migration version as 0.1, 0.2 & 0.3 (migration failed)

Sample logs to verify the migration&#x20;
