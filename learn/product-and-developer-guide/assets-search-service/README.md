# Search Service

The **search service** is designed to enable users to efficiently search and explore assets on the platform. The primary API for this purpose is the Composite search API, which provides a unified way to fetch various types of objects within the application. These objects include 'Content', 'ContentImage', 'Collection', 'CollectionImage', 'QuestionSet', 'QuestionSetImage', 'Asset', 'Channel', 'Framework', 'ObjectCategory', 'ObjectCategoryDefinition', 'License', 'Question', and more.

Users have the flexibility to apply filters based on any attribute of the [object model](https://github.com/Sunbird-Knowlg/knowledge-platform/tree/master/schemas). This means that they can narrow down their search results by specifying specific criteria, such as title, category, author, date, or any other relevant attribute associated with the objects.

By default, the Composite search API returns objects that have a 'status' of "Live" and a 'visibility' of "default". These defaults ensure that the initial search results are relevant and align with the platform's standard display settings.

It's important to note that the default result 'limit' is set to 100, meaning that the API will return up to 100 matching objects in a single response. If more results are needed, users may consider pagination or adjusting the limit accordingly.
