---
description: >-
  As the name indcates, there are multiple editors to create specific type of
  contents.
---

# Editors

Sunbird houses a wide variety of content. Users can create content on Sunbird or upload content that is created offline.

As the name indicates, there are multiple editors to create a specific type of content.

| Editor                                                                            | Type                             | Mime types                                                                                                                       | Git Repo                                                                          |
| --------------------------------------------------------------------------------- | -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| [Interactive Editor](https://github.com/project-sunbird/sunbird-content-editor)   | Resource                         | ECML                                                                                                                             | [Interactive Editor](https://github.com/project-sunbird/sunbird-content-editor)   |
| [File Upload Editor](https://github.com/project-sunbird/sunbird-generic-editor)   | Content/Resource (as a file/URL) | <p>Non ECML Contents</p><ul><li>PDF</li><li>Video (MP4, YouTube)</li><li><p>HTML (HTML, H5p)</p><ul><li>EPUB</li></ul></li></ul> | [File Upload Editor](https://github.com/project-sunbird/sunbird-generic-editor)   |
| [Collection Editor](https://github.com/project-sunbird/sunbird-collection-editor) | Collection                       | <ul><li>Collection</li><li>Textbook</li><li>Course</li></ul>                                                                     | [Collection Editor](https://github.com/project-sunbird/sunbird-collection-editor) |

![](<../../../.gitbook/assets/Screenshot from 2021-11-24 14-52-26.png>)

### Git Repo:

Content Plugins repo is the common placeholder for all the plugins. Each editor will be configured with specific plugins while building the project.

#### Content-Plugins

{% embed url="https://github.com/project-sunbird/sunbird-content-plugins" %}
Content-Plugins
{% endembed %}

#### Content Editor:

{% embed url="https://github.com/project-sunbird/sunbird-content-editor" %}
Content-Editor
{% endembed %}

#### Collection Editor: Multilevel hierarchy contents like Book, Course, Collection, etc.

{% embed url="https://github.com/project-sunbird/sunbird-collection-editor" %}
Collection-Editor
{% endembed %}

#### Generic Editor: File upload contents to create

{% embed url="https://github.com/project-sunbird/sunbird-Generic-editor" %}
