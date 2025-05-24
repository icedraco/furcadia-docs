---
classification: public
---

# MAP - Furcadia Map
## Overview
MAP files contain all the data about the dream’s initial look and settings:
arrangement of objects, floors and walls within the dream, the patch it is
going to use, how big the dream is, what features are enabled/disabled, etc.

## Format
This file has a hybrid structure: it has a plain text header and a binary
payload!

### Header
```
MAP V01.30 Furcadia    <- File header & version
height=37              <- Property
width=24               <- Property
revision=2288          <- Property
patcht=1               <- Property
BODY                   <- Body header (binary data comes after the 0x0a)
(BINARY DATA)
```
Each line (including the BODY line) ends with a single `\n` (0x0a) character.

#### Properties
The following properties can be set on a dream as of version `01.30`:

| Property         |  Type  | Description                                                                            |
| ---------------- | :----: | -------------------------------------------------------------------------------------- |
| height           |  int   | Dream height                                                                           |
| width            |  int   | Dream width (real width and not doubled)                                               |
| revision         |  int   | Revision of this dream file (incremented every time you save)                          |
| patcht           |  int   | Patch type: 0 = Default, 1 = Custom, 2 = From Server (unused)                          |
| patchs           | string | Patch source: relative path to the target patch or empty string if default             |
| name             | string | Dream name (appears under the uploader name on the portal)                             |
| allowjs          |  int   | Allow Join/Summon next to the summoner? (1 = Summon anywhere, 0 = Start of dream only) |
| allowlf          |  int   | Allow Lead/Follow in the dream? (1 = Yes, 0 = No)                                      |
| allowfurl        |  int   | Allow access via DreamURLs? (1 = Yes, 0 = No)                                          |
| swearfilter      |  int   | Enable vulgarity filter in dream? (1 = Yes, 0 = No)                                    |
| nowho            |  int   | Should all player names in dream be listed in (\`who/F4)? (1 = Yes, 0 = No)            |
| forcesittable    |  int   | Allow sitting only on sittable objects? (1 = Yes,  0 = Can sit anywhere)               |
| allowshouts      |  int   | Allow shouts inside the dream? (1 = Yes, 0 = No)                                       |
| rating           | string | Maturity rating/standard of the dream (see below)                                      |
| allowlarge       |  int   | Enable "Dream Package" features? (1 = Yes, 0 = No)                                     |
| notab            |  int   | Prevent the use of TAB key to show nearby names? (1 = Yes, 0 = No)                     |
| nonovelty        |  int   | Prevent use of seasonal avatars inside the dream? (1 = Yes, 0 = No)                    |
| parentalcontrols |  int   | Enforce parental controls in the dream? (1 = Yes, 0 = No)                              |
| noload           |  int   | Prevent loading of map in the Dream Editor? (1 = Yes, 0 = No)                          |
| encoded          |  int   | Is the dream data encoded/encrypted? (1 = Yes, 0 = No)                                 |

> **Note**
> The `noload` and `encoded` flags are normally present in encrypted dreams.
> Dreams without encryption in them don't have either of these properties.

#### Dream Ratings
Available dream standard strings in the MAP files:
- **Everyone 8+**
- **Teen+**
- **Mature 16+**
- **Adult 18+**
- **Adults Only**
- **AOClean**

See [Furcadia Dream Standards](http://www.furcadia.com/standards/) for more
info on each of these.

-------------------------------------------------------------------------------

### Body
The body of a MAP file consists of multiple layers (i.e., arrays) of items,
each of which defines which object is located at each of the coordinates in the
dream when it first initializes. The objects in each layer go in a
"top-down -> left-to-right" fashion: (0,0) ; (0,1) ; (0,2) ; … ; (2,0) ; (2,1) ; …

#### Layers (in order)
| Type    | Type          |
| ------- | ------------- |
| Floors  | uint16\[W\*H] |
| Objects | uint16\[W\*H] |
| Walls   | (see below)   |
| Regions | uint16\[W\*H] |
| Effects | uint16\[W\*H] |

##### Walls
The walls are ordered in such a way as to have a row of North-Western walls and
then a row of North-Eastern walls for the same tile:
* NW: 0,0 ; 0,1 ; … ; 0,24
* NE: 0,0 ; 0,1 ; … ; 0,24
* NW: 2,0 ; 2,1 ; … ; 2,24
* NE: 2,0 ; 2,1 ; … ; 2,24

Another way of seeing it is to split each tile in half, where the left half is
an even X coordinate and the right half is an odd X coordinate. Then, we can
see it as sequence of walls going the following way: 0,0 ; 0,1 ; … ; 1,0 ; 1,1; …
