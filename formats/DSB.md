---
classification: public
---

# DSB - DragonSpeak Binary Data
## Overview
DSB files contain the numeric data within `.ds` files in a binary form. The
numeric data can be the DS instructions seen in the `(#:#)` parentheses and the
numeric parameters provided for each such instruction.

DSB files do not contain text (e.g., messages printed to the user as a result
of an event). Instead - they contain a numeric index for each string, whereas
the strings themselves are stored in a [TXB](TXB.md) file.

## Format
### General Format
| Offset | Size | Description                                                         |
| -----: | ---: | ------------------------------------------------------------------- |
|      0 |   22 | DSB Header                                                          |
|     22 |    * | DragonSpeak lines/blocks                                            |

### DSB Header (22 bytes)
| Offset | Size | Type     | Description                                              |
| -----: | ---: | :------- | -------------------------------------------------------- |
|      0 |    5 | char\[5] | `DSB10` - DSB magic number                               |
|      5 |    4 | uint32   | Amount of DragonSpeak lines (blocks) in this file        |
|      9 |    4 | uint32   | Flags: `0x01000000` - data is encrypted                  |
|     13 |    9 | byte\[9] | Reserved (always 0)                                      |

### DragonSpeak Block (20 bytes)
| Offset | Size | Type     | Description                                              |
| -----: | ---: | :------- | -------------------------------------------------------- |
|      0 |    2 | uint16   | DS Line: Type (first element in the `(#:#)` part)        |
|      2 |    2 | uint16   | DS Line: Intruction (second element in the `(#:#)` part) |
|      4 |    2 | u\|int16 | Argument 1                                               |
|      6 |    2 | u\|int16 | Argument 2                                               |
|      8 |    2 | u\|int16 | Argument 3                                               |
|     10 |    2 | u\|int16 | Argument 4                                               |
|     12 |    2 | u\|int16 | Argument 5                                               |
|     14 |    2 | u\|int16 | Argument 6                                               |
|     16 |    2 | u\|int16 | Argument 7                                               |
|     18 |    2 | u\|int16 | Argument 8                                               |
