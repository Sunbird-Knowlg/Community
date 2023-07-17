# Release - 5.2.0

### <mark style="color:blue;">**Hot-fix:  5.2.1**</mark>** (20-01-2023)**

**Bugs:**

* For some content, when we access via dial code scanner, The play button does not play the content when click - [KN-856](https://project-sunbird.atlassian.net/browse/KN-856)\
  **NOTE:** Please deploy **content-publish** Flink job to apply the patch for the above fix.
* **csp-migrator** Flink job enhancement to upload external URL artefacts and Google Drive artefacts to sunbird cloud container.\
  **NOTE:** Please deploy **csp-migrator** Flink job to apply the patch for the above fix.



| Component               | Build Job                         | Build Tag                                                                                                        | Deploy Job                         | Deployment                                                                                                 | Comment                                                                         |
| ----------------------- | --------------------------------- | ---------------------------------------------------------------------------------------------------------------- | ---------------------------------- | ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| Knowledge-platform-jobs | Build/KnowledgePlatform/FlinkJobs | [release-5.2.1\_RC1](https://github.com/project-sunbird/knowledge-platform-jobs/releases/tag/release-5.2.1\_RC1) | Deploy/KnowledgePlatform/FlinkJobs | [release-5.2.1\_RC1](https://github.com/project-sunbird/sunbird-learning-platform/tree/release-5.2.1\_RC1) | <p>Jobs to be deploy:</p><ol><li>csp-migrator</li><li>content-publish</li></ol> |

### <mark style="color:blue;">**Hot-fix:  5.2.0**</mark>** (16-01-2023)**

<mark style="color:blue;">**Bugs:**</mark>

Mobile:- Not getting the merit certificate, the scores are not updated on the TOC page. [ ](https://project-sunbird.atlassian.net/browse/KN-710)[KN-731](https://project-sunbird.atlassian.net/browse/KN-731)

| Sunbird-Content-Player | [**v5.1.0**](https://www.npmjs.com/package/@project-sunbird/content-player/v/5.1.0) |  Whitelist urls config fixes |
| ---------------------- | ----------------------------------------------------------------------------------- | ---------------------------- |

<mark style="color:red;">Required configuration changes: The parent container(Portal & Mobile App’s) should have pass the CNAME or blob URLs as a whiteListUrl configuration. Previously it was hard-coded in player, from this release we are expecting this whiteListUrl as a configuration. The URLs that passed as configuration only will allow from player, other URLs will be blocked.</mark>

```
playerConfig = {
   context: ... //context config
   config: { whiteListUrl : ['https://obj.stage.sunbirded.org/**']} //whitelist URLs array config
   metadata: ... // metadata of the content
   data: ... // body of the content
}
```

## <mark style="color:blue;">hot-fix changes(release-5.2.0 itself)</mark>

[Release-5.1.2 hot-fix changes](release-5.1.0-ongoing.md#hot-fix-5.1.2-29-12-2022) are merged as part of the existing release-5.2.0 itself.

### Bug

Course progress does not get updated correctly( End event summary fix). [ #KN-710](https://project-sunbird.atlassian.net/browse/KN-710) (It will go has hot fix)

| Sunbird-Video-Player | **​**[**​**](https://www.npmjs.com/package/@project-sunbird/sunbird-video-player-v9/v/5.1.3)[**v5.2.4**](https://www.npmjs.com/package/@project-sunbird/sunbird-video-player-v9/v/5.2.4) | End event summary fix |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------- |

##

## <mark style="color:blue;">5.2.0</mark> (06-12-2022)

Discussion thread: [https://github.com/Sunbird-Knowlg/Community/discussions/76](https://github.com/Sunbird-Knowlg/Community/discussions/76)

|                | Start date                                               | End date     |
| -------------- | -------------------------------------------------------- | ------------ |
| Planning phase | 12 Sept 2022                                             | 23 Sept 2022 |
| Sprint 1       | 26 Sept 2022                                             | 14 Oct 2022  |
| Sprint 2       | 17 Oct 2022                                              | 4 Nov 2022   |
| PPV            | 7 Nov 2022                                               | 18 Nov 2022  |
| Prod           | <mark style="color:red;">21 Nov 2022</mark>(06 Dec 2022) |              |

### Features

* Angular version upgrade&#x20;
  * PDF Player (12 to 14 with IVY) #[KN-316](https://project-sunbird.atlassian.net/browse/KN-316)
  * Video, Epub Players(9 to 12) #[KN-523](https://project-sunbird.atlassian.net/browse/KN-523)
* One step installation of Knowledge-Platform [#KN-585](https://project-sunbird.atlassian.net/browse/KN-585)
* Design: Separation of question-set & Collection-Editor [#KN-8](https://project-sunbird.atlassian.net/browse/KN-8)
*   CSP - Knowlg microservices should be cloud agnostic [#KN-603](https://project-sunbird.atlassian.net/browse/KN-603)

    As a part of  CSP changes part 2, migration of DIAL service is completed and signing off.
* CSP - GCP video streaming interface(Slipped - Pushing as hot-fix of release-5.2.0) [#KN-549](https://project-sunbird.atlassian.net/browse/KN-549)

#### &#x20;(Adopter should integrate)

* Player: Published as web-component for ease of integration which is framework agnostic
  * Video/Youtube Player #[KN-517](https://project-sunbird.atlassian.net/browse/KN-517)
  * EPUB Player #[KN-517](https://project-sunbird.atlassian.net/browse/KN-517)
  * PDF player #[KN-304](https://project-sunbird.atlassian.net/browse/KN-304)

### Bug

* Properties with underscore are getting omitted from context data search#[KN-546](https://project-sunbird.atlassian.net/browse/KN-546) (It will go has hot fix)
* Unable to release dial codes from collection[#KN-547](https://project-sunbird.atlassian.net/browse/KN-547)

### Known Issues

* QR code is not getting updated on UI when updated through CSV[#KN-730](https://project-sunbird.atlassian.net/browse/KN-730)

#### Default values for config

default config for [flink-jobs](https://github.com/project-sunbird/sunbird-learning-platform/blob/00ec4cc965a21145d65509e913961627a6d3f6fc/ansible/inventory/env/group\_vars/all.yml#L127) and [services](https://github.com/project-sunbird/sunbird-devops/blob/cc90889f2d13c4385a1cef0bfefbeec30e71406e/ansible/roles/stack-sunbird/defaults/main.yml#L1052)

```
cloudstorage_relative_path_prefix_content: "CONTENT_STORAGE_BASE_PATH"
cloudstorage_relative_path_prefix_dial: "DIAL_STORAGE_BASE_PATH"
cloudstorage_metadata_list: '["appIcon", "artifactUrl", "posterImage", "previewUrl", "thumbnail", "assetsMap", "certTemplate", "itemSetPreviewUrl", "grayScaleAppIcon", "sourceURL", "variants", "downloadUrl", "streamingUrl", "toc_url", "data", "question", "solutions", "editorState", "media", "pdfUrl", "transcripts"]'
```

Please define below variables

```
cloudstorage_replace_absolute_path: 'true'
cloudstorage_base_path: "https://sunbirddevbbpublic.blob.core.windows.net"
valid_cloudstorage_base_urls: '["https://sunbirddevbbpublic.blob.core.windows.net"]'
```

#### <mark style="color:red;">Deprecated variables</mark>

* <mark style="color:red;">sunbird\_cloud\_storage\_type</mark>
* <mark style="color:red;">sunbird\_public\_storage\_account\_name</mark>
* <mark style="color:red;">sunbird\_public\_storage\_account\_key</mark>
* <mark style="color:red;">azure\_public\_container</mark>
* <mark style="color:red;">sunbird\_content\_azure\_storage\_container</mark>

<table><thead><tr><th width="144">Component</th><th width="130">Build Job</th><th width="109">Build Tag</th><th width="135">Deploy Job</th><th width="127">Deployment Tag</th><th width="270">Comment</th></tr></thead><tbody><tr><td>Schema upload</td><td>NA</td><td>NA</td><td>Deploy/Kubernetes/UploadSchema</td><td><a href="https://github.com/project-sunbird/knowledge-platform/tree/release-5.2.0_RC5">release-5.2.0_RC5</a></td><td>Deploy this before deploying the service and flink-jobs.</td></tr><tr><td>Kafka setup</td><td>NA</td><td>NA</td><td>Deploy/KnowledgePlatform/KafkaSetup</td><td><a href="https://github.com/project-sunbird/sunbird-learning-platform/tree/release-5.2.0_RC8">release-5.2.0_RC8</a></td><td>Deploy this before deploying flink-jobs.</td></tr><tr><td>Sync Tool</td><td>Build/KnowledgePlatform/SyncTool</td><td><a href="https://github.com/project-sunbird/sunbird-learning-platform/tree/release-5.2.0_RC9">release-5.2.0_RC9</a></td><td>NA</td><td>NA</td><td><strong>migratecspdata</strong> - Add this command to the command list in the Deploy/KnowledgePlatform/Neo4jElasticSearchSyncTool Jenkins job.</td></tr><tr><td>Knowledge-platform</td><td><p>Build/Core/Content</p><p></p><p>Build/Core/Taxonomy</p></td><td><a href="https://github.com/project-sunbird/knowledge-platform/tree/release-5.2.0_RC5">release-5.2.0_RC5</a></td><td><p>Deploy/Kubernetes/Content</p><p></p><p>Deploy/Kubernetes/Taxonomy</p></td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-5.1.0_RC4">release-5.1.0_RC4</a></td><td>Build and deploy the content-service and taxonomy-service. Please find the configuration changes <a href="https://knowlg.sunbird.org/use/release-notes/release-5.2.0-ongoing#configurations">here</a>.</td></tr><tr><td>Sunbird-learning-service</td><td>Build/KnowledgePlatform/Learning</td><td><a href="https://github.com/project-sunbird/sunbird-learning-platform/tree/release-5.2.0_RC9">release-5.2.0_RC9</a></td><td>Deploy/KnowledgePlatform/Learning</td><td><a href="https://github.com/project-sunbird/sunbird-learning-platform/tree/release-5.2.0_RC9">release-5.2.0_RC9</a></td><td></td></tr><tr><td>dial-service</td><td>Build/Core/Dial</td><td><a href="https://github.com/project-sunbird/sunbird-dial-service/tree/release-5.2.0_RC1">release-5.2.0_RC1</a></td><td>Deploy/Kubernetes/Dial</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-5.1.0_RC4">release-5.1.0_RC4</a></td><td></td></tr><tr><td>Onboard APIs</td><td>NA</td><td>NA</td><td>Deploy/Kubernetes/OnboardAPIs</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-5.1.0_RC4">release-5.1.0_RC4</a></td><td></td></tr><tr><td>Knowledge-mw-service</td><td>Build/Core/KnowledgeMW</td><td><a href="https://github.com/project-sunbird/knowledge-mw-service/tree/release-5.2.0_RC1">release-5.2.0_RC1</a></td><td>Deploy/Kubernetes/KnowledgeMW</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-5.1.0_RC4">release-5.1.0_RC4</a></td><td></td></tr><tr><td>Knowledge-platform-jobs</td><td>Build/KnowledgePlatform/FlinkJobs</td><td><a href="https://github.com/project-sunbird/knowledge-platform-jobs/tree/release-5.2.0_RC11">release-5.2.0_RC11</a></td><td>Deploy/KnowledgePlatform/FlinkJobs</td><td><a href="https://github.com/project-sunbird/sunbird-learning-platform/tree/release-5.2.0_RC9">release-5.2.0_RC9</a></td><td><p>Add the below job list to the <em>job_names_to_deploy</em> list in the Deploy/KnowledgePlatform/FlinkJobs jenkins job</p><p><strong>csp-migrator,</strong> </p><p><strong>live-node-publisher,</strong> </p><p><strong>live-video-stream-generator,</strong> </p><p><strong>cassandra-data-migration</strong> </p><p></p><p>Deploy the </p><p><strong>assessment-enrichment</strong>, </p><p><strong>content-publish</strong>, </p><p><strong>qrcode-image-generator</strong>, <strong>search-indexer</strong>, </p><p><strong>csp-migrator,</strong> </p><p><strong>live-node-publisher,</strong> </p><p><strong>live-video-stream-generator,</strong> </p><p><strong>cassandra-data-migration</strong> flink jobs. </p><p></p><p>Please find the configuration changes <a href="https://knowlg.sunbird.org/use/release-notes/release-5.2.0-ongoing#configurations">here</a>. </p></td></tr><tr><td>Sunbird-Collection-Editor</td><td>NA</td><td><a href="https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor/v/5.2.4"><strong>v5.2.4</strong></a></td><td>NA</td><td>NA</td><td>NA</td></tr><tr><td>Sunbird-Content-Editor</td><td>Build/Plugins/ContentEditor</td><td><a href="https://github.com/project-sunbird/sunbird-content-editor/releases/tag/release-5.2.0_RC1"><strong>release-5.2.0_RC1</strong></a></td><td>Deploy/Plugins/ContentEditor</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-5.1.0_RC4">release-5.1.0_RC4</a></td><td>NA</td></tr><tr><td>Sunbird-Generic-Editor</td><td>Build/Plugins/GenericEditor</td><td><a href="https://github.com/project-sunbird/sunbird-generic-editor/releases/tag/release-5.2.0_RC1"><strong>release-5.2.0_RC1</strong></a></td><td>Deploy/Plugins/GenericEditor</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-5.1.0_RC4">release-5.1.0_RC4</a></td><td>NA</td></tr><tr><td>Sunbird-content-plugins</td><td>Build/Plugins/ContentPlugins</td><td><a href="https://github.com/project-sunbird/sunbird-content-plugins/releases/tag/release-5.2.0_RC1"><strong>release-5.2.0_RC1</strong></a></td><td>Deploy/Plugins/ContentPlugins</td><td><a href="https://github.com/project-sunbird/sunbird-devops/tree/release-5.1.0_RC4">release-5.1.0_RC4</a></td><td>NA</td></tr><tr><td>Sunbird-pdf-player</td><td>NA</td><td><a href="https://www.npmjs.com/package/@project-sunbird/sunbird-pdf-player-v9/v/5.2.1"><strong>v5.2.1</strong></a></td><td>NA</td><td>NA</td><td>Upgraded to Angular 14 (from Angular 9)</td></tr><tr><td>Sunbird-video-player</td><td>NA</td><td><a href="https://www.npmjs.com/package/@project-sunbird/sunbird-video-player-v9/v/5.2.3"><strong>v5.2.3</strong></a></td><td>NA</td><td>NA</td><td>Upgraded to Angular 12<br>(from Angular 9)</td></tr><tr><td>Sunbird-epub-player</td><td>NA</td><td><a href="https://www.npmjs.com/package/@project-sunbird/sunbird-epub-player-v9/v/5.2.1"><strong>v.5.2.1</strong></a></td><td>NA</td><td>NA</td><td>Upgraded to Angular 12<br>(from Angular 9)</td></tr></tbody></table>

### Configurations

<table><thead><tr><th width="136.33333333333331">Service/Jobs</th><th>Old Configuration</th><th>New Configuration</th></tr></thead><tbody><tr><td><a href="https://github.com/project-sunbird/sunbird-devops/blob/3ed1a90d8b8eed09666468194fcac2a655c05c96/ansible/roles/stack-sunbird/templates/content-service_application.conf#L485">content-service</a></td><td><p>cloud_storage_type: "{{ sunbird_cloud_storage_type }}" azure_storage_key: "{{ sunbird_public_storage_account_name }}" </p><p>azure_storage_secret: "{{ sunbird_public_storage_account_key }}" </p><p>azure_storage_container: "{{ sunbird_content_azure_storage_container }}"</p></td><td>cloud_storage_type: "{{ cloud_service_provider }}" cloud_storage_key: "{{ cloud_public_storage_accountname }}" cloud_storage_secret: "{{ cloud_public_storage_secret }}" cloud_storage_endpoint: "{{ cloud_public_storage_endpoint }}" cloud_storage_container: "{{ cloud_storage_content_bucketname }}"</td></tr><tr><td><a href="https://github.com/project-sunbird/sunbird-devops/blob/3ed1a90d8b8eed09666468194fcac2a655c05c96/ansible/roles/stack-sunbird/templates/content-service_application.conf#L643">content-service</a></td><td></td><td><p>cloudstorage { metadata.replace_absolute_path={{ cloudstorage_replace_absolute_path | default('false') }} relative_path_prefix={{ cloudstorage_relative_path_prefix_content }} </p><p>metadata.list={{ cloudstorage_metadata_list }} read_base_path="{{ cloudstorage_base_path }}" write_base_path={{ valid_cloudstorage_base_urls }} </p><p>}</p></td></tr><tr><td><a href="https://github.com/project-sunbird/sunbird-devops/blob/3ed1a90d8b8eed09666468194fcac2a655c05c96/ansible/roles/stack-sunbird/templates/taxonomy-service_application.conf#L368">taxonomy-service</a></td><td><p>cloud_storage_type: "azure" azure_storage_key: "{{ sunbird_public_storage_account_name }}" </p><p>azure_storage_secret: "{{ sunbird_public_storage_account_key }}" </p><p>azure_storage_container: "{{ sunbird_content_azure_storage_container }}"</p></td><td><p>cloud_storage_type: "{{ cloud_service_provider }}" cloud_storage_key: "{{ cloud_public_storage_accountname }}" </p><p>cloud_storage_secret: "{{ cloud_public_storage_secret }}" cloud_storage_endpoint: "{{ cloud_public_storage_endpoint }}" cloud_storage_container: "{{ cloud_storage_content_bucketname }}"</p></td></tr><tr><td><a href="https://github.com/project-sunbird/sunbird-devops/blob/3ed1a90d8b8eed09666468194fcac2a655c05c96/ansible/roles/stack-sunbird/templates/taxonomy-service_application.conf#L402">taxonomy-service</a></td><td></td><td><p>cloudstorage { metadata.replace_absolute_path={{ cloudstorage_replace_absolute_path | default('false') }} relative_path_prefix={{ cloudstorage_relative_path_prefix_content }} </p><p>metadata.list={{ cloudstorage_metadata_list }} read_base_path="{{ cloudstorage_base_path }}" write_base_path={{ valid_cloudstorage_base_urls }} </p><p>}</p></td></tr><tr><td><a href="https://github.com/project-sunbird/sunbird-learning-platform/blob/92604bb70357cea083a879f818a5c6b30bebbaeb/kubernetes/helm_charts/datapipeline_jobs/values.j2#L318">asset-enrichment flink job</a></td><td><p>cloud_storage_type="{{ cloud_store }}" </p><p>azure_storage_key="{{ sunbird_public_storage_account_name }}" </p><p>azure_storage_secret="{{ sunbird_public_storage_account_key }}" </p><p>azure_storage_container="{{ azure_public_container }}"</p></td><td>cloud_storage_type: "{{ cloud_service_provider }}" cloud_storage_key: "{{ cloud_public_storage_accountname }}" cloud_storage_secret: "{{ cloud_public_storage_secret }}" cloud_storage_endpoint: "{{ cloud_public_storage_endpoint }}" cloud_storage_container: "{{ cloud_storage_content_bucketname }}"</td></tr><tr><td><a href="https://github.com/project-sunbird/sunbird-learning-platform/blob/92604bb70357cea083a879f818a5c6b30bebbaeb/kubernetes/helm_charts/datapipeline_jobs/values.j2#L323">asset-enrichment flink job</a></td><td></td><td><p>cloudstorage { metadata.replace_absolute_path={{ cloudstorage_replace_absolute_path | default('false') }} relative_path_prefix={{ cloudstorage_relative_path_prefix_content }} </p><p>metadata.list={{ cloudstorage_metadata_list }} read_base_path="{{ cloudstorage_base_path }}" write_base_path={{ valid_cloudstorage_base_urls }} </p><p>}</p></td></tr><tr><td><a href="https://github.com/project-sunbird/sunbird-learning-platform/blob/92604bb70357cea083a879f818a5c6b30bebbaeb/kubernetes/helm_charts/datapipeline_jobs/values.j2#L622">content-publish flink job</a></td><td><p>cloud_storage_type="{{ cloud_store }}" </p><p>azure_storage_key="{{ sunbird_public_storage_account_name }}" </p><p>azure_storage_secret="{{ sunbird_public_storage_account_key }}" </p><p>azure_storage_container="{{ azure_public_container }}"</p></td><td>cloud_storage_type: "{{ cloud_service_provider }}" cloud_storage_key: "{{ cloud_public_storage_accountname }}" cloud_storage_secret: "{{ cloud_public_storage_secret }}" cloud_storage_endpoint: "{{ cloud_public_storage_endpoint }}" cloud_storage_container: "{{ cloud_storage_content_bucketname }}"</td></tr><tr><td><a href="https://github.com/project-sunbird/sunbird-learning-platform/blob/92604bb70357cea083a879f818a5c6b30bebbaeb/kubernetes/helm_charts/datapipeline_jobs/values.j2#L627">content-publish flink job</a></td><td></td><td><p>cloudstorage { metadata.replace_absolute_path={{ cloudstorage_replace_absolute_path | default('false') }} relative_path_prefix={{ cloudstorage_relative_path_prefix_content }} </p><p>metadata.list={{ cloudstorage_metadata_list }} read_base_path="{{ cloudstorage_base_path }}" write_base_path={{ valid_cloudstorage_base_urls }} </p><p>}</p></td></tr><tr><td><a href="https://github.com/project-sunbird/sunbird-learning-platform/blob/92604bb70357cea083a879f818a5c6b30bebbaeb/kubernetes/helm_charts/datapipeline_jobs/values.j2#L679">qrcode-image-generator flink job</a></td><td><p>cloud_storage_type="{{ cloud_store }}" </p><p>azure_storage_key="{{ sunbird_public_storage_account_name }}" </p><p>azure_storage_secret="{{ sunbird_public_storage_account_key }}" </p><p>azure_storage_container="{{ azure_public_container }}"</p></td><td><p>cloud_storage_type="{{ cloud_service_provider }}" cloud_storage_key="{{ cloud_public_storage_accountname }}" </p><p>cloud_storage_secret="{{ cloud_public_storage_secret }}" cloud_storage_container="{{ cloud_storage_dial_bucketname | default("dial") }}"</p></td></tr><tr><td><a href="https://github.com/project-sunbird/sunbird-learning-platform/blob/92604bb70357cea083a879f818a5c6b30bebbaeb/kubernetes/helm_charts/datapipeline_jobs/values.j2#L671">qrcode-image-generator flink job</a></td><td></td><td><p>cloudstorage { metadata.replace_absolute_path={{ cloudstorage_replace_absolute_path | default('false') }} relative_path_prefix={{ cloudstorage_relative_path_prefix_dial }} </p><p>metadata.list={{ cloudstorage_metadata_list }} read_base_path="{{ cloudstorage_base_path }}" write_base_path={{ valid_cloudstorage_base_urls }} </p><p>}</p></td></tr><tr><td><a href="https://github.com/project-sunbird/sunbird-learning-platform/blob/92604bb70357cea083a879f818a5c6b30bebbaeb/kubernetes/helm_charts/datapipeline_jobs/values.j2#L269">search-indexer flink job</a></td><td></td><td><p>cloudstorage { metadata.replace_absolute_path={{ cloudstorage_replace_absolute_path | default('false') }} relative_path_prefix={{ cloudstorage_relative_path_prefix_content }} </p><p>metadata.list={{ cloudstorage_metadata_list }} read_base_path="{{ cloudstorage_base_path }}" </p><p>}</p></td></tr></tbody></table>



**New Flink Jobs:**

* [csp-migrator](https://knowlg.sunbird.org/learn/product-and-developer-guide/knowlg-jobs/configuration#csp-migrator)
* [live-node-publisher](https://knowlg.sunbird.org/learn/product-and-developer-guide/knowlg-jobs/configuration#live-node-publisher)
* [live-video-stream-generator](https://knowlg.sunbird.org/learn/product-and-developer-guide/knowlg-jobs/configuration#live-video-stream-generator)
* [cassandra-data-migration](https://knowlg.sunbird.org/learn/product-and-developer-guide/knowlg-jobs/configuration#cassandra-data-migration)

### Migration process:

refer [data-migration.md](../../learn/product-and-developer-guide/other/data-migration.md "mention") page for more details.

### API Deprecation details:

refer [Deprecations Release-5.2.0](../deprecations/release-5.2.0.md) page for more details

### **Schema Deprecation properties:**

**relName** and **relTrackable** properties have been deprecated from the [relational metadata schema](https://github.com/project-sunbird/knowledge-platform/blob/release-5.2.0/schemas/relationalmetadata/1.0/schema.json).&#x20;

| Deprecated Properties | Alternate Properties |
| --------------------- | -------------------- |
| relName               | name                 |
| relTrackable          | optional             |

\
