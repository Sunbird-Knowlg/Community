# APIs

### [Composite Search API](https://documenter.getpostman.com/view/25463377/2s8ZDa3MP7)

The Composite Search API is used for search and discovery of assets/objects created on the system. This service includes only one API.

Kindly use the following link to access the API documentation.

[Search API](https://documenter.getpostman.com/view/25463377/2s8ZDa3MP7)

#### **API Search Filter Operators:**

Filters are by default searched based on equals match, that is case insensitive but the request can specify other operators to search against the fields. These are as follows:

**String fields:**

* Default - String match, contains case insensitive
* startsWith - String match, starts with
* endsWith - String match, ends with
* contains - contains match
* value - contains match
* Array - Exact match with any of the given values

**Number fields:**

* Default - Equals
* \>= - Greater than or equals
* \> - Greater than
* <= - Less than or equals
* < - Less than
* Array - Exact match with any of the given values

