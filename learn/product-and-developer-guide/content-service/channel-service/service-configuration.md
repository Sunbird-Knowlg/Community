# Configuration

Channel service file configuration is available at [https://github.com/project-sunbird/sunbird-devops/blob/master/ansible/roles/stack-sunbird/templates/content-service\_application.conf](https://github.com/project-sunbird/sunbird-devops/blob/master/ansible/roles/stack-sunbird/templates/content-service\_application.conf)

| Variable                                | Purpose                                                                                                                                                                                            |
| --------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| channel.fetch.suggested\_frameworks     | <p>Enable Suggested Frameworks in Get Channel API.<br><em>Default Value: true</em></p>                                                                                                             |
| channel.content.primarycategories       | List of content primary categories (contentPrimaryCategories attribute) to be displayed during a channel read. _If not configured, it will be empty List._                                         |
| channel.collection.primarycategories    | List of content primary categories (collectionPrimaryCategories attribute) to be displayed during a channel read. _If not configured, it will be empty List._                                      |
| channel.asset.primarycategories         | List of content primary categories (assetPrimaryCategories attribute) to be displayed during a channel read. _If not configured, it will be empty List._                                           |
| channel.content.additionalcategories    | List of content primary categories (contentAdditionalCategories attribute) to be displayed during a channel read. _If not configured, it will be empty List._                                      |
| channel.collection.additionalcategories | List of content primary categories (collectionAdditionalCategories attribute) to be displayed during a channel read. _If not configured, it will be empty List._                                   |
| channel.asset.additionalcategories      | List of content primary categories (assetAdditionalCategories attribute) to be displayed during a channel read. _If not configured, it will be empty List._                                        |
| composite.search.url                    | Composite search service domain URL. _(Example: https://dev.sunbirded.org/action/composite/v3/search)_                                                                                             |
| platform.language.codes                 | List of language codes allowed in 'translations' as part of request body in Channel create and update API. _If not configured, 'translations' cannot be passed during Channel create and update ._ |
|                                         |                                                                                                                                                                                                    |