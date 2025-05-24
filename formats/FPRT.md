---
classification: public
---

# FPRT - Furcadia Portrait Data
## Overview
FPRT is a "wrapper" format around some form of image that provides additional
properties that describes this image as a Furcadia portrait.

## Format
| Offset | Size | Description                               |
| -----: | ---: | ----------------------------------------- |
|      0 |    6 | `FPRT01` - FPRT magic number              |
|      6 |    1 | W (portrait width); normally 90, or 0x5F  |
|      7 |    1 | H (Portrait height); normally 90, or 0x5F |
|      8 |    1 | Flags: `0x01` - remappable portrait       |
|      9 |  W×H | Payload ([[FSH]] encoded via XOR255+LZW)  |

* Payload is normally an [FSH](FSH.md) file with 1 shape in it (the portrait)
* When receiving a portrait from the file server, the data is stored using
  XOR255+LZW encoding!
* Data inside the portrait cache may already be decoded (i.e., no XOR255+LZW)
