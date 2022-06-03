# Telemetry Events

Telemetry is a specification to instrument all the key events. Using this specification reference applications & services will generate telemetry events. For more info [here](https://telemetry.sunbird.org/)

### Pdata

This describes the producer data of the event, and also it has the details about the producer id, version of the app, and instances of the component. below is the sample pdata.

```
    "pdata": {
      "id": "sunbird.portal", // Producer ID. For ex: For sunbird it would be "portal" or "genie"
      "ver": "3.2.12", // Version of the App
      "pid": "sunbird-portal.contentplayer" // Optional. In case the component is distributed, then which instance of that component
    },    
```

#### Below are the list of sample pdata configs for different clients

<table><thead><tr><th align="center">Client</th><th align="center">id</th><th align="center">pid</th><th align="center">ver</th><th data-type="number" data-hidden></th></tr></thead><tbody><tr><td align="center">Mobile</td><td align="center">sunbird.mobile</td><td align="center">sunbird.mobile.contentplayer</td><td align="center">&#x3C;mobile app version></td><td>null</td></tr><tr><td align="center">Portal</td><td align="center">sunbird.portal</td><td align="center">sunbird.portal.contentplayer</td><td align="center">&#x3C;portal version></td><td>null</td></tr><tr><td align="center">Desktop</td><td align="center">sunbird.desktop</td><td align="center">sunbird.desktop.contentplayer</td><td align="center">&#x3C;desktop app version></td><td>null</td></tr></tbody></table>

### List of Events

<details>

<summary>Start Event</summary>

This method initializes capture of telemetric data associated to the start of user action . Using the start event we can analysis time taken to start player.  For more info [here](https://docs.google.com/spreadsheets/d/1aOwWkff9qULGdk1Tv7F11P9b820J\_bU6V0S10Ww1-HI/edit#gid=2079230452)

&#x20;following is the sample telemetry edata

```
"edata": {
  "type": "content", // Defines edata type(app, session, editor, player, workflow, assessment)
  "mode": "play", // Mode of start.
  "pageid": "", // Page/Stage id where the start has happened.
  "duration": 7.47 // Time taken to initialize/start
}
```

</details>

<details>

<summary>Impression Event</summary>

This method is used to capture user interactions on a page. For example, search, click, preview, move, resize, configure and the following is the sample telemetry edata. For more info [here](https://docs.google.com/spreadsheets/d/1aOwWkff9qULGdk1Tv7F11P9b820J\_bU6V0S10Ww1-HI/edit#gid=2079230452)

```
"edata": {
  "type": "TOUCH", // Type of interaction TOUCH,DRAG,DROP,PINCH,ZOOM,SHAKE,ROTATE,SPEAK,LISTEN,WRITE,DRAW,START,ENDCHOOSE,ACTIVATE,SHOW,HIDE,SCROLL,HEARTBEAT,OTHER
  "subtype": "", // Additional types for a global type. For ex: for an audio the type is LISTEN and thesubtype can be one of PLAY,PAUSE,STOP,RESUME,END
  "id": "gc_menuopen", // Resource (button, screen, page, etc) id on which the interaction happened - use systemidentifiers when reporting device events
  "pageid": "2" // Stage or page id on which the event happened
}
```

</details>

<details>

<summary>interact Event</summary>

This method is used to capture telemetry for user visits to a specific page. and the following is the sample telemetry edata. For more info [here](https://docs.google.com/spreadsheets/d/1aOwWkff9qULGdk1Tv7F11P9b820J\_bU6V0S10Ww1-HI/edit#gid=2079230452)

```
"edata": {
  "type": "workflow", // Impression type (list, detail, view, edit, workflow, search)
  "subtype": "", // Additional subtype. "Paginate", "Scroll"
  "id": "gc_menuopen", // Defines edata id
  "pageid": "2" // Unique page id
  "uri": "", // Required. Relative URL of the content
}
```

</details>

<details>

<summary>End Event</summary>

This method is used to capture closure after all the activities are completed. it also capture the content played details like total number of pages , progress, duration of play and etc and the following is the sample telemetry edata. For more info [here](https://docs.google.com/spreadsheets/d/1aOwWkff9qULGdk1Tv7F11P9b820J\_bU6V0S10Ww1-HI/edit#gid=2079230452)

```
"edata": {
   "type": "content", // Defines edata type
   "mode": "play",   // Defines mode
   "pageid": "sunbird-player-Endpage", // Defines page id
    "summary": [
          {
            "progress": 22
          },
          {
            "totallength": 9
          },
          {
            "visitedlength": 2
          },
          {
            "visitedcontentend": false
          },
          {
            "totalseekedlength": 7
          },
          {
            "endpageseen": false
          }
        ],
    "duration": 11988.53 // Defines duration of play
}
```

</details>

<details>

<summary>Access Event</summary>

This method is used to capture user assessments that happen while playing content.For more info [here](https://docs.google.com/spreadsheets/d/1aOwWkff9qULGdk1Tv7F11P9b820J\_bU6V0S10Ww1-HI/edit#gid=2079230452)

</details>

<details>

<summary>Response Event</summary>

This API is used to log telemetry of user response. For example; Responded to assessments.For more info [here](https://docs.google.com/spreadsheets/d/1aOwWkff9qULGdk1Tv7F11P9b820J\_bU6V0S10Ww1-HI/edit#gid=2079230452)

</details>

### Sample Telemetry  Events

Below are the sample telemetry events  check more details about each value in the event [here](https://github.com/project-sunbird/sunbird-player-sdk/blob/master/docs/telemetry/SampleContentPlayerV2Instrumentation.csv)

<details>

<summary>START</summary>

```
{
  "eid": "START",
  "ets": 1649318545112,
  "ver": "3.0",
  "mid": "START:d733c45b87270477b1beb612dc7bda4c",
  "actor": {
    "id": "632995e29874caa57949ce954e6b5d4a",
    "type": "User"
  },
  "context": {
    "channel": "01268904781886259221",
    "pdata": {
      "id": "staging.sunbird.portal",
      "ver": "4.8.5",
      "pid": "sunbird-portal"
    },
    "env": "contentplayer",
    "sid": "35209e6a-d463-37c1-9672-6090ede5d245",
    "did": "632995e29874caa57949ce954e6b5d4a",
    "cdata": [
      {
        "id": "DH2JihRQhD9quRLkIUroNLfTA2rEQeDC",
        "type": "ContentSession"
      },
      {
        "id": "ChrI789hrOXvzCMn44U5nEQZn31Epg7o",
        "type": "PlaySession"
      },
      {
        "id": "2.0",
        "type": "PlayerVersion"
      }
    ],
    "rollup": {},
    "uid": "anonymous"
  },
  "object": {
    "id": "do_2132473634393948161725",
    "ver": "1",
    "type": "Content",
    "rollup": {}
  },
  "tags": [
    "01268904781886259221"
  ],
  "edata": {
    "type": "content",
    "mode": "play",
    "pageid": "",
    "duration": 5.35
  }
}
```

</details>

<details>

<summary>INTERACT</summary>

```
{
  "eid": "INTERACT", // Event id 
  "ets": 1646727758517, // Event time stamp
  "ver": "3.0", // Event Version 
  "mid": "INTERACT:e6cf5520a276294b068acfabd52f363a", // Message Id which is uniq
  "actor": { // User details 
    "id": "280d913d358428e24c92ed6b9e6d89a7",
    "type": "User"
  },
  "context": {
    "channel": "01268904781886259221", // Channel id
    "pdata": { 
      "id": "preprod.diksha.portal", // Producer ID.
      "ver": "4.7.0", // Version of the app
      "pid": "sunbird-portal.contentplayer" //Optional. In case the component is distributed, then which instance of that component
    },
    "env": "contentplayer",  // Defines the environment 
    "sid": "f7a8a672-9a3b-e83e-42a7-6131a553f65f", // User sessionid
    "did": "280d913d358428e24c92ed6b9e6d89a7", // Unique id to identify the device or browser
    "cdata": [ // Defines correlation data
      {
        "id": "fdaafa8413a27931dc01ff5a4cb3a0e2",
        "type": "ContentSession"
      },
      {
        "id": "7e20b101878957052b8cb9a9ec770ce7",
        "type": "PlaySession"
      }
    ],
    "rollup": { // Roll up data
      "l1": "01268904781886259221"
    }
  },
  "object": {
    "id": "do_2134417722515210241147", // Asset identifier
    "type": "Content", // Asset type
    "ver": "1",  // Asset version
    "rollup": {} // Roll up data
  },
  "tags": [ // Defines the tags data
    "01268904781886259221"
  ],
  "edata": {
    "type": "TOUCH", // Event data type
    "subtype": "", // Event sub data type
    "id": "gc_menuopen", // Defines the id
    "pageid": "2" // Defines the page id
  }
}
```

</details>

<details>

<summary>IMPRESSION</summary>

```
{
  "eid": "IMPRESSION",
  "ets": 1649320122499,
  "ver": "3.0",
  "mid": "IMPRESSION:ffe3a6f635a13f6810cd3c9979ca5529",
  "actor": {
    "id": "632995e29874caa57949ce954e6b5d4a",
    "type": "User"
  },
  "context": {
    "channel": "01268904781886259221",
    "pdata": {
      "id": "staging.sunbird.portal",
      "ver": "4.8.5",
      "pid": "sunbird-portal"
    },
    "env": "contentplayer",
    "sid": "35209e6a-d463-37c1-9672-6090ede5d245",
    "did": "632995e29874caa57949ce954e6b5d4a",
    "cdata": [
      {
        "id": "DH2JihRQhD9quRLkIUroNLfTA2rEQeDC",
        "type": "ContentSession"
      },
      {
        "id": "apTUc3ZpDycy5tm4C6mkhZkifeRA0aRa",
        "type": "PlaySession"
      },
      {
        "id": "2.0",
        "type": "PlayerVersion"
      }
    ],
    "rollup": {},
    "uid": "anonymous"
  },
  "object": {
    "id": "do_2132473634393948161725",
    "ver": "1",
    "type": "Content",
    "rollup": {}
  },
  "tags": [
    "01268904781886259221"
  ],
  "edata": {
    "type": "workflow",
    "subtype": "",
    "pageid": "3",
    "uri": ""
  }
}
```

</details>

<details>

<summary>END</summary>

```
{
  "eid": "END",
  "ets": 1649326236878,
  "ver": "3.0",
  "mid": "END:898f1e88610da17e3a12fd0a9a18d9c7",
  "actor": {
    "id": "90ee25617d93d2973ab012abf2854322",
    "type": "User"
  },
  "context": {
    "channel": "01268904781886259221",
    "pdata": {
      "id": "staging.sunbird.portal",
      "ver": "4.8.5",
      "pid": "sunbird-portal"
    },
    "env": "contentplayer",
    "sid": "cc9d525c-850d-ba69-3589-e4892408d2ff",
    "did": "90ee25617d93d2973ab012abf2854322",
    "cdata": [
      {
        "id": "1iPaJwSm9CZ642DJ4NPHwx9VXInhkMGm",
        "type": "ContentSession"
      },
      {
        "id": "rQVRoTYlITk6WBuQm0iQqB3G6zSv4Tm5",
        "type": "PlaySession"
      },
      {
        "id": "2.0",
        "type": "PlayerVersion"
      }
    ],
    "rollup": {
      "l1": "01268904781886259221"
    },
    "uid": "anonymous"
  },
  "object": {
    "id": "do_2134250082225192961958",
    "ver": "1",
    "type": "Content",
    "rollup": {
      "l1": "do_2134250082225192961958"
    }
  },
  "tags": [
    "01268904781886259221"
  ],
  "edata": {
    "type": "content",
    "mode": "play",
    "pageid": "sunbird-player-Endpage",
    "summary": [
      {
        "progress": 100
      },
      {
        "totallength": 137.56
      },
      {
        "visitedlength": 57.708
      },
      {
        "visitedcontentend": false
      },
      {
        "totalseekedlength": 39.583
      },
      {
        "endpageseen": true
      },
      {
        "score": 0
      }
    ],
    "duration": 58.61
  }
}
```

</details>

### Telemetry Instrumentation for V2 Players

Click [here](https://github.com/project-sunbird/sunbird-player-sdk/blob/master/docs/telemetry/ContentPlayerV2Instrumentation.csv) for telemetry details &#x20;
