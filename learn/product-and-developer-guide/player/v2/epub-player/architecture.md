# Architecture

![](<../../../../../.gitbook/assets/Content  player Achitecture-PDF player-Epub player 2.drawio (3).png>)

**Common Service Lib:**

This is used for generating the telemetry from the player as a utility dependency library.

****

**Sunbird Player SDK:**

SDK contains common components used by all the V2 players to make it consistent and reusable across players, It contains Start, End Page components along with Navigation and Side menu components



**EPub JS:**

Epub js dependency library is used for rendering the epub files and it helps in the navigation of the epub file. Refer [here](https://github.com/futurepress/epub.js/) for more details.
