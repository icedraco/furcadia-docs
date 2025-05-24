# FS2 - Furcadia Shapes v2
> **DEPRECATION WARNING**
> 
> This format has been superseded by the [FOX](FOX.md) format!
> It may still be in use in order to maintain compatibility with old/legacy
> dreams.

## Overview
The FSH 2.002 (FS2) format is an enhanced version of the [FSH](FSH.md) format.
While it is capable of replacing the FSH format entirely, it was mostly geared
towards dreams and patches through the extra feature it provided:
  1. **Encryption** - FS2 files had a flag that specified whether the content
        in them was encrypted or not.
  2. **Replacement Object** - this extra field in each shape specified which
        shape in the original FSH file was being replaced by it. By providing
        only the objects that were modified (and not all of them) - this would
        optimize the size of patch files (and the bandwidth required to
        transfer them) in dreams where only some of the default graphics were
        changed.
  3. **No payload size array** - since payload size could be calculated via
        each shape's height and width, this further reduced the file size by
        removing redundant data from it.

## Format
### General Format
| Offset | Size | Type      | Description                                            |
| -----: | ---: | :-------- | ------------------------------------------------------ |
|      0 |    8 | char\[8]  | `FSH2.002` - FS2 magic number                          |
|      8 |    4 | uint32    | N: amount of shapes in this file (do not exceed 16bit) |
|     12 |    4 | uint32    | Flags: `0x01000000` - payload is encrypted (DRM bit)   |
|     16 |    * | Shape\[N] | Shapes                                                 |

### Shape
| Offset | Size | Type        | Description                                      |
| -----: | ---: | ----------- | ------------------------------------------------ |
|      0 |    1 | uint8       | W: shape width                                   |
|      1 |    1 | uint8       | H: shape height                                  |
|      2 |    1 | int8        | X Offset (signed!)                               |
|      3 |    1 | int8        | Y Offset (signed!)                               |
|      4 |    2 | uint16      | Replacement FSH object index                     |
|      6 |  W×H | byte\[W\*H] | Payload, indexed (color 0-255; 1 byte per pixel) |

* The payload is image data written in Furcadia palette; 1 byte per pixel.
* The payload will be encrypted (if encryption flag in the main header is set).
  If encrypted, the payload will be of the same size!
