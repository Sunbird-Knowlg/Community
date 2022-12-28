---
description: >-
  Documentation about list of APIs deprecated or to be deprecated and their
  corresponding new/alternative APIs available.
---

# Release-5.2.0

### APIs

| Deprecated API                                               | Alternate API                                                                                                                    | Remarks                                                                                   |
| ------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| \{{host\}}/api/content/v1/publish/\{{content\_id\}}          | \{{host\}}/api/content/v2/publish/\{{content\_id\}}, \{{host\}}/api/collection/v1/publish/\{{collection_\__id\}}                 | New/Alternate APIs introduced are to be used based on the objectType (Content/Collection) |
| \{{host\}}/api/content/v1/unlisted/publish/\{{content\_id\}} | {host\}}/api/content/v2/unlisted/publish/\{{content\_id\}}, \{{host\}}/api/collection/v1/unlisted/publish/\{{collection_\__id\}} | New/Alternate APIs introduced are to be used based on the objectType (Content/Collection) |
|                                                              |                                                                                                                                  |                                                                                           |



| To be deprecated API                                   | Alternate API                                                                                                                    | Remarks                                                                                   |
| ------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| \{{host\}}/api/content/v1/create                       | \{{host\}}/api/content/v2/create, \{{host\}}/api/collection/v1/create                                                            | New/Alternate APIs introduced are to be used based on the objectType (Content/Collection) |
| \{{host\}}/api/content/v1/update/\{{content\_id\}}     | \{{host\}}/api/content/v2/update/\{{content\_id\}}, {host\}}/api/collection/v1/update/\{{collection\_id\}}                       | New/Alternate APIs introduced are to be used based on the objectType (Content/Collection) |
| \{{host\}}/api/content/v1/read/\{{content\_id\}}       | \{{host\}}/api/content/v2/read/\{{content\_id\}}, \{{host\}}/api/collection/v1/read/\{{collection\_id\}}                         | New/Alternate APIs introduced are to be used based on the objectType (Content/Collection) |
| \{{host\}}/api/content/v1/upload/url/\{{content\_id\}} | \{{host\}}/api/content/v2/upload/url/\{{content\_id\}}                                                                           |                                                                                           |
| \{{host\}}/api/content/v1/upload/\{{content\_id\}}     | \{{host\}}/api/content/v2/upload/\{{content\_id\}}, \{{host\}}/api/collection/v1/copy/\{{collection\_id\}}                       | New/Alternate APIs introduced are to be used based on the objectType (Content/Collection) |
| \{{host\}}/api/content/v1/import                       | \{{host\}}/api/content/v2/import                                                                                                 |                                                                                           |
|                                                        | {host\}}/api/content/v2/discard/\{{content\_id\}}, \{{host\}}/api/collection/v1/discard/\{{collection\_id\}}                     | New/Alternate APIs introduced are to be used based on the objectType (Content/Collection) |
| \{{host\}}/api/content/v1/retire/\{{content\_id\}}     | \{{host\}}/api/content/v2/retire/\{{content\_id\}}, \{{host\}}/api/collection/v1/retire/\{{collection\_id\}}                     | New/Alternate APIs introduced are to be used based on the objectType (Content/Collection) |
| \{{host\}}/api/content/v1/review/\{{content\_id\}}     | \{{host\}}/api/content/v2/review/\{{content\_id\}}, \{{host\}}/api/collection/v1/review/\{{collection\_id\}}                     | New/Alternate APIs introduced are to be used based on the objectType (Content/Collection) |
| \{{host\}}/api/content/v1/reject/\{{content\_id\}}     | \{{host\}}/api/content/v2/reject/\{{content\_id\}}, \{{host\}}/api/collection/v1/reject/\{{collection\_id\}}                     | New/Alternate APIs introduced are to be used based on the objectType (Content/Collection) |
| \{{host\}}/api/dialcode/v1/content/link                | \{{host\}}/api/content/v2/dialcode/link, \{{host\}}/api/collection/v1/dialcode/link/\{{collection\_id\}}                         | New/Alternate APIs introduced are to be used based on the objectType (Content/Collection) |
| \{{host\}}/api/textbook/v1/toc/upload                  | \{{host\}}/api/collection/v1/import/\{{collection\_id\}}                                                                         |                                                                                           |
| \{{host\}}/api/textbook/v1/toc/download                | \{{host\}}/api/collection/v1/export/\{{collection\_id\}}                                                                         |                                                                                           |
| \{{host\}}/api/dialcode/v1/reserve                     | \{{host\}}/api/content/v2/dialcode/reserve/\{{content\_id\}}, \{{host\}}/api/collection/v1/dialcode/reserve/\{{collection\_id\}} | New/Alternate APIs introduced are to be used based on the objectType (Content/Collection) |
| \{{host\}}/api/dialcode/v1/release                     | \{{host\}}/api/content/v2/dialcode/release/\{{content\_id\}}, \{{host\}}/api/collection/v1/dialcode/release/\{{collection\_id\}} | New/Alternate APIs introduced are to be used based on the objectType (Content/Collection) |
|                                                        |                                                                                                                                  |                                                                                           |
