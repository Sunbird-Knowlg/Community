# Release - 5.0.0

### <mark style="color:blue;">**Hot-fix:  5.0.3 (17-11-2022)**</mark>

<mark style="color:blue;">**Bugs:**</mark>

Null pointer exception while publishing collection [KN-609](https://project-sunbird.atlassian.net/browse/KN-609)

<table><thead><tr><th>Component</th><th>Service to be build</th><th width="190">Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Knowledge-platform-jobs</td><td>Build/KnowldgePlatform/Flinkjobs</td><td><a href="https://github.com/project-sunbird/knowledge-platform-jobs/commits/release-5.0.3_RC1"><strong>release-5.0.3_RC1</strong></a></td><td></td></tr></tbody></table>

### <mark style="color:blue;">**Hot-fix:  5.0.1 (29-09-2022)**</mark>

<mark style="color:blue;">**Bugs:**</mark>

Content imported from sourcing to consumption should not be linked to collection if it is not published [SB-31006](https://project-sunbird.atlassian.net/browse/SB-31006)

<table><thead><tr><th>Component</th><th>Service to be build</th><th width="174">Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Knowledge-platform-jobs</td><td>Build/KnowldgePlatform/Flinkjobs</td><td><a href="https://github.com/project-sunbird/knowledge-platform-jobs/tree/release-5.0.1_RC1"><strong>release-5.0.1_RC1</strong></a></td><td><a href="https://project-sunbird.atlassian.net/browse/SB-30566">SB-30566</a> patch reversal</td></tr></tbody></table>

### <mark style="color:blue;">5.0.0</mark> (08-08-2022)

<table><thead><tr><th width="284.5">Component</th><th>Service to be Build</th><th>Tag</th><th>Comment</th></tr></thead><tbody><tr><td>Kafka setup</td><td>Deploy/KnowledgePlatform/KafkaSetup</td><td><a href="https://github.com/project-sunbird/sunbird-learning-platform/tree/release-5.0.0_RC1"><strong>release-5.0.0_RC1</strong></a></td><td>Deploy this to add newly added topic for <strong>dialcode-context-updater</strong> job.</td></tr><tr><td>DIAL Service</td><td>Build/Core/Dial</td><td><a href="https://github.com/project-sunbird/sunbird-dial-service/releases/tag/release-5.0.0_RC1"><strong>release-5.0.0_RC1</strong></a></td><td></td></tr><tr><td>DIAL Context related Flink jobs</td><td>Build/KnowldgePlatform/Flinkjobs</td><td><a href="https://github.com/project-sunbird/knowledge-platform-jobs/releases/tag/release-5.0.0_RC1"><strong>release-5.0.0_RC1</strong></a></td><td><p>Deploy the <strong>content-publish,</strong></p><p><strong>post-publish-processor,</strong></p><p><strong>dialcode-context-updater</strong> job.</p></td></tr><tr><td>Content video player</td><td>NA</td><td><a href="https://www.npmjs.com/package/@project-sunbird/sunbird-video-player-v9/v/5.0.4"><strong>v5.0.4</strong></a></td><td></td></tr><tr><td><strong>Hot-FIx: CSP changes</strong></td><td></td><td></td><td></td></tr><tr><td>Sunbird-Collection-Editor</td><td>NA</td><td><a href="https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor-v9/v/5.0.7"><strong>v5.0.7</strong></a></td><td></td></tr><tr><td>Sunbird-Content-Editor</td><td>Build/Plugins/ContentEditor</td><td><a href="https://github.com/project-sunbird/sunbird-content-editor/releases/tag/release-5.0.0_RC3"><strong>release-5.0.0_RC3</strong> </a></td><td></td></tr><tr><td>Sunbird-Generic-Editor</td><td>Build/Plugins/GenericEditor</td><td><a href="https://github.com/project-sunbird/sunbird-generic-editor/releases/tag/release-5.0.0_RC3"><strong>release-5.0.0_RC3</strong> </a></td><td></td></tr><tr><td>Sunbird-content-plugins</td><td>Build/Plugins/ContentPlugins</td><td><a href="https://github.com/project-sunbird/sunbird-content-plugins/releases/tag/release-5.0.0_RC1"><strong>release-5.0.0_RC1</strong></a></td><td></td></tr><tr><td>Knowledge-platform</td><td>Build/Kubernetes/Content</td><td><a href="https://github.com/project-sunbird/knowledge-platform/releases/tag/release-5.0.0_RC1"><strong>release-5.0.0_RC1</strong></a></td><td></td></tr><tr><td>Knowledge-platform-jobs</td><td>Build/KnowldgePlatform/Flinkjobs</td><td><a href="https://github.com/project-sunbird/knowledge-platform-jobs/tree/release-5.0.0_RC2"><strong>release-5.0.0_RC</strong></a><strong>2</strong></td><td></td></tr></tbody></table>

#### **Features**

* Knowlg portal - Version 1 : [https://dev.knowlg.sunbird.org/](https://dev.knowlg.sunbird.org/) [#SB-28301](https://project-sunbird.atlassian.net/browse/SB-28301)
* Interactive Video - Online Playback [#SB-30516](https://project-sunbird.atlassian.net/browse/SB-30516) (Signed off)
* Content service to update the DIAL context [#](https://project-sunbird.atlassian.net/browse/SB-30118)[KN-285](https://project-sunbird.atlassian.net/browse/KN-285)
* Content - DIAL Reserve API refactoring #[SB-28316](https://project-sunbird.atlassian.net/browse/SB-28316)
* Collection Dialcode Link API Refactor LP to KP #[SB-30154](https://project-sunbird.atlassian.net/browse/SB-30154)
* Inclusion of SB vocabulary validation for extended vocabulory #[SB-30378](https://project-sunbird.atlassian.net/browse/SB-30378) (Note: this is a new feature for knowlg, adopter can only implement this feature and not adopt it)

#### **Bug Fixes**

[Unable to edit the book - Blank Screen is coming](https://project-sunbird.atlassian.net/browse/SB-30307) #[SB-30307](https://project-sunbird.atlassian.net/browse/SB-30307)

[Remove originField from content.nested.fields from content public config property](https://project-sunbird.atlassian.net/browse/SB-30560) #[SB-30560](https://project-sunbird.atlassian.net/browse/SB-30560)

[Issue in collection Publish resulting deleted TBU coming in QR code scan/search](https://project-sunbird.atlassian.net/browse/SB-30573) #[SB-30573](https://project-sunbird.atlassian.net/browse/SB-30573)

#### Documentations

* Adopters - How to setup DIAL context [https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/3214016513/Adoption+of+Sunbird+DIAL+Context](https://project-sunbird.atlassian.net/wiki/spaces/SBDES/pages/3214016513/Adoption+of+Sunbird+DIAL+Context)
* Postman DIAL Service APIs: [https://postman.com/knowlg-sunbird/workspace/dial/documentation/4214340-c506c361-8f86-45c3-999d-9e6ed7a2e28d](https://postman.com/knowlg-sunbird/workspace/dial/documentation/4214340-c506c361-8f86-45c3-999d-9e6ed7a2e28d)

#### Configurations

**DIAL service configuration:** [https://github.com/project-sunbird/sunbird-devops/blob/release-5.0.0/ansible/roles/stack-sunbird/templates/dial-service\_application.conf](https://github.com/project-sunbird/sunbird-devops/blob/release-5.0.0/ansible/roles/stack-sunbird/templates/dial-service\_application.conf)

| Variable          | Purpose                                                                                                                                                                                                                      |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| jsonld.basepath   | base path of the jsonld.type folder contents                                                                                                                                                                                 |
| jsonld.type       | 'folder name' containing jsonld schema vocabulary and context json files to be referred to.                                                                                                                                  |
| jsonld.localPath  | server directory to which the 'contextValidation.json' file is to be downloaded.                                                                                                                                             |
| jsonld.ttl        | file caching refresh time of 'contextValidation.json'                                                                                                                                                                        |
| jsonld.sb\_schema | Sunbird vocabulary, 'schema.jsonld' file path whose reference is to be validated in the custom 'context.json'. Mupltiple vocabulary file paths can be mentioned in order to verify if the custom context.json has extended   |
| dial\_id          | dial code URL to be returned in the dial code context during context read for '@id'                                                                                                                                          |
| dial\_type        | 'type' value to be shown during the dial code context read for '@type'.                                                                                                                                                      |

**Flink jobs configuration:** [https://github.com/project-sunbird/sunbird-learning-platform/blob/release-5.0.0/kubernetes/helm\_charts/datapipeline\_jobs/values.j2](https://github.com/project-sunbird/sunbird-learning-platform/blob/release-5.0.0/kubernetes/helm\_charts/datapipeline\_jobs/values.j2)

**dialcode-context-updater:** Refer to [https://knowlg.sunbird.org/learn/product-and-developer-guide/knowlg-jobs/configuration#dialcode-context-updater](https://knowlg.sunbird.org/learn/product-and-developer-guide/knowlg-jobs/configuration#dialcode-context-updater)&#x20;

**content-publish:**&#x20;

| Variable                | Description                                                                                                                             |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| enableDIALContextUpdate | Used to specify if the DIAL code context update data is to be computed using the linked/de-linked Dial codes of the content/collection. |

**post-publish-processor:**

```
dialcode.context.topic = {{ env_name }}.dialcode.context.job.request
```

**CSP configuration for edtors:**

| Name                          | Configuration                                                                                                                                                                                                                          |
| ----------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Sunbird-collection-editor** | [https://github.com/Sunbird-Ed/sunbird-collection-editor/blob/release-5.0.0/docs/CONFIGURATION.md#2-editor-context](https://github.com/Sunbird-Ed/sunbird-collection-editor/blob/release-5.0.0/docs/CONFIGURATION.md#2-editor-context) |
| **Sunbird-content-editor**    | [https://github.com/project-sunbird/sunbird-content-editor/tree/release-5.0.0#:\~:text=public%2Ddev/%22-,cloudStorage,-It%20is%20object](https://github.com/project-sunbird/sunbird-content-editor/tree/release-5.0.0)                 |
| **Sinbird-generic-editor**    | [https://github.com/Sunbird-Ed/sunbird-collection-editor/blob/release-5.0.0/docs/CONFIGURATION.md#2-editor-context](https://github.com/Sunbird-Ed/sunbird-collection-editor/blob/release-5.0.0/docs/CONFIGURATION.md#2-editor-context) |
