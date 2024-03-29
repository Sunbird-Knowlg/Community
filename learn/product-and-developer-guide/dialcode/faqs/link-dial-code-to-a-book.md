# Link DIAL Code to a Book

An educational institution XYZ, with over three thousand students, is spread across three locations. XYZ institute has decided to use Sunbird for its digital learning solution to provide more scalable and effective education to its students.

An energized book contains a QR code or a QR Code with a DIAL code in it. The students can scan the QR code using the Sunbird mobile app (Android 1.7.0 onwards) on their smartphone or other electronic devices like a laptop (using chrome browser) or a tablet. Scanning QR code provides a user the web links of related reading content. It helps the students to access the more content easily and understand the topics better.

### Intended Audience <a href="#intended-audience" id="intended-audience"></a>

A user with book creation access

### Overview <a href="#overview" id="overview"></a>

A book creator can tag various pages and topics with DIAL code as required. Using the DIAL codes, a book’s content can be converted into digital content. It provides the students easy access to content by transforming physical content material into digital content.

### Prerequisites <a href="#prerequisites" id="prerequisites"></a>

1.  &#x20;

    API Key to access Sunbird APIs. To create an API key refer [How to generate a  API key](../../player/telemetry-events/generate-api-keys.md)
2.  &#x20;

    Software that can make API calls like curl or [POSTMAN](https://www.getpostman.com/docs/v6/postman/api\_documentation/intro\_to\_api\_documentation)
3.  &#x20;

    The root organization and sub-organizations created and their **organsationId** and root organization’s **channel** readily available
4.  &#x20;

    The user account created in the root-organization and **userId** readily available
5.  &#x20;

    The created users are mapped to the organization and given appropriate rights and permisssions
6.  &#x20;

    Access to QR code and DIAL code. By default, any book creator gets access to link and unlink DIAL code
7.  &#x20;

    The DIAL code attribute must be configured in the Create Content API

### Taskflow <a href="#taskflow" id="taskflow"></a>

[**Content linking to QR code**](https://documenter.getpostman.com/view/25463377/2s935hRnae#02f47a1c-a56c-4bef-a4ad-51bb8cdb38ba): As a book creator or author, you can create content and associate the QR code and DIAL code to the content. This can be done via API and Sunbird User interface as well. This document describes how to link DIAL code to a book using APIs.

### Presteps to Follow to Before Linking a DIAL Code to a Book <a href="#presteps-to-follow-to-before-linking-a-dial-code-to-a-book" id="presteps-to-follow-to-before-linking-a-dial-code-to-a-book"></a>

Ensure to complete the following before linking DIAL code to a book:

a. [Create Publisher](https://documenter.getpostman.com/view/25463377/2s935hR7AM#81d8ee57-d567-4e62-829e-d3ee7c5671cf)

b. [Generate QR code](https://documenter.getpostman.com/view/25463377/2s935hR7AM#dc8b03d5-95e3-4314-a78a-ab61e9ebaa4e)

a. **Create Publisher**

This API is associated with creating a publisher

* The `dialcode/v1/publisher/create` endpoint executes the “Create Publisher” request based on parameters provided as metadata in the request body
* Required fields cannot be left null or empty

While providing values for the parameters in the request body of the API, it is essential to mention values as mentioned in the following table:

| HEADER PARAMETER | SAMPLE VALUE                                                           | DESCRIPTION                                                                                                                        | IS MANDATORY |
| ---------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| X-Channel-Id     | in.ekstep                                                              | It is a unique Id to identify the root organization to which the publisher has to be created                                       | Yes          |
| Content-Type     | Application/json Multipart/form-data Application/x-www-form-urlencoded | The media type of the resource                                                                                                     | Yes          |
| Authorization    | NA                                                                     | All User APIs require authorization. Raise a request to the administrator for the authorization key. Mention the received key here | Yes          |

**Request Body for create publisher API**

```
    {
      "request": {
          "publisher": {
              "identifier": "skpublisher",
              "name": "SK Publisher"
          }
      }
  }

```

**Response Body of Create Publisher API**

```
    {
    "id": "api.publisher.create",
    "ver": "1.0",
    "ts": "2018-10-04T07:12:47.729Z",
    "params": {
        "resmsgid": "e5b63e10-c7a4-11e8-bbd8-e58670bcc2b7",
        "msgid": "e51fca70-c7a4-11e8-ac7b-7b8f28c2d9c1",
        "status": "successful",
        "err": null,
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "identifier": "skpublisher"
    }
  }

```

b. Generate QR Code

This API is associated with generating DIAL code.

* The `/dialcode/v1/generate` endpoint executes the “Generate DIAL code” request based on parameters provided as metadata in the request body to be replaced by appropriate Id
* Required fields cannot be left null or empty

While providing values for the parameters in the request body of the API, it is essential to mention values as mentioned in the following table:

| HEADER PARAMETER | SAMPLE VALUE                                                           | DESCRIPTION                                                                                                                        | IS MANDATORY |
| ---------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| X-Channel-Id     | in.ekstep                                                              | It is a unique Id to identify the root organization to which the dialcodes have to be generated                                    | Yes          |
| Content-Type     | Application/json Multipart/form-data Application/x-www-form-urlencoded | The media type of the resource                                                                                                     | Yes          |
| Authorization    | NA                                                                     | All User APIs require authorization. Raise a request to the administrator for the authorization key. Mention the received key here | Yes          |

**Request Body of Generate DIAL Code API \*\* :**

```
    {
      "request": {
          "dialcodes": {
              "count": 2,
              "publisher": "skpublisher"
          }
      }
  }

```

**Response Body of Generate DIAL Code API**

```
    {
    "id": "api.dialcode.generate",
    "ver": "2.0",
    "ts": "2017-10-04T10:54:28.916",
    "params": {
        "resmsgid": "dcd64f40-c7c3-11e8-9bfa-fd2e5637008b",
        "msgid": "dc3af9a0-c6c3-11e8-9fb2-b710543e8512",
        "status": "successful",
        "err": null,
        "errmsg": null
    },
    "responseCode": "OK",
    "result": {
        "dialcodes": [
            "QP79LL",
            "WMHNYJ",
        ],
        "count": 2,
        "batchcode": "skpublisher.20181004T106427",
        "publisher": "skpublisher"
    }
  }

```

#### Link DIAL code to content using DIAL API <a href="#link-dial-code-to-content-using-dial-api" id="link-dial-code-to-content-using-dial-api"></a>

This API is associated with linking DIAL code to the content.

* The `/dialcode/v1/content/link` endpoint executes the “Link DIAL code” request based on parameters provided as metadata in the request body.
* Required fields cannot be left null or empty.
* As it is an updated request, whatever the list of dial codes API gets in the request body against any particular content Id or list of content Ids; the API updates the same as content metadata. If API does not get any value in dial code list, it delinks the content from all the existing dial-code by removing dial codes from content metadata.

While providing values for the parameters in the request body of the API, it is essential to mention values as mentioned in the following table:

| HEADER PARAMETER | SAMPLE VALUE                                                           | DESCRIPTION                                                                                                                        | IS MANDATORY |
| ---------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| X-Channel-Id     | in.ekstep                                                              | It is a unique Id to identify the root organization to which the user belongs                                                      | Yes          |
| Content-Type     | Application/json Multipart/form-data Application/x-www-form-urlencoded | The media type of the resource                                                                                                     | Yes          |
| Authorization    | NA                                                                     | All User APIs require authorization. Raise a request to the administrator for the authorization key. Mention the received key here | Yes          |

**Request Body Parameter**

| REQUEST BODY PARAMETER | SAMPLE VALUE     | DESCRIPTION                                                 | IS MANDATORY |
| ---------------------- | ---------------- | ----------------------------------------------------------- | ------------ |
| content.identifier     | “do\_3010101010” | List of content identifiers that are linked with dial codes | Yes          |
| content.dialcode       | “A6GHY”          | List of dial codes to which identifiers will be linked      | Yes          |

Link DIAL code API End point: `POST: /dialcode/v1/content/link`

**Request Body for linking DIAL code API**

```
    {
    "request": {
      "content":
        {
          "identifier": "do_3010101011",
          "dialcode": "3R3DSS"
        }
    }
  }

```

**Response Body for linking DIAL code API**

{ “id”: “sunbird.content.dialcode.link”, “ver”: “3.0”, “ts”: “2018-09-18T09:15:01ZZ” “, “params”: { “resmsgid”: “287298eb-ac54-4c9a-bf98-c0b1b1d4732e”, “msgid”: “null”, “err”: “null”, “status”: “successful”, “errmsg”: “null” }, “responseCode”: “OK”, “result”: { “node\_id”: “do\_3010101011”, “versionKey”: “1542625257776” } }

The [Link DIAL Code](https://documenter.getpostman.com/view/25463377/2s935hRnae#02f47a1c-a56c-4bef-a4ad-51bb8cdb38ba) (Digital Infrastructure for Augmented Learning) API resources are used for energizing the textbooks.

For more information, refer to [Content linking ](https://documenter.getpostman.com/view/25463377/2s935hRnae#02f47a1c-a56c-4bef-a4ad-51bb8cdb38ba)to QR code.

#### Consuming DIAL Code linked content <a href="#consuming-dial-code-linked-content" id="consuming-dial-code-linked-content"></a>

You can consume the content linked with DIAL code using mobile or website

**To consume the content using Sunbird mobile app**:

Scan the QR code using the Sunbird app installed on your mobile

**To consume the content using Sunbird portal:**

Go to [https://play.diksha.gov.in/dialpage/index.html](https://play.diksha.gov.in/dialpage/index.html)

Enter the DIAL code (the alphanumeric number) in the **Explore Content Using DIAL Code** field and click on the Search icon

### Concept Covered <a href="#concept-covered" id="concept-covered"></a>

**QR code:** It is a two-dimensional machine-readable barcode that is readable by smartphones and some other electronic devices. It consists of an array of black and white squares, which essentially encode web link as graphics. Users can scan QR code using a smartphone and some other electronic devices.

Discovery of digital content from physical textbooks is made possible by printing a QR code along with DIAL code on books and linking digital teaching and learning content to the QR codes placed in textbooks at a chapter and topic level.

**DIAL Code**: A DIAL code is the 6 digits alphanumeric code embedded with QR code.

**Energized book**: A book that is embedded with QR codes is called Energized book. The energized book serves as the anchor to the reader enabling them to have easy access to digital learning and training material.

#### Related Topic <a href="#related-topic" id="related-topic"></a>

[Update DIAL code](https://documenter.getpostman.com/view/25463377/2s935hR7AM#238b2e6f-3952-423d-8d63-c17d2fea995c)

[Update publisher](https://documenter.getpostman.com/view/25463377/2s935hR7AM#6ece54dd-d4c3-4a67-8b88-a1c0ee9ffb14)

[List DIAL Code](https://documenter.getpostman.com/view/25463377/2s935hR7AM#ef5f57bb-87e8-4dfd-8359-9c7c3c061635)
