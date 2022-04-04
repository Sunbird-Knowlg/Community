# Telemetry Events

Telemetry is a specification to instrument all the key events. Using this specification reference applications & services will generate telemetry events. For more info [here](https://telemetry.sunbird.org)

### List of Events

#### Start Event

&#x20;This method initializes capture of telemetric data associated to the start of user action and the following is the sample telemetry edata. For more info [here](https://telemetry.sunbird.org/learn/v3\_event\_details#start)

```
"edata": {
  "type": "content", // Defines edata type
  "mode": "play", // Defines edata mode
  "pageid": "", // Defines page id/number
  "duration": 7.47 // Defines duration of play
}
```

#### Interact Event

&#x20;This method is used to capture user interactions on a page. For example, search, click, preview, move, resize, configure and the following is the sample telemetry edata. For more info [here](https://telemetry.sunbird.org/learn/v3\_event\_details#interact)

```
"edata": {
  "type": "TOUCH", // Defines edata type
  "subtype": "", // Defines edata sub type
  "id": "gc_menuopen", // Defines edata id
  "pageid": "2" // Defines page id/number
}
```

#### Impression Event

&#x20;This method is used to capture telemetry for user visits to a specific page. and the following is the sample telemetry edata. For more info [here](https://telemetry.sunbird.org/learn/v3\_event\_details#impression)

```
"edata": {
  "type": "TOUCH", // Defines edata type
  "subtype": "", // Defines edata sub type
  "id": "gc_menuopen", // Defines edata id
  "pageid": "2" // Defines page id/number
}
```

#### End Event

&#x20;This method is used to capture closure after all the activities are completed. and the following is the sample telemetry edata. For more info [here](https://telemetry.sunbird.org/learn/v3\_event\_details#end)

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
