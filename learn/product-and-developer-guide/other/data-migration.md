---
description: Replacing the absolute paths stored in the database with relative paths.
---

# Data Migration

This document details about the migration of below points

* Replace existing absolute paths in database with relative paths.
*   Migration of data while changing the CSP provider

    Example: Moving from Azure to AWS service provider.

#### Migration data

* Neo4J node data need to migrate
*   Cassandra data need to migrate

    This will impact for collections like Textbook, Course, ECML contents.
* DIAL code download URL
* ECAR generate
* Generating new video steaming(for new CSP provider)

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
