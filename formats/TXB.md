---
classification: public
---

# TXB - DragonSpeak Text
## Overview
TXB files indexes the text strings used within DragonSpeak instructions
(e.g., messages that should be printed out to the user when they enter a dream,
or trigger some other event). These index numbers are referenced by a
[DSB](DSB.md) file of the same name.

TXB files are generated from a `.ds` file prior to uploading a dream to the
file server. They are kept on the game server and are normally NOT provided by
the file server back to the client, as the client has no real use for them -
the strings are printed/interpreted server-side only.

## Format
* This is a text file: it should be interpreted line-by-line
* Line delimiter: `\n` (0x0a)
* Index delimiter: `:` (0x3a)

### Structure
```
DST10
0:Master Socket kidnapped my kiwi!
1:String 1
2:String 2
...
N:String N
```
* The first line is the TXB magic number that identifies the format
* The rest of the lines are strings in the `<index>:<string>\n` form
* String index 0 ("Master Socket kidnapped my kiwi!") is a special string that
  is used by default when an index is unknown or corrupted/invalid
