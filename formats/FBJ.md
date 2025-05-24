---
classification: public
---

# FBJ - Furcadia Object Properties
## Overview
FBJ file stores properties of every shape that exists in an
[FSH](FSH.md)/[FS2](FS2.md) file with the same name. This information comes
separate from the graphics of each object because the game server doesn't need
to know what the object looks like, but it *does* need to know if the object
is walkable/sittable/etc.

## Format
### General Format
| Offset |     Size | Description                                               |
| -----: | -------: | --------------------------------------------------------- |
|      0 |        8 | FBJ Header                                                |
|      8 | N×{1..3} | Shape property blocks                                     |

### FBJ Header (8 bytes)
| Offset | Size | Description                                                   |
| -----: | ---: | ------------------------------------------------------------- |
|      0 |    4 | `FO01` - FBJ magic number                                     |
|      4 |    4 | Amount of shape properties in this file (cannot exceed 16bit) |

### Shape Properties Block (1-3 bytes)
| Offset | Size | Description                                                   |
| -----: | ---: | ------------------------------------------------------------- |
|      0 |    1 | Flags (see below)                                             |
|     *1 | 0\|1 | X offset, Y offset, or n/a (see Flags)                        |
|     *2 | 0\|1 | Y offset, or n/a (see Flags)                                  |

#### Flags
```
0001 1111
---Y XSGW - WALKABLE          (0x01)
 | | ||'--- GETTABLE          (0x02)
 | | |'---- SITTABLE          (0x04)
 | | '----- X offset present  (0x08)
 | '------- Y offset present  (0x10)
 '--------- (unused)
```

#### X/Y Offset
The reading/parsing behavior of the X/Y offset, and the bytes after the Flags 
can be described by the following pseudo-code:

```c
static const uint8_t F_XOFFSET = 0x08;
static const uint8_t F_YOFFSET = 0x10;

uint8_t flags = read(fd, 1);
int8_t x_offset = 0;
int8_t y_offset = 0;

if (flags & F_XOFFSET) {
	x_offset = read(fd, 1); // next byte is x offset
}

if (flags & F_YOFFSET) {
	y_offset = read(fd, 1); // next byte is y offset
}
```
