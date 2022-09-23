# latest

### <mark style="color:blue;">5.0.0</mark> (08-08-2022)



<mark style="color:red;">**Hot-fix: To be released**</mark>

<mark style="color:red;">**Communications Service Provider(CSP) changes: All the services should be cloud agnostic**</mark>

| Component                            | Tag                                                                                                                     |
| ------------------------------------ | ----------------------------------------------------------------------------------------------------------------------- |
| DIAL Service                         | [**release-5.0.0\_RC1**](https://github.com/project-sunbird/sunbird-dial-service/releases/tag/release-5.0.0\_RC1)       |
| DIAL Context related Flink jobs      | [**release-5.0.0\_RC1**](https://github.com/project-sunbird/knowledge-platform-jobs/releases/tag/release-5.0.0\_RC1)    |
| Content video player                 | ****[**v5.0.4**](https://www.npmjs.com/package/@project-sunbird/sunbird-video-player-v9/v/5.0.4)****                    |
| **Hot-FIx: CSP changes**             |                                                                                                                         |
| Sunbird-Collection-Editor            | [**v5.0.7**](https://www.npmjs.com/package/@project-sunbird/sunbird-collection-editor-v9/v/5.0.7)****                   |
| Sunbird-Content-Editor               | [**release-5.0.0\_RC3** ](https://github.com/project-sunbird/sunbird-content-editor/releases/tag/release-5.0.0\_RC3)    |
| Sunbird-Generic-Editor               | [**release-5.0.0\_RC3** ](https://github.com/project-sunbird/sunbird-generic-editor/releases/tag/release-5.0.0\_RC3)    |
| Sunbird-content-plugins              | [**release-5.0.0\_RC1** ](https://github.com/project-sunbird/sunbird-content-plugins/releases/tag/release-5.0.0\_RC1)   |
| Knowledge-platform (Content Service) | ****[**release-5.0.0\_RC1**](https://github.com/project-sunbird/knowledge-platform/releases/tag/release-5.0.0\_RC1)**** |
| Knowledge-platform-jobs              | TBD                                                                                                                     |
|                                      |                                                                                                                         |

#### **Features**

* Knowlg portal - Version 1 : [https://dev.knowlg.sunbird.org/](https://dev.knowlg.sunbird.org/) [#SB-28301](https://project-sunbird.atlassian.net/browse/SB-28301)
* Interactive Video - Online Playback [#SB-30516](https://project-sunbird.atlassian.net/browse/SB-30516) (Sign-off pending)
* Content service to update the DIAL context [#SB-30118](https://project-sunbird.atlassian.net/browse/SB-30118)
* Content - DIAL Reserve API refactoring #[SB-28316](https://project-sunbird.atlassian.net/browse/SB-28316)
* Collection Dialcode Link API Refactor LP to KP #[SB-30154](https://project-sunbird.atlassian.net/browse/SB-30154)

#### **Bug Fixes**

[Unable to edit the book - Blank Screen is coming](https://project-sunbird.atlassian.net/browse/SB-30307)

[Content imported from sourcing to consumption should not be linked to collection if it is not published](https://project-sunbird.atlassian.net/browse/SB-30566)

[Issue in collection Publish resulting deleted TBU coming in QR code scan/search](https://project-sunbird.atlassian.net/browse/SB-30573)

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
| enableDIALContextUpdate | Used to sepcify if the DIAL code context update data is to be computed using the linked/de-linked Dial codes of the content/collection. |

**post-publish-processor:**

```
dialcode.context.topic = {{ env_name }}.dialcode.context.job.request
```
