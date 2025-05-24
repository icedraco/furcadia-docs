---
classification: public
---

# RCH2 - Furcadia Container / Archive
## Overview
Unlike [RCH](RCH.md), RCH2 format is used as a blob in the Furcadia Installer.
It contains all the Furcadia files with their designated (variable) paths.

It is possible to read and extract the files from within the RCH2 archive
inside a `furcsetup.exe` file without launching it, which can help with
installing Furcadia (or at least its assets) on non-Windows operating systems.

### Furcadia Installer Offsets
Different installer versions have the RCH2 blob at different offsets.
The following offsets are "of interest":

| Installer Version |     Offset |
| :---------------- | ---------: |
| furcsetup031c.exe | `0x198a00` |
| ???               | `0x09fa00` |
| ???               | `0x030000` |
| ???               | `0x02f000` |

If none of these offsets have the `RCH2.0` magic number, one can scan the
entire `.exe` file for it. It isn't hard - just relatively time-consuming...

## Format
### General Format (TODO)
> THE INFO HERE IS OF THE RCH FORMAT - UPDATE IT WHEN YOU RE-ACQUIRE RCH2

| Offset | Size | Type     | Description                              |
| -----: | ---: | :------- | :--------------------------------------- |
|      0 |    4 | char\[4] | `FR01` - RCH magic number                |
|      4 |    4 | uint32   | Container version                        |
|      8 |    4 | uint32   | Creation timestamp (always `0` - unused) |
|     12 |    4 | u\|int32 | Reserved (`0`)                           |
|     16 |    4 | u\|int32 | Reserved (`0`)                           |
|     20 |    4 | u\|int32 | Reserved (`0`)                           |
|     24 |    4 | u\|int32 | Reserved (`0`)                           |
|     28 |    * | File\[]  | File blocks                              |

### File Block (TODO)
> THE INFO HERE IS OF THE RCH FORMAT - UPDATE IT WHEN YOU RE-ACQUIRE RCH2

| Offset |  Size | Type         | Description                                                      |
| -----: | ----: | :----------- | :--------------------------------------------------------------- |
|      0 |     2 | char\[2]     | `FZ` - File Block magic number                                   |
|      2 |    40 | char\[40]    | Filename (NULL-padded)                                           |
|     42 |     4 | uint32       | File version (`1`)                                               |
|     46 |     4 | uint32       | Timestamp (always `0` - unused)                                  |
|     50 |     4 | uint32       | Payload size                                                     |
|     54 |     4 | uint32       | CRC32 checksum of the payload                                    |
|     58 |     4 | uint32       | Compression algorithm<br>(0 = XOR255+LZW, 1 = XOR255, 2 = BZip2) |
|     62 | pSize | byte\[pSize] | Payload                                                          |

## Source
Information about this format was obtained Artex via reverse-engineering and
guesstimation. As such, it is not privileged...
