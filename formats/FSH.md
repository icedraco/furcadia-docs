# FSH - Furcadia Shapes
> **DEPRECATION WARNING**
>
> This format has been superseded by the [FS2](FS2.md) format, and later - by
> the [FOX](FOX.md) format! It may still be in use in order to maintain
> compatibility with old/legacy dreams.

## Overview
FSH files store all the graphical components of the client (GUI) including:
* dream graphics: floors, walls, objects, characters
* text graphics: specitags, description tags, emoji
* GUI elements: buttons and tabs
* portraits

The only graphics NOT stored by these files are:
* anything that requires more than 256x256 resolution
  (e.g., client GUI background)
* anything with a non-Furcadian color palette
  (e.g., non-remap JPG/PNG portraits)

Each FSH file may contain zero or more "shapes" (images), each with its own
properties on how it is to be rendered by the client.

## Format
### General Format
| Offset | Size | Type       | Description                               |
| -----: | ---: | :--------- | ----------------------------------------- |
|      0 |    2 | uint16     | N: amount of shapes in this file          |
|      2 |  N×2 | uint16\[N] | Payload size in bytes of each shape       |
|  2+N×2 |    * | Shape\[N]  | Shapes                                    |
|     -8 |    8 | char\[8]   | (optional) `FSH1.002` - FSH revision tail |

> Note: This file does not start with a magic number! It MAY end with a tail...

### Shape
| Offset | Size | Type        | Description                                      |
| -----: | ---: | ----------- | ------------------------------------------------ |
|      0 |    1 | uint8       | W: shape width                                   |
|      1 |    1 | uint8       | H: shape height                                  |
|      2 |    1 | int8        | X Offset (signed!)                               |
|      3 |    1 | int8        | Y Offset (signed!)                               |
|      4 |  W×H | byte\[W\*H] | Payload, indexed (color 0-255; 1 byte per pixel) |

The payload is image data written in Furcadia palette; 1 byte per pixel.
