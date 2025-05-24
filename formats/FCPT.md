---
classification: public
---

# FCPT - Furcadia Cached Portrait Data
## Overview
FCPT is a format that wraps around a cached Furcadia portrait. It is normally
used inside [portraits.howl](../files/portraits.howl.md) as payload for every
cached portrait.

## Format
| Offset | Size | Type        | Description                |
| -----: | ---: | ----------- | -------------------------- |
|      0 |    4 | char\[4]    | `fcpt` - FCPT magic number |
|      4 |    4 | uint32      | Portrait ID                |
|      8 |    4 | uint32      | Portrait format            |
|     12 |    4 | u\|int32    | Reserved (always `0`)      |
|     16 |    4 | uint32      | H: Image height            |
|     20 |    4 | uint32      | W: Image width             |
|     24 |  W×H | byte\[W\*H] | Payload                    |

### Portrait Formats
| Identifier | Type              | Description     |
| ---------- | ----------------- | --------------- |
| 1          | FORMAT_8BIT       | FSH style       |
| 2          | FORMAT_BGR        | FOX style       |
| 3          | FORMAT_BGRA       | FOX style       |
| 7          | FORMAT_BGRA_RECOL | FOX 32bit remap |

See the **IMAGEDATA** section in [026_fox_format.pdf](../official/026_fox_format.pdf)
